# Prompt de bootstrap

Cole o bloco abaixo num agente que consiga ler e escrever arquivos (Cursor, Claude Code, Copilot Workspace, etc.). Substitua `/caminho/do/vault` e descreva a mesa real em 3–5 frases.

Quem só tem chat (Custom GPT sem disco): peça os arquivos em Markdown e grave você na pasta.

```text
Quero um segundo cérebro operacional a partir deste kit:
https://github.com/silvaitamar/segundo-cerebro-operacional

Leia README.md e AGENTS.md. Não invente convenções.

1. Copie templates/vault-minimo/ para /caminho/do/vault/
   (não copie a árvore 01–12; não crie pastas vazias).
2. Ajuste wikilinks e o path do vault se a skill/rule for instalada.
3. Preencha 00-painel/estado-atual.md e 00-painel/prioridades.md
   com a mesa REAL que eu descrevo abaixo — não deixe projeto-exemplo
   se eu já disse o que está na mesa. Sem segredos; use [removido].
4. Crie 00-painel/diario/YYYY-MM-DD.md (hoje) a partir do _modelo.
5. Rode um fechamento mínimo: diário + estado-atual atualizados.
6. Não publique catalogo.md, snapshot.md, nem pasta de contas reais.

Minha mesa agora:
- (projeto principal, uma frase)
- (o que ficou aberto)
- (o que NÃO abrir hoje)

Quando terminar: mostre os paths criados e o próximo passo em uma frase.
```
