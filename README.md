# Segundo cérebro operacional

Kit para montar um **segundo cérebro** — memória operacional em Markdown para trabalhar com agentes de IA. Não é um produto. Não é o vault de ninguém. Copie, corte, renomeie.

Guia: as seções numeradas estão neste README. Templates em `templates/vault/`. Skills e rules em `examples/`. Licença MIT.

## Em uma tela

O segundo cérebro **não** é um caderno de notas bonitas. É **memória operacional em Markdown**: onde paramos, o que foi decidido, o que vem a seguir.

Cada chat de agente começa amnésico. O vault é o que o próximo chat **lê antes de agir** e o que ele **escreve ao fechar** — extraído, nunca o transcript.

Três camadas:

1. **Porta** — MCP, CLI, APIs: o agente toca o mundo.
2. **Ambiente** — skills/rules + catálogo da *sua* máquina: como rodar um comando sem improvisar.
3. **Segundo cérebro** — vault: estado, diário, decisões, contas.

Três rituais: **retomar** (ler o checkpoint) · **registrar** (extrair o trabalho) · **fechar** (atualizar o checkpoint).

Três regras: **sem segredos** · **extrair, não despejar** · **editar o trecho, não reescrever a nota**.

O vault **não** é skills, rules nem catálogo. Esses artefatos (fora do vault) ensinam o agente *como* operar e **autoalimentar** o próximo chat — senão o segundo cérebro envelhece e o shell se improvisa.

## Como usar este kit

1. Leia as seções numeradas abaixo (a seção 0 já está no topo).
2. Copie `templates/vault/` para a pasta do seu vault Obsidian (ou só para uma pasta de Markdown).
3. Preencha `00-painel/estado-atual.md` e `00-painel/prioridades.md` com a mesa *real* de hoje — não com pastas vazias.
4. Copie `examples/skills/` para `~/.cursor/skills/` (ou o equivalente do seu agente) e ajuste `/caminho/do/vault`.
5. Copie `examples/rules/` para `~/.cursor/rules/` se o seu agente tiver rules always-on / glob.
6. Rode **um** ritual de verdade (retomar ou fechar). Sem o primeiro ciclo, o kit é pasta com nomes bonitos.

Não publique o *seu* vault, o catálogo da sua máquina, nem pasta de clientes com dados.

O domínio de origem do texto é manutenção WordPress com agentes (MCP, WP-CLI). O padrão serve a qualquer ops em que o contexto se perde quando o chat fecha.

## Licença

[MIT](LICENSE) — uso irrestrito, inclusive comercial. Mantenha o aviso da licença nas cópias substanciais.

Este repositório **é** o kit: este `README.md`, `templates/` e `examples/`. Clone, copie para o seu vault e para `~/.cursor/` (ou o equivalente do seu agente). Não é o segundo cérebro de ninguém — é o ponto de partida.

---

## 1. O que é (40 segundos)

Não é “notas bonitas”. É memória operacional em arquivos Markdown (tipicamente num vault Obsidian):

- **estado atual** — checkpoint: onde paramos, próximas ações;
- **diário** — log do dia, extraído;
- **prioridades** — agora / depois / incubado;
- **decisões** — uma por nota, recuperáveis;
- **contas ou projetos** — visão + *uma* lista canônica do que falta.

O agente **lê** isso no início da sessão e **escreve** no fechamento. MCP (ou CLI) abre a porta; o segundo cérebro diz o que já sabemos. Pasta de cliente no ar? Não. Mostra-se a **estrutura**, não o conteúdo.

Fala pronta:

> Cada chat esquece. O segundo cérebro é o Markdown que o próximo agente lê antes de agir e atualiza ao parar: estado, diário, decisões. Extrai conhecimento. Não despeja conversa.

---

## 2. Por que existe

Agentes são excelentes em executar e péssimos em lembrar o chat anterior. Sem um lugar canônico:

- o mesmo diagnóstico se refaz;
- a pendência vive no briefing, no diário *e* no WhatsApp — e some na retomada;
- a decisão “não fazer X” morre no transcript;
- o próximo modelo inventa um roadmap porque não leu *onde paramos*.

