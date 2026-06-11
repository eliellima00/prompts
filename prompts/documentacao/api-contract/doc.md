[← README](../../../README.MD)

# API Contract

- **Nome:** API Contract
- **Prompt:** [prompt.md](prompt.md)
- **Categoria:** Documentação

## Objetivo

Gerar resumos técnicos padronizados de contratos de API destinados ao time de frontend. Cobre: rota, método HTTP, inputs (body/query/params), outputs (200 OK), códigos de erro e changelog de exceções quando houver alterações em serviços.

## Modelos Testados

| Modelo | Resultado |
|--------|-----------|
| claude-sonnet-4-6 | ✅ Funcional |

## Observações Gerais

- Para melhor resultado, forneça o contexto de domínio e os códigos de erro do projeto ao invocar
- Não substitui a documentação Swagger/OpenAPI do projeto — é um resumo textual para comunicação rápida com o frontend
- Para documentar alterações em serviços (novas exceptions ou remoções), forneça o diff ou descreva o que mudou
- Combinar com `error-constants` para garantir alinhamento entre constantes implementadas e as documentadas

## Últimas Atualizações

| Data | Alteração |
|------|-----------|
| 2026-06-10 | Criação inicial |
