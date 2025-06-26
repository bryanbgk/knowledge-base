### 📁 `sql-server/util-commands.md`

# 👑 Comandos úteis

### 🔍 Perquisar por tabelas e colunas

```sql
SELECT
    S.name AS Esquema
	, T.name AS Tabela
	, S.name + '.' + T.name AS EsquemaTabela
	--, C.name AS Coluna
FROM sys.objects AS T WITH (NOLOCK)
INNER JOIN sys.schemas AS S WITH (NOLOCK) ON T.schema_id = S.schema_id
--INNER JOIN sys.all_columns AS C WITH (NOLOCK) ON T.object_id = C.object_id
WHERE T.name LIKE '%outbox%'
    --AND C.name LIKE '%st%' 
    AND T.type = 'U' -- Tabelas do usuário
ORDER BY S.name, T.name;
```

### 🔍 Transações

```sql
begin transaction
-- (...)
rollback transaction
```

### 🔍 ?
```sql
```

# ⚡ Dicas de Performance

## ✨ Otimização básica

- Evite `SELECT *`, selecione apenas as colunas necessárias.
- Prefira `INNER JOIN` quando possível, evita leituras desnecessárias.
- Crie índices nas colunas usadas em `JOIN`, `WHERE`, `ORDER BY`.
- Cuidado com subqueries correlacionadas — tente reescrever com `JOIN` ou `OUTER APPLY`.

## 🛠 Ferramentas úteis

- `SET STATISTICS TIME ON` — mostra tempo de execução.
- `SET STATISTICS IO ON` — mostra leituras lógicas/físicas.
- `EXEC sp_whoisactive` — ver sessões ativas com consumo de recursos.
- `Query Store` — histórico de performance de queries no SQL Server.

## 🧠 Boas práticas

- Teste com dados reais ou representativos.
- Use CTEs com parcimônia: podem gerar planos ruins se mal utilizados.
- Sempre analise o plano de execução (Estimated e Actual Plan).