O objetivo **não** é disciplina perfeita. É **continuidade**: voltar depois de três dias e, em cinco minutos, saber o que está na mesa.

```text
Informação (chat, export, código)
        → extração
Consolidação em nota viva
        → knowledge base + memória operacional
Consulta no chat seguinte (@ anexar o pacote mínimo)
```

**Continuidade > disciplina.** Um checkpoint honesto vence um vault “completo” que ninguém atualiza.

---

## 3. Três camadas do stack

```text
                    você pergunta
                         │
                         ▼
                      [agente]
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
     1. PORTA       2. AMBIENTE     3. SEGUNDO CÉREBRO
     MCP / CLI      skills, rules   vault Markdown
     WP-CLI, APIs   catálogo        estado · diário
     (exemplo WP)   snapshot        decisões · contas
```

| Camada | Papel | O que **não** é |
|--------|--------|-----------------|
| Porta | Deixa o agente *ver* e, com freio, *agir* no sistema real | A memória do projeto |
| Ambiente | Receitas validadas *desta* máquina | O backlog da conta |
| Segundo cérebro | O *quê* existe e *onde paramos* | Dump de chats |

A implementação do agente (skill, rules) fica **fora** do vault, em `~/.cursor/skills/…`.

### Skill vs rule vs autoalimentação

| Artefato | Onde | Papel |
|----------|------|--------|
| Vault | `/caminho/do/vault` | O *quê* e *onde paramos* |
| Skill | `~/.cursor/skills/<nome>/SKILL.md` | Playbook sob demanda |
| Rule always-on | `~/.cursor/rules/*.mdc` | Cartão curto em todo chat |
| Rule com glob | mesma pasta, `globs:` | Convenções ao tocar o vault |
| Snapshot + catálogo | junto da skill de ambiente | Verdade *desta* máquina |
| Cookbook de domínio | junto da skill de domínio | Receitas do ofício (ex.: WP-CLI) |

Três skills-núcleo (copie a *função*, não o nome): `segundo-cerebro` · `ambiente-local` · skill de domínio.

**Autoalimentação:** armadilha ou tipo novo de operação → receita no catálogo/cookbook **neste turno**, antes da resposta final. Sem senha.

**Não conta:** ter acertado neste chat; ter escrito só no vault; improvisar “só desta vez”.

**Teste:** o próximo chat copia o catálogo, não o transcript.

Always-on curto; catálogo e vault longos sob demanda. Gates humanos: commit, produção, dinheiro.

---

## 4. Mapa de pastas sugerido

Crie pasta quando o primeiro arquivo real existir. Números ordenam o Explorer.

