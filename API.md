# API
A fim de facilitar a implementação com serviços externos, a VeriAgro fornece uma API. A seguir são os endpoints da API.

## Dados gerais

Versão atual: v0.1.1

Linguagem de programação do backend atual: Typescript

URL base da API: https://sra-system-backend-999646529726.southamerica-east1.run.app/

> [!NOTE]\
> A API ainda está em no começo do desenvolvimento. Dados gerais sujeitos a mudança.
 
# Endpoints
## Teste de conexão
#### GET /
---
###### Resposta:
```
Hello World!
```
## Criação
#### POST /location
---
É o endpoint de criação / cadastro de local.
###### Exemplo:
```json
{
  "name": "O nome do local",
  "description": "Uma descrição do local",
  "latitude" : -1.234567,
  "longitude": 12.345678
}
```
###### Resposta:
```json
{
   "name":"O nome do local",
   "description":"Uma descrição do local",
   "latitude":-1.234567,
   "longitude":12.345678,
   "_id":"67ae6bcf5ef34c6be30e9ef9",
   "__v":0
}
```
#### POST /animal
---
É o endpoint de criação / cadastro de animal.
###### Exemplo:
```json
{
  "name": "O nome do animal",
  "birth_date": "2025-02-11T00:00:00.000Z",
  "birth_location": "Um id de local de nascimento",
  "sex": "M ou F",
  "breed": "A raça do animal"
}
```
###### Resposta:
```json
{
   "name":"O nome do animal",
   "birth_date":"2025-02-11T00:00:00.000Z",
   "birth_location":{
      "_id":"67ae6bcf5ef34c6be30e9ef9",
      "name":"O nome do local",
      "description":"Uma descrição do local",
      "latitude":-1.234567,
      "longitude":12.345678,
      "__v":0
   },
   "sex":"M ou F",
   "breed":"A raça do animal",
   "register_date":"2025-02-13T22:09:03.936Z",
   "_id":"67ae6d7f5ef34c6be30e9efe",
   "__v":0
}
```
#### POST /event
---
É o endpoint de criação / cadastro de evento.

O tipo é um número de 1-4, sendo: 

