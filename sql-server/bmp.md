### 📁 `sql-server/bmp.md`

# 👑 Comandos úteis para serem usados na BMP

### 🔍 Pegar conta por codigo

```sql
SELECT
Numero + Digito AS NumeroDigito
, *
FROM cad.Conta WITH(NOLOCK)
WHERE Codigo = '9730F3E2-7FEC-4A5C-72C5-08DAB2A86A91'
```

### 🔍 Update de CodigoPerfilFrontEnd para novas contas
```sql
UPDATE ofec
SET ofec.CodigoPerfilFrontEnd = '5C4433D7-4F6C-4252-CDE9-08D9204BB04F'
FROM cad.OperadorFrontEndConta ofec WITH(NOLOCK)
INNER JOIN cad.OperadorFrontEnd ofe WITH(NOLOCK) 
    ON ofec.CodigoOperadorFrontEnd = ofe.Codigo
WHERE ofe.Email = 'bryan.konowalow@moneyp.com.br';
```