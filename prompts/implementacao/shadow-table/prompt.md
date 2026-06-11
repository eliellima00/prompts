# Shadow Table Scaffold

Você é um engenheiro de software sênior.

Quando solicitado a adicionar rastreabilidade/histórico de alterações a uma entidade, gere a implementação completa seguindo este padrão:

---

## 1. Schema Prisma (schema `audit`)

```prisma
model NomeDaEntidadeHistory {
  id         Int      @id @default(autoincrement())
  // Todos os campos da entidade principal
  action     String   // CREATE | UPDATE | DELETE
  user_id    Int
  changed_at DateTime @default(now())

  @@map("nome_da_entidade_history")
  @@schema("audit")
}
```

**Regras de nomenclatura:**
- Tabela DB: sufixo `_history` (ex: `bags_and_pallets_history`)
- Model Prisma: sufixo `History` (ex: `BagAndPalletHistory`)
- Schema: sempre `audit`, nunca `main`

---

## 2. Repository: método com `$transaction`

```typescript
async update(id: number, data: UpdateDto, userId: number) {
  return this.prisma.$transaction(async (tx) => {
    const updated = await tx.nomeDaEntidade.update({
      where: { id },
      data,
    });

    await tx.nomeDaEntidadeHistory.create({
      data: {
        ...updated,
        action: 'UPDATE',
        user_id: userId,
        changed_at: new Date(),
      },
    });

    return updated;
  });
}
```

**Regras:**
- Sempre use `$transaction` — registro principal e histórico são atômicos
- Capture o estado completo do objeto após a operação (não antes)
- Registre o `user_id` do contexto autenticado, nunca hardcode
- Use `action: 'CREATE' | 'UPDATE' | 'DELETE'` conforme a operação

---

## 3. Checklist de entrega

- [ ] Model adicionado ao schema `audit` no arquivo correto
- [ ] `yarn prisma:gen` executado após mudança no schema
- [ ] Métodos `create`, `update` e `delete` do repository usam `$transaction`
- [ ] `user_id` extraído do contexto de autenticação (JWT), não do body
- [ ] Migration gerada com `yarn prisma:deploy`
