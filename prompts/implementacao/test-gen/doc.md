[← README](../../../README.MD)

# Test Generation

- **Nome:** Test Generation
- **Prompt:** [prompt.md](prompt.md)
- **Categoria:** Implementação

## Objetivo

Gerar testes Jest seguindo os padrões estabelecidos: mocks completos do Prisma para testes unitários, banco real para integração, nomenclatura padronizada de `describe`/`it` e verificação de constantes de erro (nunca mensagens de texto livre).

## Modelos Testados

| Modelo | Resultado |
|--------|-----------|
| claude-sonnet-4-6 | ✅ Funcional |

## Observações Gerais

- Forneça o código do serviço ou repository alvo para melhor resultado
- Para testes de integração de repositories, é necessário um banco PostgreSQL de teste configurado
- Combinar com `error-constants` para garantir que os erros testados estão alinhados com as constantes do projeto
- O padrão de mock do Prisma pode precisar de ajuste conforme a versão e configuração do adapter no projeto

## Últimas Atualizações

| Data | Alteração |
|------|-----------|
| 2026-06-10 | Criação inicial |