VACINACAO = 1,
MOVIMENTO = 2,
ABATE = 3,
REGISTRO = 4,
###### Exemplo:
```json
{
   "type_number": 1,
   "description": "Exemplo com vacinação de animal. Mais informações vão aqui",
   "date": "2025-02-12T00:00:00.000Z",
   "animal_id": "67ae6d7f5ef34c6be30e9efe",
   "location_id": "67ae6bcf5ef34c6be30e9ef9"
}
```
###### Resposta:
```json
{
   "type_number":1,
   "description":"Exemplo com vacinação de animal. Mais informações vão aqui",
   "date":"2025-02-12T00:00:00.000Z",
   "animal":{
      "_id":"67ae6d7f5ef34c6be30e9efe",
      "name":"O nome do animal",
      "birth_date":"2025-02-11T00:00:00.000Z",
      "birth_location":"67ae6bcf5ef34c6be30e9ef9",
      "sex":"M ou F",
      "breed":"A raça do animal",
      "register_date":"2025-02-13T22:09:03.936Z",
      "__v":0
   },
   "location":{
      "_id":"67ae6bcf5ef34c6be30e9ef9",
      "name":"O nome do local",
      "description":"Uma descrição do local",
      "latitude":-1.234567,
      "longitude":12.345678,
      "__v":0
   },
   "_id":"67ae71d2e9a33e5b883475da",
   "__v":0
}
```
## Leitura
#### GET /location/{id}
---
###### Resposta:
```json
{
   "name":"O nome do local",
   "description":"Uma descrição do local",
   "latitude":-1.234567,
   "longitude":12.345678,
   "_id":"67ae6bcf5ef34c6be30e9ef9",
   "__v":0
}
```
#### GET /animal/{id}
---
###### Resposta:
```json
{
   "name":"O nome do animal",
   "birth_date":"2025-02-11T00:00:00.000Z",
   "birth_location":{
      "_id":"67ae6bcf5ef34c6be30e9ef9",
      "name":"O nome do local",
      "description":"Uma descrição do local",
      "latitude":-1.234567,
      "longitude":12.345678,
      "__v":0
   },
   "sex":"M ou F",
   "breed":"A raça do animal",
   "register_date":"2025-02-13T22:09:03.936Z",
   "_id":"67ae6d7f5ef34c6be30e9efe",
   "__v":0
}
```
#### GET /event/{id}
---
###### Resposta:
```json
{
   "type_number":1,
   "description":"Exemplo com vacinação de animal. Mais informações vão aqui",
   "date":"2025-02-12T00:00:00.000Z",
   "animal":{
      "_id":"67ae6d7f5ef34c6be30e9efe",
      "name":"O nome do animal",
      "birth_date":"2025-02-11T00:00:00.000Z",
      "birth_location":"67ae6bcf5ef34c6be30e9ef9",
      "sex":"M ou F",
      "breed":"A raça do animal",
      "register_date":"2025-02-13T22:09:03.936Z",
      "__v":0
   },
   "location":{
      "_id":"67ae6bcf5ef34c6be30e9ef9",
      "name":"O nome do local",
      "description":"Uma descrição do local",
      "latitude":-1.234567,
      "longitude":12.345678,
      "__v":0
   },
   "_id":"67ae71d2e9a33e5b883475da",
   "__v":0
}
```
#### GET /events/animal{id}
---
Retorna todos os eventos cadastrados a um animal
###### Resposta:
```json
[
   {
      "_id":"67ac007d27f4da090d87e3b4",
      "type_number":1,
      "description":"Ela foi vacinada bem direitinho",
      "date":"2025-02-11T22:58:00.000Z",
      "animal":{
         "_id":"67ae6d7f5ef34c6be30e9efe",
         "name":"O nome do animal",
         "birth_date":"2025-02-11T00:00:00.000Z",
         "birth_location":"67ae6bcf5ef34c6be30e9ef9",
         "sex":"M ou F",
         "breed":"A raça do animal",
         "register_date":"2025-02-13T22:09:03.936Z",
         "__v":0
      },
      "location":{
         "_id":"67ae6bcf5ef34c6be30e9ef9",
         "name":"O nome do local",
         "description":"Uma descrição do local",
         "latitude":-1.234567,
         "longitude":12.345678,
         "__v":0
      },
      "__v":0
   },
   {
      "_id":"67ac00c627f4da090d87e3b8",
      "type_number":3,
      "description":"Peso final: 70kg",
      "date":"2025-02-11T22:59:00.000Z",
      "animal":{
         "_id":"67ae6d7f5ef34c6be30e9efe",
         "name":"O nome do animal",
         "birth_date":"2025-02-11T00:00:00.000Z",
         "birth_location":"67ae6bcf5ef34c6be30e9ef9",
         "sex":"M ou F",
         "breed":"A raça do animal",
         "register_date":"2025-02-13T22:09:03.936Z",
         "__v":0
      },
      "location":{
         "_id":"67ae6bcf5ef34c6be30e9ef9",
         "name":"O nome do local",
         "description":"Uma descrição do local",
         "latitude":-1.234567,
         "longitude":12.345678,
         "__v":0
      },
      "__v":0
   },
   {
      "_id":"67ac017527f4da090d87e3bc",
      "type_number":4,
      "description":"Exemplo de um registro, com um texto qualquer",
      "date":"2025-02-11T22:59:00.000Z",
      "animal":{
         "_id":"67ae6d7f5ef34c6be30e9efe",
         "name":"O nome do animal",
         "birth_date":"2025-02-11T00:00:00.000Z",
         "birth_location":"67ae6bcf5ef34c6be30e9ef9",
         "sex":"M ou F",
         "breed":"A raça do animal",
         "register_date":"2025-02-13T22:09:03.936Z",
         "__v":0
      },
      "location":{
         "_id":"67ae6bcf5ef34c6be30e9ef9",
         "name":"O nome do local",
         "description":"Uma descrição do local",
         "latitude":-1.234567,
         "longitude":12.345678,
         "__v":0
      },
      "__v":0
   }
]
```


