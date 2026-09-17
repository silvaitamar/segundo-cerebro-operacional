---
tags:
  - area/modelos
tipo: procedimento
status: ativo
area: modelos
---

# Propriedades padrão

Convenção YAML para notas que importam. Opcional no dia 1.

```yaml
---
tags:
  - area/painel
tipo: painel
status: ativo
prioridade: nucleo
area: painel
aliases:
  - Nome curto
---
```

| Campo | Valores |
|--------|---------|
| `tipo` | `projeto` · `produto` · `cliente` · `lab` · `procedimento` · `ideia` · `painel` · `diario` |
| `status` | `ativo` · `construcao` · `pausado` · `arquivo` |
| `prioridade` | `nucleo` · `alto` · `medio` · `baixo` |
| `area` | espelha a pasta |

Checkpoint (`estado-atual`) usa também `ultima_atualizacao: YYYY-MM-DD`.

Wikilinks com caminho da raiz: `[[00-painel/estado-atual|Estado Atual]]`. Não usar `[[caminho|alias]]` dentro de célula de tabela.
