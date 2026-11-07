# Exercícios de SQL: Produtos, Estoque e Clientes

Lista de exercícios práticos de SQL (T-SQL / SQL Server) cobrindo desde a criação de tabelas até consultas com `JOIN`, subqueries e tratamento de valores `NULL` com `CASE`.

## Sobre o projeto

Os exercícios simulam o banco de dados de uma loja: cadastro de produtos, categorias, controle de estoque e cadastro de clientes. Estão divididos em dois níveis:

### Iniciante

| # | Exercício | Conceitos |
|---|-----------|-----------|
| 1 | Criar a tabela `Produto` | `CREATE TABLE`, `PRIMARY KEY`, `IDENTITY` |
| 2 | Inserir 10 produtos | `INSERT INTO ... VALUES` |
| 3 | Atualizar o preço de venda | `UPDATE`, `WHERE` |
| 4 | Listar os 5 produtos mais caros | `SELECT TOP`, `ORDER BY ... DESC` |
| 5 | Excluir produtos em prejuízo | `DELETE`, condição entre colunas |

### Intermediário

| # | Exercício | Conceitos |
|---|-----------|-----------|
| 1 | Criar `ProdutoCategoria` e `ProdutoEstoque` | `FOREIGN KEY`, `ON DELETE CASCADE` |
| 2 | Inserir categorias e estoque | `INSERT INTO ... SELECT` |
| 3 | Listar nome, categoria e quantidade | `INNER JOIN` |
| 4 | Inserir produtos do tipo roupa | `INSERT` em múltiplas tabelas |
| 5 | Excluir produtos da categoria "Roupas" | `DELETE` com subquery (`IN`) |
| 6 | Criar a tabela `Cliente` | Campos opcionais (`NULL`) |
| 7 | Gerar lista de nomes completos | `CASE`, `DISTINCT`, concatenação |

## Estrutura

```
.
├── exercicios_sql.txt   # Todos os scripts comentados
└── README.md
```

## Como executar

1. Abra o **SQL Server Management Studio (SSMS)** ou outro cliente SQL Server.
2. Crie um banco de dados de teste:
   ```sql
   CREATE DATABASE LojaExercicios;
   GO
   USE LojaExercicios;
   ```
3. Execute os scripts de `exercicios_sql.txt` **na ordem em que aparecem**, pois os exercícios dependem uns dos outros (por exemplo, o `DELETE` de prejuízo acontece antes de inserir categorias).

## Observações

- **MySQL:** a única adaptação necessária é trocar `TOP 5` por `LIMIT 5` no final da consulta do exercício 4 (Iniciante). Em MySQL, `IDENTITY(1,1)` também deve ser trocado por `AUTO_INCREMENT`, e a concatenação com `+` por `CONCAT()`.
- **`ON DELETE CASCADE`:** sem ele, excluir um produto que possui categoria ou estoque gera erro de chave estrangeira.
- **`NULL` na concatenação:** no SQL Server, `'texto' + NULL` resulta em `NULL`. Por isso o `CASE` é usado para montar o nome completo do cliente.
- Dois produtos do exercício 2 têm prejuízo de propósito (`Cabo HDMI` e `Hub USB`) para testar o `DELETE` do exercício 5.

## Tecnologias

- SQL Server (T-SQL)
- SQL Server Management Studio (SSMS)

