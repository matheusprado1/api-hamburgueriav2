<h1 align="center">
  API Hamburgueria 2.0
</h1>

<p align = "center">
Este é o backend da aplicação <b>Hamburgueria 2.0</b> -  O objetivo dessa aplicação é conseguir elevar a hamburgueria, contendo cadastro, login e busca de produtos.
</p>

<p align="center">
  <a href="#endpoints">Endpoints</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>

## **Endpoints**

A API tem um total de 3 endpoints,  podendo cadastrar seu usuario, realizar login e busca de produtos. <br/>

A url base da API é https://api-hamburgueriav2.onrender.com

<h2 align ='center'> Criação de usuário </h2>

`POST /users - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "johndoe@email.com",
  "password": "123456",
  "name": "John Doe",
}
```

Caso dê tudo certo, a resposta será assim:

`POST /users - FORMATO DA RESPOSTA - STATUS 201`

```json
{
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQGdtYWlsLmNvbW0iLCJpYXQiOjE2Njk5MDMxMTEsImV4cCI6MTY2OTkwNjcxMSwic3ViIjoiMiJ9.WubTMTSE0ee2i5pN33w6vsI_GH1bq0a3K2aQx-3qCO8",
    "user": {
        "id": "c110dbb6-beb9-4682-ab63-2c12a570d66b",
        "name": "John Doe",
        "email": "johndoe@email.com"
    }  
}
```

<h2 align ='center'> Possíveis erros </h2>

Caso você acabe errando e mandando algum campo errado, a resposta de erro será assim:

A senha necessita de 6 caracteres.

`POST /users - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
"Password is too short"
```

Email já cadastrado:

`POST /users - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
"Email already exists"
```

<h2 align = "center"> Login </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "johndoe@email.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 200`

```json
{
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQGdtYWlsLmNvbW0iLCJpYXQiOjE2Njk5MDMxMTEsImV4cCI6MTY2OTkwNjcxMSwic3ViIjoiMiJ9.WubTMTSE0ee2i5pN33w6vsI_GH1bq0a3K2aQx-3qCO8",
    "user": {
        "id": "c110dbb6-beb9-4682-ab63-2c12a570d66b",
        "name": "John Doe",
        "email": "johndoe@email.com"
    }  
}
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

<h2 align = "center"> Autologin </h2>

`GET /users/:userId`

```
Não é necessário um corpo da requisição mas será necessária a autorização.
```

Caso dê tudo certo, a resposta será assim:

`GET /users/:userId - FORMATO DA RESPOSTA - STATUS 200`

```json
{
   "id": "c110dbb6-beb9-4682-ab63-2c12a570d66b",
   "name": "John Doe",
   "email": "johndoe@email.com"
} 
```

Está rota fornece os dados do usuário e um objeto e pode servir para uma feature de autologin.

<h2 align ='center'> Produtos </h2>

`GET /products`

```
Não é necessário um corpo da requisição mas será necessária a autorização.
```
Caso dê tudo certo, a resposta será assim:

`GET /products - FORMATO DA RESPOSTA - STATUS 200`

```json
[
	{
		"id": 1,
		"name": "Hamburguer",
		"category": "Sanduíches",
		"price": 14,
		"img": "https://i.imgur.com/Vng6VzV.png"
	},
	{
		"id": 2,
		"name": "X-Burguer",
		"category": "Sanduíches",
		"price": 16,
		"img": "https://i.imgur.com/soOUeeW.png"
	}

    {...}
]
```

---