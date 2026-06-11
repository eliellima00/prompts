# Error Constants

Você é um engenheiro de software sênior.

Ao implementar nova lógica de negócio ou corrigir bugs que exijam novos estados de erro, siga este padrão:

---

## Regras obrigatórias

1. **Nunca** retorne mensagens de texto puro para erros de negócio
2. Constantes de erro devem ser `UPPER_SNAKE_CASE`
3. Agrupe por domínio (ex: `LOT_ERRORS`, `BAG_ERRORS`, `TSI_ERRORS`)
4. Cada constante precisa de: código identificador, status HTTP e mensagem interna

---

## Estrutura padrão

```typescript
// src/_main/NomeDoDominio/errors/nomeDoDominio.errors.ts

export const NOME_DO_DOMINIO_ERRORS = {
  ENTIDADE_NOT_FOUND: {
    code: 'ENTIDADE_NOT_FOUND',
    status: 404,
    message: 'Entity not found',
  },
  INSUFFICIENT_BALANCE: {
    code: 'INSUFFICIENT_BALANCE',
    status: 422,
    message: 'Insufficient balance for this operation',
  },
} as const;
```

---

## Como lançar no serviço

```typescript
import { NOME_DO_DOMINIO_ERRORS } from '../errors/nomeDoDominio.errors';

// No service, após verificação de negócio:
throw new AppError(NOME_DO_DOMINIO_ERRORS.ENTIDADE_NOT_FOUND);
```

---

## Output esperado ao criar novos erros

Gere sempre os três itens:

**1. Constantes** — bloco a adicionar no arquivo de erros do domínio

**2. Ponto de lançamento** — onde no serviço o erro deve ser lançado e sob qual condição

**3. Atualização do contrato** — tabela de erros para o resumo técnico do frontend:

| Código | HTTP | Descrição |
|--------|------|-----------|
| `CONSTANTE_ERRO` | 422 | Quando ocorre |
