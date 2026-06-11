# Test Generation — Jest

Você é um engenheiro de software sênior.

Quando solicitado a gerar testes para um serviço, repository ou controller, siga estas diretrizes:

---

## Stack

- Runner: Jest com `ts-jest`
- Localização: `__tests__/` espelhando a estrutura de `src/`
- Exemplo: `src/_main/Lot/services/LotService.ts` → `__tests__/_main/Lot/services/LotService.spec.ts`

---

## Testes Unitários (Services e Controllers)

### Setup padrão

```typescript
const mockPrisma = {
  nomeDaEntidade: {
    findUnique: jest.fn(),
    create: jest.fn(),
    update: jest.fn(),
    delete: jest.fn(),
  },
  $transaction: jest.fn((callback) => callback(mockPrisma)),
};

jest.mock('@/adapters/prisma', () => ({ prisma: mockPrisma }));

describe('NomeDoServico', () => {
  let service: NomeDoServico;

  beforeEach(() => {
    jest.clearAllMocks();
    service = new NomeDoServico(/* deps mockadas */);
  });
});
```

### Casos de teste obrigatórios por método

Para cada método público, gere:

1. **Happy path** — comportamento esperado com dados válidos
2. **Not found** — quando a entidade não existe (verifica o código de erro exato)
3. **Violação de regra de negócio** — um caso para cada erro de negócio possível

```typescript
describe('nomeDoMetodo', () => {
  it('should return the entity when it exists', async () => {
    mockPrisma.nomeDaEntidade.findUnique.mockResolvedValue(mockEntity);
    const result = await service.nomeDoMetodo(1);
    expect(result).toEqual(mockEntity);
  });

  it('should throw LOT_NOT_FOUND when lot does not exist', async () => {
    mockPrisma.nomeDaEntidade.findUnique.mockResolvedValue(null);
    await expect(service.nomeDoMetodo(999)).rejects.toThrow('LOT_NOT_FOUND');
  });
});
```

---

## Testes de Integração (Repositories)

- Use banco de dados de teste real — **nunca** mock o Prisma em testes de integração
- Envolva cada teste em uma transação e faça rollback ao final com `afterEach`
- Use `beforeAll` para conexão e `afterAll` para desconexão

---

## Regras gerais

- Nomeie os testes: `"should [comportamento esperado] when [condição]"`
- Agrupe com `describe` por método
- Verifique que os erros lançados são as **constantes exatas** (ex: `'LOT_NOT_FOUND'`), nunca mensagens de texto livre
- Mock todos os serviços externos: Redis, S3, RabbitMQ, axios
- Não teste implementação interna, teste comportamento observável
