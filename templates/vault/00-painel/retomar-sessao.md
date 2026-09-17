# Retomar Sessão

> Playbook para voltar após um sumiço, ou para começar o dia com contexto.
> Checkpoint: [[00-painel/estado-atual|Estado Atual]]

---

## Ritual ao voltar (~5 min)

1. Abrir [[00-painel/estado-atual|Estado Atual]] — *Onde paramos* e *Próximas ações*
2. Abrir os últimos 2–3 diários em `00-painel/diario/`
3. Olhar [[00-painel/prioridades|Prioridades]]
4. **Não** abrir o mapa/biblioteca primeiro
5. Pedir à IA o recorte operacional (prompt abaixo)

---

## Ritual ao parar (~2–5 min)

1. Preencher o diário do dia
2. Atualizar o estado-atual (data, *Onde paramos*, *Próximas ações*)
3. Se for conta: atualizar `pendencias.md`
4. **Não** colar o chat inteiro — só decisões, links e uma frase de contexto

Checklist: [[13-modelos/modelo-fechamento-sessao|Fechamento de Sessão]]

---

## Pacote mínimo para a IA

1. `00-painel/estado-atual.md`
2. Últimos 2–3 arquivos em `00-painel/diario/`
3. `00-painel/prioridades.md`
4. Uma visão de projeto, se o foco já estiver claro

Conta: 5–7 arquivos no máximo; sempre incluir `pendencias.md`.

---

## Prompt — o que trabalhar hoje?

```text
Fiquei [N] dias sem trabalhar.

Com base em estado-atual, últimos diários e prioridades:
1. UM projeto principal para hoje.
2. Até TRÊS tarefas realistas.
3. O que NÃO abrir hoje.
4. Se a energia estiver baixa: versão mínima do dia.

Não invente roadmap. Priorize continuidade a partir de "Onde paramos".
```

---

## Prompt — fechar sessão

```text
Vou encerrar a sessão. Com base no que trabalhamos hoje, gere:

1. Texto curto para a seção "O que foi feito" do diário de hoje.
2. Atualização das seções "Onde paramos" e "Próximas ações" para estado-atual.md
   (máx. 5 bullets cada).
3. Uma frase para "Estado operacional" se mudou algo.

Formato: markdown pronto para colar. Sem repetir o chat inteiro.
```
