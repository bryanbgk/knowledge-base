### 📁 `sql-server/linx.md`

# 👑 Comandos úteis para serem usados na MoneyP

### 🔍 Autorizar automaticamente NF-e

```sql
UPDATE nfe_parametros SET autorizar_automaticamente = 0 WHERE empresa = 1
```

### 🔍 Buscar config tributaria
```sql
SELECT 
    m.documento, 
    m.serie, 
    m.identificador, 
    '-' AS '-',
    pd.id_config_tributaria,
    ctd.id_config_tributaria_detalhe,
    m.cfop AS 'Natureza',
    cf.id_clientes_fornec_classe_fiscal AS 'ID CF',
    cfcf.descricao AS 'CF',
    '-' AS '-',
    m.id_cst_icms_fiscal
    ,* 
FROM movimento m
INNER JOIN clientes_fornec cf ON cf.cod_cliente = m.codigo_cliente
INNER JOIN clientes_fornec_classe_fiscal cfcf ON cfcf.id_clientes_fornec_classe_fiscal = cf.id_clientes_fornec_classe_fiscal
INNER JOIN produtos_detalhes pd ON pd.codigoproduto = m.codigoproduto AND pd.empresa = m.empresa
INNER JOIN config_tributaria_detalhes ctd ON ctd.cfop = m.cfop 
	AND ctd.id_config_tributaria = pd.id_config_tributaria 
	AND ctd.id_clientes_fornec_classe_fiscal = cf.id_clientes_fornec_classe_fiscal
WHERE m.identificador = 'C4666745-FF58-48CB-8E10-5A54CA21EDF4'
```


### 🔍 Senha usuario

```sql
USE portal

DECLARE @portal_login TABLE (id VARCHAR(50) COLLATE SQL_Latin1_General_CP1_CI_AS)

INSERT INTO @portal_login VALUES ('microvix.dev9016'),('microvix.teste9017')

SELECT * FROM @portal_login pl
OUTER APPLY (
	SELECT TOP 1 
		l.log_senha
	FROM log l
	WHERE l.log_login = pl.id
		AND l.log_senha <> ''
	ORDER BY l.log_id DESC
) AS l1(log_senha)
```


### 🔍 Checkar mensagens de erro NF-e rejeição SEFAZ

```sql
select * from nfe_comportamento

select REPLACE(codigo, 'M', '10'), * from nfe_comportamento order by CAST(REPLACE(codigo, 'M', '10') AS INT)
```


### 🔍 Descobrir o endereço de ambiente das rotinas

```sql
--  micportal
--  config_ambiente_acesso
--  empresas
--  config_rotina
--  SE NÃO
--    MV

--{ Ambientes
use portal

DECLARE @portal TABLE (id INT)
INSERT INTO @portal VALUES (9016) -- config_ambiente = 33
INSERT INTO @portal VALUES (9017) -- config_ambiente = 34
INSERT INTO @portal VALUES (950)  -- config_ambiente = 34

SELECT 
e.emp_codigo AS Portal
, e.id_config_ambiente
, cf.descricao
, cr.descricao
, cr.id_config_rotina
, car.id_config_ambiente_rotina
, car.endereco
FROM empresas e
INNER JOIN config_ambiente cf ON cf.id_config_ambiente = e.id_config_ambiente
INNER JOIN config_ambiente_rotina car ON car.id_config_ambiente = e.id_config_ambiente
INNER JOIN config_rotina cr ON cr.id_config_rotina = car.id_config_rotina
WHERE e.emp_codigo IN (SELECT p.id FROM @portal p)
AND cr.descricao like '%fiscal%'
ORDER BY e.emp_codigo

select id_config_ambiente, * from empresas where emp_codigo = 9016
select id_config_ambiente, * from config_ambiente where id_config_ambiente = 15
select * from config_rotina where descricao Like '%ES.%'


update config_ambiente_rotina
set endereco = 'http://192.168.18.94:9989'
where id_config_ambiente =  15
and id_config_rotina = 61

--}
```


### 🔍 POS ERP URL

```sql
--tabela servidor
select  * from servidor where servidor = 215 order by servidor desc -- 215 fui eu que criei
select servidor, * from empresas
```

## LISTA DE SERVIDORES QUE CRIEI:
- 215
- 122


### 🔍 Tipo de transações

```markdown
tipo_transacao
- J - Ajuste
- A
- C
- D
- E
- I - Complemento ou transferencia de icms
- M
- O
- P
- R - Reserva
- S
- T
- V
```


### 🔍 Senha usuario

```sql
```