# Contrato para agentes

Este arquivo é o contrato curto para qualquer agente de IA que opere um **segundo cérebro operacional**: memória em Markdown (estado atual, diário, decisões, lista canônica). A especificação completa está no [README.md](README.md).

Não invente convenções. Não cole o vault inteiro neste contrato nem em rule always-on.

## Fonte da verdade

O vault em `/caminho/do/vault` (a pessoa substitui o path). Pacote mínimo a **ler** no início:

1. `00-painel/estado-atual.md`
2. Últimos 2–3 arquivos em `00-painel/diario/`
3. `00-painel/prioridades.md`
4. Uma visão de projeto só se o foco já estiver claro

Conta ou cliente: no máximo 5–7 arquivos; incluir sempre `pendencias.md`.

## O que gravar ao fechar

Trabalho relevante (código, decisão, marco, conta) → diário do dia + edição **cirúrgica** do estado-atual. Decisão importante → nota em `15-decisoes/` + linha no índice. Conta → checkbox em `pendencias.md` (não deixar ação nova só no diário).

Default: gravar e resumir em 2–3 linhas. Override da pessoa: «só me mostre o bloco para colar».

## O que não fazer

- Segredos no Markdown (usar `[removido]`)
- Despejar o chat no vault
- Reescrever nota curada inteira
- Meter o vault ou o catálogo da máquina em always-on
- Criar pastas `01`–`12` vazias
- Improvisar o shell e deixar a receita só no transcript (autoalimentação: catálogo **neste turno**)

## Instalação

Prompt colável: [prompts/bootstrap.md](prompts/bootstrap.md).

Por ferramenta: [Cursor](prompts/cursor.md) · [Claude](prompts/claude.md) · [ChatGPT](prompts/chatgpt.md).
