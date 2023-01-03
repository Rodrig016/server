<h1 align="center">
  Patrocine um Atleta - API
</h1>

<p align = "center">
Este é o JSON-Server Fake-API da aplicação Patrocine um atleta - Uma aplicação onde é possível conectar atletas que precisam de apoio e quem pode dar apoio a esses atletas ! O objetivo dessa aplicação é conseguir criar um frontend de qualidade em grupo, com tudo o que aprendemos no M3 - E desenvolver hard skills e soft skills.
</p>

# **Endpoints**

A API tem um total de 4 endpoints, login, registe, users, athlete.

<a href="https://insomnia.rest/run/?label=Patrocine%20um%20Atleta&uri=https%3A%2F%2Fgithub.com%2FAnderson-Keller%2Fjson-server-base-Adote-um-Atleta%2Fblob%2Fmaster%2Finsomnia.json" target="_blank"><img src="https://insomnia.rest/images/run.svg" alt="Run in Insomnia"></a>

A url base da API é https://json-server-fakeapi-adoteumatleta.onrender.com

## Rotas que não precisam de autenticação

<h2 align ='center'> Listando Atletas </h2>

Nessa aplicação o usuário sem fazer login ou se cadastrar pode ver os ateltas já cadastrados na plataforma, na API podemos acessar a lista dessa forma: <br/>
Aqui conseguimos ver os atletas, sua idade, e para qual instituição pertence.

`GET /athlete - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "name": "José da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "Rio de Janeiro - RJ",
  "userId": "1",
  "id": 1
}
```

Podemos utilizar os query params para mudar a lista, fazer filtros, etc..

`GET /athlete/?age=20 - STATUS 200`</br>
<span>Mostra todos os atletas com 20 anos.</span>

`GET /athlete/?_sort=name&_order=desc - STATUS 200`</br>
<span>Mostra todos os atletas ordenado em ordem decrescente do nome.</span>

`GET /athlete/?_sort=name&_order=asc - STATUS 200`</br>
<span>Mostra todos os atletas ordenado em ordem crescente do nome.</span>

`GET /athlete/?_page=1&_limit=2 - STATUS 200`
<span>Mostra 2 atletas da página 1</span>

<p>Para acessar um atleta específico:</p>

`GET /athlete/id - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "name": "José da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "Rio de Janeiro - RJ",
  "userId": "1",
  "id": 1
}
```

<h2 align ='center'> Criação de usuário </h2>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
  "name": "João da Silva",
  "CPF": "189.064.257-67",
  "email": "exemplo@email.com",
  "password": "123Jo@"
}
```

O campo senha precisa ter: no mínimo 6 caracteres sendo eles: 1 letra minúscula, 1 maiúscula, 1 número e 1 caractere especial. </br>
Todos os campos desse requisição são do tipo string.

`POST /register - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImV4ZW1wbG9AZW1haWwuY29tIiwiaWF0IjoxNjcyNzYyNzk5LCJleHAiOjE2NzI3NjYzOTksInN1YiI6IjMifQ.FbrBLiP_LcPb8vEumymsyCmMzXiPR8U2GtQvWM4ZUug",
  "user": {
    "email": "exemplo@email.com",
    "name": "João da Silva",
    "CPF": "189.064.257-67",
    "id": 3
  }
}
```

<h2 align ='center'> Possíveis erros </h2>

`POST /register - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
"Email already exists"
```

<h2 align = "center"> Login </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "exemplo@email.com",
  "password": "123Jo@"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImV4ZW1wbG9AZW1haWwuY29tIiwiaWF0IjoxNjcyNzYyNzk5LCJleHAiOjE2NzI3NjYzOTksInN1YiI6IjMifQ.FbrBLiP_LcPb8vEumymsyCmMzXiPR8U2GtQvWM4ZUug",
  "user": {
    "email": "exemplo@email.com",
    "name": "João da Silva",
    "CPF": "189.064.257-67",
    "id": 3
  }
}
```

Com essa resposta, vemos que temos duas informações, o user e o token respectivo, dessa forma você pode guardar o token e o usuário logado no localStorage para fazer a gestão do usuário no seu frontend.

<h2 align ='center'> Possíveis erros </h2>

`POST /login - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
"Cannot find user"
```

`POST /login - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
"Incorrect password"
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:<br/>

> Authorization: Bearer {token}

Após o usuário estar logado, ele deve conseguir ver e fazer doações para os atletas.

<h2 align ='center'> Buscar Perfil do usuário logado (token) </h2>

`GET /users/id - FORMATO DA REQUISIÇÃO`

<blockquote>Na requisição apenas é necessário o TOKEN, a aplicação ficará responsável em buscar o id do usuário no token e retorna ele.</blockquote>

<br>

`GET /users/id - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "email": "exemplo@email.com",
  "password": "$2a$10$dKeuOBGNMBhc8Vl9oATwBecoUkmK8u7Jz0fnsEJVtKYQDDqkTBuEu",
  "name": "João da Silva",
  "CPF": "189.064.257-67",
  "id": 3
}
```

`DELETE /users/id - FORMATO DA RESPOSTA - STATUS 200`

```json
{}
```

<h2 align ='center'> Cadastro de atletas </h2>

`POTS /users/id/athlete - FORMATO DA REQUISIÇÃO`

<span>É válido somente o id do admin</span>

<blockquote>Na requisição apenas é necessário o TOKEN.</blockquote></br>

`POST /users/id/athlete - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "name": "José da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "Rio de Janeiro - RJ"
}
```

`DELETE /athlete/id - FORMATO DA RESPOSTA - STATUS 200`

```json
{}
```

`PATCH /athlete/1 - FORMATO DA REQUISIÇÃO` </br>

<blockquote>Na requisição apenas é necessário o TOKEN</blockquote> </br>

```json
{
  "age": 30
}
```

`PATCH /athlete/1 - FORMATO DA RESPOSTA - STATUS 200` </br>

```json
{
  "name": "José da Silva",
  "age": 30,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "Rio de Janeiro - RJ",
  "userId": "1",
  "id": 1
}
```

`PUT /athlete/1 - FORMATO DA REQUISIÇÃO` </br>

<blockquote>Na requisição apenas é necessário o TOKEN, e no body é necessário passar o id do admin (o "dono" do atleta)</blockquote></br>

```json
{
  "name": "José da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "São Paulo - SP",
  "userId": "1"
}
```

`PUT /athlete/1 - FORMATO DA RESPOSTA - STATUS 200` </br>

```json
{
  "name": "José da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "São Paulo - SP",
  "userId": "1",
  "id": 1
}
```

<p>Feito com carinho ♥</p>