```text
/caminho/do/vault/
  00-painel/            cockpit
    estado-atual.md
    prioridades.md
    retomar-sessao.md
    diario/YYYY-MM-DD.md
  01-marca/             identidade (se fizer sentido)
  02-servicos/
  03-produtos/
  04-dominio/           conhecimento estável da sua área
  05-laboratorio/
  06-clientes/cliente-a/
    visao-geral.md
    pendencias.md       ← lista canônica
    infraestrutura.md
    material-bruto/     ← já redigido
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

Neste kit, o mínimo já está em `templates/vault/`.

Item simples → **nota única**. Item rico → pasta com `visao.md` + satélites só com conteúdo. Nunca pasta vazia.

---

## 5. Tipos principais de notas

| `tipo` | Arquivo | Serve para | Não é |
|--------|---------|------------|--------|
| `painel` | `estado-atual.md` | Checkpoint da mesa | Backlog de uma conta |
| `diario` | `diario/YYYY-MM-DD.md` | Extração do dia | Knowledge base |
| `procedimento` | `retomar-sessao.md` | Ritual | O que aconteceu hoje |
| `cliente` | `visao-geral.md` | Hub da conta | Lista de pendências |
| — | `pendencias.md` | **Único** backlog da conta | Briefing |
| `produto` / `lab` | `visao.md` | Hub em evolução | Pasta vazia |
| — | `15-decisoes/slug.md` | Decisão recuperável | Insight só no diário |

**Estado-atual:** atualizar ao parar. Seções: foco · onde paramos · próximas ações (3–5). Edição cirúrgica.

**Pendências:** checkboxes abertos no topo. Item só no briefing **não existe** na retomada.

**Decisão:** uma por nota + linha no índice. Data, contexto (uma frase), decisão, consequências.

Frontmatter opcional no dia 1: `tipo`, `status`, `prioridade`, `area`, `tags`. Wikilink com caminho da raiz. Não use `[[caminho|alias]]` dentro de tabela.

Os arquivos em `templates/vault/` e `13-modelos/` são os modelos prontos para copiar.

---

## 6. Rituais

**Retomar (~5 min):** estado-atual → últimos 2–3 diários → prioridades → um projeto, até 3 tarefas, o que não abrir. Não abrir a biblioteca primeiro.

**Registrar:** diário + estado-atual cirúrgico + `pendencias.md` se a conta mudou + uma decisão se nasceu uma.

**Fechar:** checklist em `templates/vault/13-modelos/modelo-fechamento-sessao.md`.

Chat de organização não vira chat de código.

---

## 7. Regras invioláveis

1. Sem segredos no Markdown (`[removido]`).
2. Extrair, não despejar o chat.
3. Edição cirúrgica em notas curadas.
4. Uma lista canônica por conta (`pendencias.md`).
5. O agente não inventa convenções — lê os modelos.
6. Referências congeladas são somente leitura.
7. Não meter o vault inteiro em rule always-on.

---

## 8. Como um agente usa

Ler no início: estado-atual, 2–3 diários, prioridades, uma visão se o foco estiver claro. Pacote de conta: 5–7 arquivos, sempre com `pendencias.md`.

Durante: tipo novo → catálogo neste turno.

Fim: diário, estado-atual, pendências, decisão. Resumo de 2–3 linhas. Override: “só me mostre o bloco para colar”.

Stubs prontos: `examples/skills/` e `examples/rules/`.

---

## 9. Como começar do zero em uma tarde

1. Copie `templates/vault/` para `/caminho/do/vault/`.
2. Preencha estado-atual e prioridades com a mesa **real**.
3. Copie `examples/skills/segundo-cerebro/SKILL.md` para `~/.cursor/skills/segundo-cerebro/` e ajuste o caminho do vault.
4. Copie `examples/skills/ambiente-local/` e preencha *o seu* `catalogo.md` (não publique esse arquivo).
5. Copie as rules em `examples/rules/` se o agente tiver always-on / glob.
6. Rode um ritual hoje (retomar ou fechar).

---

## 10. O que adaptar

Pastas `01`–`12`, se usa “clientes” ou “times”, idioma único, porta (MCP ou não), catálogo da máquina, skill de domínio, always-on vs sob demanda.

Não adapte: sem segredos, extrair, cirúrgico, autoalimentação no mesmo turno.

---

## 11. Anti-padrões

Dump de chat no vault · segundo backlog escondido · secrets no Markdown · always-on com o vault inteiro · improvisar o shell e deixar a receita no transcript · autoalimentação só no vault · reorganizar no meio da execução · pastas vazias com estado-atual velho · agente inventando convenção.

---

## 12. FAQ

**Tokens?** Pacote mínimo; ops em chat exclusivo; catálogo para não retryar. Vault fora do always-on.

**Obsidian vs Notion?** Arquivo em disco. Agentes leem `.md`.

**Precisa de Cursor?** Não. Qualquer agente que leia pastas + um humano no fechamento.

**Só local, sem MCP?** Sim. A porta pode ser o terminal ou você colando output.

**Gist?** Este kit é um repositório de propósito. Não publique o vault real.

**Publicar minhas skills de verdade?** Não. Stubs e o padrão. Catálogo da máquina fica privado (`catalogo.md` está no `.gitignore`).

---

## Apêndices

**A — Decisão:** data, contexto (uma frase), decisão, consequências; linha no índice. Modelo: `templates/vault/13-modelos/modelo-decisao.md`.

**B — Material bruto:** redigir OTP/token/URL de bypass antes de derivar notas. `templates/vault/13-modelos/regra-material-bruto.md`.

**C — Licença:** MIT (`LICENSE`). Use, copie, modifique, distribua, inclusive comercialmente. Mantenha o aviso da licença nas cópias substanciais. Não publique pasta de contas com dados reais.
