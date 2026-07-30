# Modelagem de Dados

> Competência 4 — Gestão de Dados e Persistência  
> Curso Move Tech — Magalu × Prósper Digital Skills

---

## Contexto

A API de pedidos precisa guardar os dados de forma permanente. Até agora, os dados ficavam na memória do servidor — ao reiniciar o container, tudo era perdido.

Nesta competência, vamos conectar a aplicação a um banco de dados PostgreSQL provisionado no DBaaS da Magalu Cloud.

---

## Entidades

A aplicação trabalha com duas entidades principais:

### Pedido (`orders`)

Representa uma compra feita por um cliente.

| Coluna | Tipo | Descrição |
|--------|------|-----------|
| `id` | `VARCHAR` (PK) | Identificador único do pedido (UUID) |
| `customer` | `VARCHAR` | Nome do cliente |
| `status` | `VARCHAR` | Situação do pedido: `open` ou `cancelled` |
| `created_at` | `TIMESTAMP WITH TIME ZONE` | Data e hora de criação |

### Item (`items`)

Representa um produto dentro de um pedido.

| Coluna | Tipo | Descrição |
|--------|------|-----------|
| `id` | `VARCHAR` (PK) | Identificador único do item (UUID) |
| `order_id` | `VARCHAR` (FK) | Referência ao pedido ao qual pertence |
| `sku` | `VARCHAR` | Código do produto |
| `description` | `VARCHAR` | Descrição do produto |
| `quantity` | `INTEGER` | Quantidade |

---

## Relacionamento

Um pedido pode ter vários itens. Um item pertence a exatamente um pedido.

```
orders                    items
──────────────────        ──────────────────────
id (PK)         ◄────┐    id (PK)
customer             └─── order_id (FK)
status                    sku
created_at                description
                          quantity
```

**Tipo:** 1 para N (um pedido → muitos itens)

---

## Como as tabelas são criadas

As tabelas são criadas automaticamente pela aplicação na primeira vez que ela se conecta ao banco, a partir dos modelos definidos em `app/models.py`.

Não é necessário rodar SQL manualmente.

---

## Configuração da conexão

A aplicação lê a string de conexão a partir da variável de ambiente `DATABASE_URL`:

```
postgresql://<usuario>:<senha>@<host>:<porta>/<nome-do-banco>
```

No Kubernetes, essa variável é fornecida via Secret:

```bash
kubectl create secret generic db-secret \
  --from-literal=url=postgresql://usuario:senha@<host-mgc>/orders
```
