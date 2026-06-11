# Error Constants

- **Nome:** Error Constants
- **Prompt:** [prompt.md](prompt.md)
- **Categoria:** Implementação

## Objetivo

Padronizar a criação de constantes de erro de negócio. Garante que novos erros sigam o padrão `UPPER_SNAKE_CASE`, sejam agrupados por domínio, incluam código identificador e status HTTP, e sejam corretamente integrados com o `errorHandler` global.

## Modelos Testados

| Modelo | Resultado |
|--------|-----------|
| claude-sonnet-4-6 | ✅ Funcional |

## Observações Gerais

- Verificar a implementação atual do `AppError` no projeto antes de aplicar o padrão de lançamento
- Combinar com `api-contract` para garantir que os erros documentados para o frontend estão alinhados com os implementados
- Combinar com `test-gen` para garantir que os testes verificam as constantes corretas, não strings arbitrárias

## Últimas Atualizações

| Data | Alteração |
|------|-----------|
| 2026-06-10 | Criação inicial |
