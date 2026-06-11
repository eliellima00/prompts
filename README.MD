# Prompts Repository

Repositório centralizado de prompts estruturados para uso com modelos de linguagem, organizados por categoria e com documentação padronizada.

---

## Índice

### Exploração e Planejamento

_Em breve_

### Documentação
| Prompt | Objetivo |
|--------|----------|
| [API Contract](prompts/documentacao/api-contract/doc.md) | Geração de resumos técnicos de contratos de API para o frontend |

### Implementação
| Prompt | Objetivo |
|--------|----------|
| [Shadow Table Scaffold](prompts/implementacao/shadow-table/doc.md) | Scaffold completo de shadow tables com padrão de auditoria |
| [Test Generation](prompts/implementacao/test-gen/doc.md) | Geração de testes Jest com mocks do Prisma e serviços externos |
| [Error Constants](prompts/implementacao/error-constants/doc.md) | Criação de constantes de erro de negócio e integração com errorHandler |

### Utils
| Prompt | Objetivo |
|--------|----------|
| [PR Description](prompts/utils/pr-description/doc.md) | Geração de descrições estruturadas para Pull Requests |
| [Conventional Commit](prompts/utils/commit/doc.md) | Geração de mensagens de commit seguindo Conventional Commits |

---

## Estrutura de Cada Prompt

Cada prompt é armazenado em sua própria pasta com dois arquivos:
- `prompt.md` — O prompt em texto puro, pronto para uso
- `doc.md` — Documentação: objetivo, modelos testados, observações e histórico de atualizações
