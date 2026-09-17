---
tags:
  - area/modelos
tipo: procedimento
status: ativo
prioridade: nucleo
area: modelos
---

# Regra — material bruto e dados sensíveis

Vale para `06-clientes/*/material-bruto/` e exports colados no vault.

## Nunca manter no vault

- Senhas, tokens, API keys
- Códigos 2FA / OTP
- Links com token de convite ou URL de acesso temporário — substituir por `[removido]`

## Onde guardar credenciais reais

- Gestor de senhas
- Painel do provedor
- Nunca em `material-bruto`, diário ou `visao-geral`

## Fluxo

1. Redigir o bruto se ainda houver segredos
2. Não copiar segredos para notas derivadas
3. Registrar o trabalho no diário do dia
