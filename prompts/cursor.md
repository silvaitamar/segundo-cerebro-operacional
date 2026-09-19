# Cursor

Contrato: [AGENTS.md](../AGENTS.md). Especificação: [README.md](../README.md). Bootstrap: [bootstrap.md](bootstrap.md).

## Skills

Copie `examples/skills/segundo-cerebro/` para `~/.cursor/skills/segundo-cerebro/`.
Copie `examples/skills/ambiente-local/` para `~/.cursor/skills/ambiente-local/`.

No `SKILL.md` do segundo cérebro, troque `/caminho/do/vault` pelo path real.

Copie `catalogo.example.md` → `catalogo.md` e `snapshot.example.md` → `snapshot.md` **fora** de git público (já estão no `.gitignore` do kit). Preencha com *esta* máquina.

## Rules

Copie `examples/rules/*.mdc` para `~/.cursor/rules/`. São cartões. Não cole o vault no always-on.

Opcional: rule com glob só nos arquivos do vault (`vault-glob.mdc`).

## Pacote por chat

Anexe estado-atual + 2–3 diários + prioridades. Não indexe o vault inteiro no projeto do agente se isso puxar uploads ou `wp-content`.
