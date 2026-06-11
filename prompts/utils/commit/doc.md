# Conventional Commit

- **Nome:** Conventional Commit
- **Prompt:** [prompt.md](prompt.md)
- **Categoria:** Utils

## Objetivo

Gerar mensagens de commit seguindo o padrão Conventional Commits. Garante consistência no histórico do git e facilita geração de changelogs automáticos.

## Modelos Testados

| Modelo            | Resultado    |
| ----------------- | ------------ |
| claude-sonnet-4-6 | ✅ Funcional |

## Observações Gerais

- Forneça o diff ou uma descrição das alterações para melhor resultado
- Mensagens são geradas em inglês por padrão (convenção da indústria para histórico git)
- Para breaking changes, o modelo inclui `!` no tipo e a seção `BREAKING CHANGE:` no rodapé

## Últimas Atualizações

| Data       | Alteração       |
| ---------- | --------------- |
| 2026-06-10 | Criação inicial |
