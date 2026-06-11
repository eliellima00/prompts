# Shadow Table Scaffold

- **Nome:** Shadow Table Scaffold
- **Prompt:** [prompt.md](prompt.md)
- **Categoria:** Implementação

## Objetivo

Gerar o scaffold completo para implementação de shadow tables (tabelas de histórico). Cobre: schema Prisma no schema `audit`, nomenclatura obrigatória com sufixo `_history`/`History`, implementação do repository com `$transaction` atômico e checklist de entrega.

## Modelos Testados

| Modelo | Resultado |
|--------|-----------|
| claude-sonnet-4-6 | ✅ Funcional |

## Observações Gerais

- Requer contexto sobre a estrutura de schemas (`main`/`audit`) do projeto para melhor resultado
- O campo `action` deve sempre usar os valores literais `'CREATE'`, `'UPDATE'` ou `'DELETE'`
- Fornecer o model Prisma da entidade principal ao invocar o prompt para melhor resultado
- Lembrar de executar `yarn prisma:gen` após qualquer alteração de schema antes de usar os novos tipos

## Últimas Atualizações

| Data | Alteração |
|------|-----------|
| 2026-06-10 | Criação inicial |
