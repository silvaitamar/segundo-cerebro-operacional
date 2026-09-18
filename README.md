# Segundo cérebro operacional

**Segundo cérebro operacional** é memória em Markdown — em geral um vault [Obsidian](https://obsidian.md) — que um agente de IA lê no início da sessão e atualiza ao fechar: estado atual, diário, decisões e uma lista canônica do que falta.

Este repositório é o kit público do padrão: texto de referência, [templates do vault](templates/vault/) e [stubs de skills e rules](examples/). Não é um produto, não é um curso e **não é o vault de ninguém**. O texto e os stubs acompanham a evolução do sistema (vault, skills, rules, catálogo de ambiente) e mudam quando o padrão muda.

Origem: operação WordPress com agentes (MCP, WP-CLI). O mesmo contrato serve a qualquer ops em que o contexto some quando o chat fecha.

<table>
<tbody>
<tr><td>Licença</td><td><a href="LICENSE">MIT</a></td></tr>
<tr><td>Atualização</td><td>2026-09-18</td></tr>
<tr><td>Autor</td><td><a href="https://github.com/silvaitamar">Itamar Silva</a></td></tr>
<tr><td>Apoio</td><td><a href="https://github.com/sponsors/silvaitamar">GitHub Sponsors</a> · <a href="https://buymeacoffee.com/silva.itamar">Buy Me a Coffee</a></td></tr>
<tr><td>Conteúdo</td><td><code>README.md</code> · <code>templates/</code> · <code>examples/</code></td></tr>
</tbody>
</table>

Cada sessão de agente começa amnésica. O segundo cérebro é o Markdown que o próximo agente lê antes de agir e grava ao parar. Extrai conhecimento. Não despeja conversa.

## Sumário

- [Definição](#definição)
- [Continuidade entre sessões](#continuidade-entre-sessões)
- [Arquitetura: porta, ambiente e vault](#arquitetura-porta-ambiente-e-vault)
- [Skills, rules e autoalimentação](#skills-rules-e-autoalimentação)
- [Estrutura do vault](#estrutura-do-vault)
- [Tipos de nota](#tipos-de-nota)
- [Rituais de sessão](#rituais-de-sessão)
- [Restrições](#restrições)
- [Contrato com o agente](#contrato-com-o-agente)
- [Adoção](#adoção)
- [O que é estável e o que evolui](#o-que-é-estável-e-o-que-evolui)
- [Anti-padrões](#anti-padrões)
- [Perguntas frequentes](#perguntas-frequentes)
- [Conteúdo do repositório](#conteúdo-do-repositório)
- [Apoio](#apoio)
- [Licença](#licença)

## Definição

O segundo cérebro operacional **não** é um caderno de notas bonitas. É o checkpoint da mesa de trabalho.

Peças mínimas:

| Peça | Função |
|------|--------|
| Estado atual | Onde paramos e o que vem a seguir |
| Diário | Extração do dia, não knowledge base |
| Prioridades | Agora / depois / incubado |
| Decisões | Uma por nota, recuperáveis |
| Contas ou projetos | Visão + **uma** lista canônica do que falta |

O agente lê isso no início e escreve no fechamento. MCP ou CLI abrem a porta para o mundo real; o segundo cérebro diz o que já se sabe. O que se publica neste kit é a **estrutura**, não o conteúdo de contas.

O vault **não** substitui skills, rules nem o catálogo da máquina. Esses artefatos ficam fora do vault: ensinam *como* operar e **autoalimentam** o chat seguinte. Sem eles o segundo cérebro envelhece e o shell se improvisa.

## Continuidade entre sessões

Agentes executam bem e lembram mal o chat anterior. Sem um lugar canônico:

- o mesmo diagnóstico se refaz;
- a pendência vive no briefing, no diário e no WhatsApp — e some na retomada;
- a decisão de *não* fazer algo morre no transcript;
- o modelo seguinte inventa um roadmap porque não leu *onde paramos*.

O objetivo não é disciplina perfeita. É **continuidade**: voltar depois de dias parado e, em poucos minutos, saber o que está na mesa. Um checkpoint honesto vence um vault “completo” que ninguém atualiza.

```text
Informação (chat, export, código)
        → extração
Nota viva
        → knowledge base + memória operacional
Consulta na sessão seguinte (pacote mínimo, não o vault inteiro)
```

## Arquitetura: porta, ambiente e vault

Três camadas distintas. Confundi-las é a origem da maior parte da confusão.

```text
                      [agente]
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
       PORTA         AMBIENTE      SEGUNDO CÉREBRO
     MCP / CLI     skills, rules    vault Markdown
     APIs, WP-CLI  catálogo         estado · diário
                   snapshot         decisões · contas
```

| Camada | Papel | Não é |
|--------|--------|--------|
| Porta | Ver e, com freio, agir no sistema real | A memória do projeto |
| Ambiente | Receitas validadas *desta* máquina | O backlog da conta |
| Segundo cérebro | O *quê* existe e *onde paramos* | Dump de chats nem um segundo gerenciador de tarefas |

A porta sem cérebro alucina contexto. O cérebro sem porta descreve o mundo sem tocá-lo. O ambiente sem os dois faz o agente improvisar `PATH` a cada sessão.

Skills e rules ficam **fora** do vault (`~/.cursor/skills/`, `~/.cursor/rules/`, ou o equivalente da ferramenta).

Dentro do vault há três funções (não são pastas obrigatórias no primeiro dia):

1. **Knowledge base** — o que é estável.
2. **Memória operacional** — estado-atual e diário.
3. **Direção** — prioridades, roteiros, contas.

A retomada começa na memória operacional, não na biblioteca.

## Skills, rules e autoalimentação

| Artefato | Onde | Papel |
|----------|------|--------|
| Vault | `/caminho/do/vault` | O *quê* e *onde paramos* |
| Skill | `~/.cursor/skills/<nome>/SKILL.md` | Playbook sob demanda |
| Rule always-on | `~/.cursor/rules/*.mdc` | Cartão curto em todo chat |
| Rule com glob | a mesma pasta, `globs:` | Convenções ao tocar o vault |
| Snapshot + catálogo | junto da skill de ambiente | Verdade *desta* máquina |
| Cookbook de domínio | junto da skill de domínio | Receitas do ofício (ex.: WP-CLI) |

Skill é longa e tem fluxos. Rule always-on é um cartão: aponta para a skill; não cola o catálogo no contexto de todos os chats. Meter o vault ou o cookbook no always-on come token e é o contrário de context engineering.

Três funções-núcleo (os nomes são exemplos; copia-se a função):

1. **Segundo cérebro** — ler e escrever o vault (rituais, granularidade, sem segredos).
2. **Ambiente local** — como *esta* máquina executa comando (shell, PATH, armadilha).
3. **Domínio** — no exemplo WordPress: detectar ambiente, não editar core, mutação só com flag explícita. Em outro ofício: o equivalente.

Rules always-on que cabem num cartão: captura ao fechar; ponte “antes do terminal, a skill de ambiente”; privacidade em repo público; commit só com pedido; um guardrail estreito de produção. O detalhe longo permanece sob demanda.

### Autoalimentação

Cada chat começa amnésico. Se a descoberta ficar só no transcript, o próximo agente repete o erro. Autoalimentação é gravar a receita no artefato durável **neste turno**, antes da resposta final.

```text
armadilha ou tipo novo de operação
        ↓  mesmo turno
catálogo da máquina  ou  cookbook de domínio
        ↓
o próximo chat copia o artefato, não o transcript
```

Gatilho: primeira vez daquele tipo de comando; armadilha nova; snapshot divergente da realidade; o ambiente mudou.

Não conta: ter acertado neste chat; ter escrito só no vault da conta; improvisar “só desta vez”.

Teste: se o próximo agente precisa copiar o comando do transcript, a regra falhou neste turno.

O segundo cérebro registra *que* a sessão aconteceu e *onde paramos*. A autoalimentação registra *como* repetir a operação. Um não substitui o outro.

Gates humanos (não são o vault): commit, push, tag; mutação em produção; promover receita interna a este repositório público. Tokens e nomes de conta nunca no git público.

## Estrutura do vault

Números no começo ordenam o Explorer. Cria-se pasta quando o primeiro arquivo real existir. Pastas vazias não ajudam.

```text
/caminho/do/vault/
  00-painel/              cockpit
    estado-atual.md
    prioridades.md
    retomar-sessao.md
    diario/YYYY-MM-DD.md
  01-marca/               identidade (se fizer sentido)
  02-servicos/
  03-produtos/
  04-dominio/             conhecimento estável da área
  05-laboratorio/
  06-clientes/cliente-a/
    visao-geral.md
    pendencias.md         ← lista canônica
    infraestrutura.md
    material-bruto/       ← já redigido
  07-infraestrutura/
  08-roteiros/
  09-conteudo/
  10-ativos/
  11-snippets/
  12-ideias/
  13-modelos/
  15-decisoes/indice.md
  99-arquivo/
```

O mínimo deste kit está em [`templates/vault/`](templates/vault/).

Item simples e estável → **nota única**. Item com várias dimensões vivas → **pasta** com `visao.md` e satélites só os que tiverem conteúdo. Nunca pasta vazia; promove-se quando a nota passa de uma tela ou mistura assuntos.

Pastas `01`–`12` e o rótulo “clientes” vs “times” são adaptáveis. `14-negocios/` só existe com dado financeiro real.

## Tipos de nota

O `tipo` no frontmatter é o contrato com o agente: o que a nota *é* e o que ela não substitui.

| `tipo` | Arquivo | Serve para | Não é |
|--------|---------|------------|--------|
| `painel` | `estado-atual.md` | Checkpoint da mesa | Backlog de uma conta |
| `diario` | `diario/YYYY-MM-DD.md` | Extração do dia | Knowledge base |
| `procedimento` | `retomar-sessao.md` | Ritual repetível | O que aconteceu hoje |
| `cliente` | `visao-geral.md` | Hub da conta | Lista de pendências |
| — | `pendencias.md` | **Único** backlog da conta | Briefing |
| `produto` / `lab` | `visao.md` | Item em evolução | Pasta vazia |
| — | `15-decisoes/slug.md` | Decisão recuperável | Insight só no diário |

**Estado atual.** Atualizar ao parar. Seções: foco, onde paramos, próximas ações (3–5). Edição cirúrgica: muda-se a subseção tocada e a data, não a nota inteira.

**Pendências.** Checkboxes abertos no topo. Item que só existe no briefing **não existe** na retomada.

**Decisão.** Uma por nota e uma linha no índice. Data, contexto (uma frase), decisão, consequências.

Frontmatter opcional no primeiro dia: `tipo`, `status`, `prioridade`, `area`, `tags`. Wikilink com caminho desde a raiz. Não usar `[[caminho|alias]]` dentro de célula de tabela. Datas: `YYYY-MM-DD`.

Modelos em [`templates/vault/13-modelos/`](templates/vault/13-modelos/).

## Rituais de sessão

**Retomar.** Estado atual → últimos dois ou três diários → prioridades → um projeto, até três tarefas, o que não abrir. A biblioteca não é o ponto de partida.

**Registrar.** Gatilho: trabalho relevante (código, decisão, marco, conta). Diário do dia + estado atual cirúrgico + `pendencias.md` se a conta mudou + uma nota de decisão se nasceu uma. Q&A trivial não entra.

**Fechar.** Checklist em [`templates/vault/13-modelos/modelo-fechamento-sessao.md`](templates/vault/13-modelos/modelo-fechamento-sessao.md).

Chat de organização não vira chat de execução de código.

## Restrições

1. Sem segredos no Markdown (`[removido]`).
2. Extrair; não despejar o chat.
3. Edição cirúrgica em notas curadas.
4. Uma lista canônica por conta (`pendencias.md`).
5. O agente não inventa convenções: lê os modelos.
6. Referências congeladas são somente leitura.
7. O vault inteiro não entra em rule always-on.

## Contrato com o agente

No início: estado atual, dois ou três diários, prioridades, uma visão se o foco já estiver claro. Pacote de conta: cinco a sete arquivos, sempre com `pendencias.md`.

Durante: tipo novo de operação → catálogo neste turno.

No fim: diário, estado atual, pendências, decisão. Resumo de duas ou três linhas. Override: gravar só o bloco para colar.

Stubs: [`examples/skills/`](examples/skills/) e [`examples/rules/`](examples/rules/).

## Adoção

1. Copiar [`templates/vault/`](templates/vault/) para `/caminho/do/vault/` (Obsidian ou qualquer pasta Markdown).
2. Preencher `estado-atual.md` e `prioridades.md` com a mesa **real** — não com pastas vazias.
3. Copiar [`examples/skills/`](examples/skills/) para `~/.cursor/skills/` (ou o equivalente) e ajustar o caminho do vault.
4. Preencher o *próprio* `catalogo.md` da máquina. Esse arquivo **não** se publica (está no `.gitignore` deste kit).
5. Copiar [`examples/rules/`](examples/rules/) se a ferramenta tiver always-on / glob.
6. Rodar um ritual de verdade (retomar ou fechar). Sem o primeiro ciclo, o kit é pasta com nomes.

Não se publica o vault real, o catálogo da máquina, nem pasta de contas com dados.

## O que é estável e o que evolui

Este repositório **não** é o recorte de uma palestra. É o extrato público de um sistema em uso. Quando o vault, as skills ou as rules mudam de forma que altere o padrão, este texto e os stubs acompanham.

| Estável (não “adaptar embora”) | Evolui com o ofício |
|-------------------------------|---------------------|
| Sem segredos | Árvore `01`–`12` |
| Extrair, não despejar | “Clientes” vs “times” vs “projetos” |
| Edição cirúrgica | Idioma das notas |
| Lista canônica por conta | Porta (MCP, CLI, ou nenhum) |
| Autoalimentação no mesmo turno | Catálogo *desta* máquina |
| Três camadas (porta / ambiente / vault) | Skill de domínio, always-on vs sob demanda |

O que **não** sobe aqui: receitas com path de máquina, hosts, nomes de conta, checklists internas. Sobe o padrão; o cookbook privado fica privado.

## Anti-padrões

Dump de chat no vault · segundo backlog escondido no briefing · secrets no Markdown · always-on com o vault inteiro · improvisar o shell e deixar a receita no transcript · autoalimentação só no vault · reorganizar o vault no meio da execução · pastas vazias com estado atual velho · agente inventando convenção · tratar este README como script de aula em vez de especificação viva.

## Perguntas frequentes

### O segundo cérebro operacional precisa do Obsidian?

Não. Precisa de arquivos em disco. Agentes leem Markdown. Obsidian é um viewer conveniente, não o requisito.

### Funciona sem Cursor?

Sim. Qualquer agente que leia pastas, mais um humano no fechamento. Cursor é um jeito cômodo de carregar skills e rules.

### Dá para usar só local, sem MCP?

Sim. A porta pode ser o terminal ou o output colado na sessão.

### Qual a diferença para um “second brain” clássico (PARA, Zettelkasten)?

O foco aqui não é biblioteca pessoal nem criatividade. É **memória operacional para agentes**: checkpoint, lista canônica, decisão recuperável, autoalimentação do ambiente. Knowledge base existe, mas a retomada não começa nela.

### Gist resolve?

Não carrega templates nem stubs. Este repositório existe por isso. O vault real continua privado.

### Publico as skills da minha máquina?

Não. Publicam-se stubs e o padrão. `catalogo.md` e `snapshot.md` ficam fora do git público.

### Isso aumenta o uso de tokens?

O pacote mínimo reduz retrabalho. Ops em chat exclusivo. Catálogo para não retryar o mesmo wrap. Vault **fora** do always-on.

## Conteúdo do repositório

```text
segundo-cerebro-operacional/
  README.md
  LICENSE
  .github/FUNDING.yml
  templates/vault/          cockpit, modelos, cliente-a genérico
  examples/skills/          segundo-cerebro · ambiente-local (exemplos)
  examples/rules/           captura, ponte, privacidade, glob, commits
```

Placeholders públicos: `cliente-a`, `projeto-exemplo`, `/caminho/do/vault`. Nada de conta real.

## Apoio

Quem quiser pagar um café: [GitHub Sponsors](https://github.com/sponsors/silvaitamar) ou [Buy Me a Coffee](https://buymeacoffee.com/silva.itamar). O botão **Sponsor** do repositório aponta para os dois.

## Licença

[MIT](LICENSE) — uso, cópia, modificação e distribuição, inclusive comercial. Manter o aviso da licença nas cópias substanciais.
