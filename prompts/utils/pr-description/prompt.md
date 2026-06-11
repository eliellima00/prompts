# PR Description — Arquivos

Este prompt é composto por três arquivos. Cada um mapeia diretamente para um campo ou variável do script gerador.

| Arquivo | Destino no script | Conteúdo |
|---------|-------------------|----------|
| [system.md](system.md) | parâmetro `system` da API | System prompt estático |
| [user-template.md](user-template.md) | variável `prompt` | Template da mensagem do usuário com placeholders |
| [pr-template.md](pr-template.md) | variável `template` | Molde de saída do PR com placeholders |

## Placeholders

**user-template.md**
| Placeholder | Origem no script |
|-------------|-----------------|
| `{{DOMAIN_SECTION}}` | `domain_section` (pode ser vazio) |
| `{{TEMPLATE}}` | resultado final de `pr-template.md` após substituição |
| `{{DIFF}}` | `diff_truncated` |

**pr-template.md**
| Placeholder | Origem no script |
|-------------|-----------------|
| `{{TASK_LINE}}` | `task_line` (link Jira ou "Não identificado") |
| `{{TASK_REF}}` | `task_ref` (referência markdown do link) |
