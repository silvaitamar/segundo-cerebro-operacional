---
name: ambiente-local
description: >-
  Shell e caminhos desta máquina. Use em todo comando de terminal
  ou quando falhar PATH, HOME, ou ferramenta not found.
---

# Ambiente local

Memória operacional **desta** máquina. Não improvisar shell.

Ler na ordem: esta skill → [snapshot.md](snapshot.md) → [catalogo.md](catalogo.md) se a operação não estiver óbvia.

Preencha os dois artefatos com a *sua* realidade (OS, PATH, wrap). Não copie o catálogo de outra pessoa.

## Snapshot

O que existe agora: ferramentas, usuários, mounts. Gerado ou escrito à mão uma vez; regenerar quando o ambiente mudar.

## Catálogo

Receitas validadas. Formato: contexto → comando canônico → armadilha já vista.

## Autoalimentação (mesmo turno)

Gatilho: tipo novo de operação, armadilha nova, ferramenta que o snapshot marca ausente/presente e a realidade divergiu, ou o humano disse que o ambiente mudou.

Antes da resposta final:

1. Linha em `catalogo.md` (receita + armadilha). Sem senha, sem OTP.
2. Se identidade/tooling mudou → atualizar `snapshot.md`.

**Não conta:** só ter acertado neste chat; só ter escrito no vault; ter “lembrado” a receita e improvisado só desta vez.

**Teste:** o próximo chat copia o catálogo, não o transcript.

## O que esta skill não substitui

- Vault: skill `segundo-cerebro`
- Playbook de domínio (CMS, cloud, etc.): skill própria + cookbook
- Segredos: nunca no snapshot/catálogo
