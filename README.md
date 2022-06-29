<h1 align="center">
  FakeAPI
</h1>

# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2.

<p align="center">
  <a href="#endpoints">Endpoints</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>

## **Endpoints**

A API tem um total de 4 endpoints, sendo em volta principalmente do usuário - podendo cadastrar seu perfil, logar e fazer posts públicos e privados. <br/>

O url base da API é https://json-server-fakeapi-kenzie.herokuapp.com/

## Rotas que não precisam de autenticação

<h2 align ='center'> Criação de usuário </h2>

`POST /users - FORMATO DA REQUISIÇÃO`

Campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

```json
{
  "email": "johndoe@email.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /users - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InJlbmFuQGdtYWlsLmNvbSIsImlhdCI6MTY1NjUyMzAyOCwiZXhwIjoxNjU2NTI2NjI4LCJzdWIiOiIyIn0.3RCF12RserD2aYUWohRKireDxNDIvEYFm3K4ynuBiPg",
  "user": {
    "email": "johndoe@email.com",
    "id": 1
  }
}
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

`POST /sessions - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InJlbmFuQGdtYWlsLmNvbSIsImlhdCI6MTY1NjUyNTQ2MSwiZXhwIjoxNjU2NTI5MDYxLCJzdWIiOiIyIn0.TMCxCkVwPbzQ5ZhjcIil7PIdZ1AGCDtPfAI2p0znalk",
  "user": {
    "email": "renan@gmail.com",
    "id": 2
  }
}
```

Com essa resposta, vemos que temos duas informações, o user e o token respectivo, dessa forma você pode guardar o token e o usuário logado no localStorage para fazer a gestão do usuário no seu frontend.

<h2 align = "center"> Posts </h2>

`GET /posts - FORMATO DA REQUISIÇÃO`

Caso dê tudo certo, a resposta será assim:

`GET /posts - FORMATO DA RESPOSTA - STATUS 200`

```json
[
  {
    "message": "mensagem bacana",
    "id": 1
  }
]
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

Após o usuário estar logado, criar posts públicos.

<h2 align ='center'> Criar posts públicos</h2>

`POST /posts - FORMATO DA REQUISIÇÃO`

```json
{
  "message": "React"
}
```

`POST /posts - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "message": "mensagem bacana",
  "id": 1
}
```

<h2 align ='center'> Criar posts privados </h2>

`POST /privatePosts - FORMATO DA REQUISIÇÃO`

```json
{
  "message": "mensagem privada bacana",
  "userId": 1
}
```

`POST /posts - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "message": "mensagem privada bacana",
  "userId": 1,
  "id": 1
}
```

---

Feito com ♥ by Renan :wave:
