# PR Description

- **Nome:** PR Description
- **Prompts:** [system.md](system.md) · [user-template.md](user-template.md) · [pr-template.md](pr-template.md)
- **Categoria:** Utils

## Objetivo

Gerar automaticamente a descrição de PRs a partir do diff entre a branch atual e a base. Usa o `DOMAIN.md` do projeto para injetar contexto do domínio apenas nos módulos tocados pelo diff, evitando enviar contexto desnecessário ao modelo.

## Modelos Testados

| Modelo | Resultado |
|--------|-----------|
| claude-haiku-4-5-20251001 | ✅ Funcional |

## Observações Gerais

- O script extrai automaticamente quais módulos de `src/_main/` aparecem no diff e injeta apenas as seções relevantes do `DOMAIN.md`
- O diff é reordenado antes do truncamento para priorizar arquivos de `src/_main/` e `src/`, evitando que código de feature seja cortado por mudanças em docs ou configs
- O `system.md` usa `cache_control: ephemeral` no script — indicado para prompts grandes e repetidos (reduz custo)

## Últimas Atualizações

| Data | Alteração |
|------|-----------|
| 2026-06-10 | Extração correta dos prompts do script gerador; separação em system/user-template/pr-template |
