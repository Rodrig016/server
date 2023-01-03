<h1 align="center">
  Patrocine um Atleta - API
</h1>

<p align = "center">
Este é o JSON-Server Fake-API da aplicação Patrocine um atleta - Uma aplicação onde é possível conectar atletas que precisam de apoio e quem pode dar apoio a esses atletas ! O objetivo dessa aplicação é conseguir criar um frontend de qualidade em grupo, com tudo o que aprendemos no M3 - E desenvolver hard skills e soft skills.
</p>

# **Endpoints**

A API tem um total de 4 endpoints, login, registe, users, athlete.

<a href="https://insomnia.rest/run/?label=Patrocine%20um%20Atleta&uri=https%3A%2F%2Fjson-server-fakeapi-adoteumatleta.onrender.com%2Finsomnia.json" target="_blank"><img src="https://insomnia.rest/images/run.svg" alt="Run in Insomnia"></a>

A url base da API é https://json-server-fakeapi-adoteumatleta.onrender.com

## Rotas que não precisam de autenticação

<h2 align ='center'> Listando Atletas </h2>

Nessa aplicação o usuário sem fazer login ou se cadastrar pode ver os ateltas já cadastrados na plataforma, na API podemos acessar a lista dessa forma: <br/>
Aqui conseguimos ver os atletas, sua idade, e para qual instituição pertence.

`GET /athlete - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "name": "José",
  "lastname": "da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "Rio de Janeiro - RJ",
  "userId": "1",
  "id": 1
}
```

Podemos utilizar os query params para mudar a lista, fazer filtros, etc..

`GET /athlete/?age=20 - FORMATO DA RESPOSTA - STATUS 200`

<span>Obs: Mostra todos os atletas com 20 anos.</span>

```json
{
  "name": "José",
  "lastname": "da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "Rio de Janeiro - RJ",
  "userId": "1",
  "id": 1
}
...
```

Para acessar um atleta específico:

`GET /athlete/id - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "name": "José",
  "lastname": "da Silva",
  "age": 20,
  "img": "https://imgs.search.brave.com/G4KDpFlyrJ0Jk1kz1LotjEp5nWfQZGuGDo-7tiJp25A/rs:fit:880:670:1/g:ce/aHR0cHM6Ly93d3cu/cGluY2xpcGFydC5j/b20vcGljZGlyL21p/ZGRsZS8xNTUtMTU1/OTMxNl9tYWxlLWF2/YXRhci1jbGlwYXJ0/LnBuZw",
  "bio": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in varius sapien. Fusce sagittis euismod enim, ac pellentesque ex sodales ac. Aliquam erat volutpat. Morbi faucibus lacus non elementum cursus. In mattis ante in nibh rhoncus vehicula. Praesent rutrum elit vel justo pharetra, a consequat felis varius. Donec ullamcorper nunc vel tortor consectetur vehicula. Morbi eros arcu, tincidunt gravida egestas sit amet, molestie id sem. Nullam ornare molestie urna, ut blandit leo commodo in. In congue interdum odio a elementum. Nam nec facilisis odio. Duis scelerisque tortor at felis placerat, at interdum ex maximus. Cras id commodo urna. Fusce et feugiat risus, vel fermentum dolor. Donec non ligula massa.",
  "locality": "Rio de Janeiro - RJ",
  "userId": "1",
  "id": 1
}
```
