![simge-devs](https://user-images.githubusercontent.com/3603793/131751022-fda4146c-9ada-4ad0-82fc-d8f0a73acd3f.png)

# EM CONSTRUÇÃO
Se baseando fortemente na base da juntos somos mais / Juntos somos devs

# Diretriz
Lorem y...

1. [Padrões de arquivos](#1-padrões-de-arquivos-⬆)
2. [HTML](#2-html-⬆)
3. [Bootstrap](#3-bootstrap-⬆)
4. [Quasar](#4-quasar-⬆)
5. [Vue](#5-vue-⬆)
6. [JavaScript](#6-javascript-⬆)
7. [TypeScript](#7-typescript-⬆)
8. [CSS](#8-css-⬆)
9. [GraphQL](#9-graphql-⬆)

---

## 1. Padrões de arquivos **[⬆](#diretriz)**

- 1.1 [Formatação](#11-formatação-⬆)
- 1.2 [Arquitetura de Diretórios](#12-arquitetura-de-diretórios-⬆)
- 1.3 [Comentários](#13-comentários-⬆)
- 1.4 [Bibliotecas](#14-bibliotecas-⬆)

### 1.1 Formatação **[⬆](#1-padrões-de-arquivos-⬆)**
### 1.2 Arquitetura de Diretórios **[⬆](#1-padrões-de-arquivos-⬆)**
### 1.3 Comentários **[⬆](#1-padrões-de-arquivos-⬆)**

Evite utilizar comentários no código, mantendo o código autoexplicativo, com nomes de variáveis, métodos entre outros. 

**✅ Bom:**

```html
<div>
    ...
</div>
```

```js
const calculaAlgo = () => {};
```

**❌ Ruim:**

```html
<!-- Titulo -->
<div>
    ...
</div>
```

```js
// Calcula algo
const teste = () => {};
```

#### Melhorias futuras

Os comentários são só adequados para futuras melhorias (TODOs). Ao escrever um TODO, tente resumir escrevendo apenas uma sugestão de melhoria, apenas em últimos casos descreva o problema.

### 1.4 Bibliotecas **[⬆](#1-padrões-de-arquivos-⬆)**

Foi passado uma boa parte de funções que eram usadas entre os sistemas para a lib simge-utils, dessa forma, a mesma função pode ser utilizada entre as aplicações agrupando uma possível manutenção em um único lugar. Verifique e importe quando possível da lib:

**✅ Bom:**

```js
import { DateFormatter, NumberFormatter, EnumConverter, Pagination, getPagination, showNotify } from 'simge-utils';
```

**❌ Ruim:**

```js
import { DateFormatter } from 'src/utils/date-formatter';
import { NumberFormatter } from 'src/utils/number-formatter';
import { getPagination } from 'src/utils/pagination';
import { showNotify } from 'src/utils/notify';
import { EnumConverter } from 'src/utils/enum-converter';
```

---

## 2. HTML **[⬆](#diretriz)**

---

## 3. Bootstrap **[⬆](#diretriz)**

Ao utilizar as classes prédefinidas do bootstrap para [grid responsivo](https://getbootstrap.com/docs/4.0/layout/grid/), se atentar com redundancia de definições, lembrando que as classes priorizam o menor valor disponibilizado e os tamanhos responsivos de colunas não disponibilizados obedecem os valores menores disponibilizados:

**✅ Bom:**

```html
<div class="col-12 col-lg-6">
    ...
</div>
```

**❌ Ruim:**

```html
<div class="col-12 col-sm-12 col-md-12 col-lg-6">
    ...
</div>
```

---

## 4. Quasar **[⬆](#diretriz)**

---

## 5. Vue **[⬆](#diretriz)**
- 5.1 [Componentes](#51-componentes-⬆)
- 5.2 [Organização estrutural](#52-organização-estrutural-⬆)
- 5.3 [Stores](#53-stores-⬆)

### 5.1 Componentes **[⬆](#5-vue-⬆)**

Um dos grandes benefícios do Vue é a componentização, ou seja, permitir separar 'pedaços' de uma interface afim de possibilitar a reutilização desse 'pedaço' em outros lugares, diminuindo redundancia de código.

#### Cards

Estruture os componentes de cards no HTML de forma que não tenham cards dentro de cards. Caso exista um formulário, englobe o trecho do código dentro do componente simple-form-default. Caso contrário, utilize o simple-card-default.

```html

```

### 5.2 Organização estrutural **[⬆](#5-vue-⬆)**

### 5.3 Stores **[⬆](#5-vue-⬆)**

---

## 6. JavaScript **[⬆](#diretriz)**
- 6.1 [Escopos](#61-escopos-⬆)
- 6.2 [Laços](#62-lacos-⬆)
- 6.2 [Laços](#62-lacos-⬆)
- 6.2 [Laços](#62-lacos-⬆)
- 6.2 [Laços](#62-lacos-⬆)
### Escopos **[⬆](#6-javascript-⬆)**
### Laços **[⬆](#6-javascript-⬆)**
### Condicionais **[⬆](#6-javascript-⬆)**
### Validação **[⬆](#6-javascript-⬆)**
### Métodos Assíncronos **[⬆](#6-javascript-⬆)**

---

## 7. TypeScript **[⬆](#diretriz)**

Devemos ter certeza da tipagem das variáveis para evitar warnings, lembrando que durante o desenvolvimento devemos manter um código limpo, sem erros e sem warnings.

### 7.1 Tipando arrays

Ao tipar arrays, podemos melhorar a legibilidade tipando um array com `[]` ao invés de `Array<>`, além disso, ao declarar as Columns devemos tipar qual objeto será listado, dessa forma não será necessário tipar a `row`, caso tenha a necessidade de apresentar uma coluna não existente no objeto fragment, podemos criar uma interface custom para adicionar campos extras:

**✅ Bom:**

```ts
const columns: Column<GetExemploFragment>[] = [
    {
        name: 'exemploId',
        ...
        field: (row) => row.propriedade,
    },
];
```

**❌ Ruim:**

```ts
const columns: Array<Column> = [
    {
        name: 'exemploId',
        ...
        field: (row: GetExemploFragment) => row.propriedade,
    },
];
```

---

## 8. CSS **[⬆](#diretriz)**

---

## 9. GraphQL **[⬆](#diretriz)**
### Fragments **[⬆](#9-graphql-⬆)**
### Queries **[⬆](#9-graphql-⬆)**
