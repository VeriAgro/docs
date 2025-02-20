# API
A fim de facilitar a implementação com serviços externos, a VeriAgro fornece uma API. A seguir são os endpoints da API.

## Dados gerais

Versão atual: v0.2.0

Linguagem de programação do backend atual: Typescript

URL base da API: https://api.veriagro.com.br/

> [!NOTE]\
> A API ainda está em no começo do desenvolvimento. Dados gerais sujeitos a mudança.

> [!WARNING]\
> Exceto pelos campos 'descrição', todos os campos devem ter até no máximo 32 caracteres.

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
    "description": "A descrição do local",
    "latitude": "40.7128",
    "longitude": "-74.0060"
  }
```
###### Resposta:
```json
{
   "id":"0xa284a5f8a329e42a271A55a7A1F0142170F821Ea",
   "name": "O nome do local",
    "description": "A descrição do local",
    "latitude": "40.7128",
    "longitude": "-74.0060"
}
```
#### POST /animal
---
É o endpoint de criação / cadastro de animal. O sexo é um booleano, sendo true para macho e false para fêmea.
###### Exemplo:
```json
{
    "name": "Nome do animal",
    "sex": true,
    "breed": "Raça do animal"
  }
```
###### Resposta:
```json
{
    "id": "0xc28BD2ecDdBD727CEED0764d0Cda1629C10Adc10",
    "name": "Nome do animal",
    "sex": true,
    "breed": "Raça do animal"
}
```
#### POST /event
---
É o endpoint de criação / cadastro de evento.

O tipo é um número de 0-4, sendo:

NASCIMENTO = 0,
VACINACAO = 1,
MOVIMENTO = 2,
ABATE = 3,
REGISTRO = 4

> [!WARNING]\
> Na versão v0.2.1, o id também será retornado

###### Exemplo:
```json
{
    "typeNumber": 1,
    "description": "Descrição do evento, como a vacinação",
    "date": 1739931426,
    "animalId": "0xc28BD2ecDdBD727CEED0764d0Cda1629C10Adc10",
    "locationId": "0xa284a5f8a329e42a271A55a7A1F0142170F821Ea",
    "weight": 100
}
```
###### Resposta:
```json
{
    "typeNumber": 1,
    "description": "Descrição do evento, como a vacinação",
    "date": 1739931426,
    "animalId": "0xc28BD2ecDdBD727CEED0764d0Cda1629C10Adc10",
    "locationId": "0xa284a5f8a329e42a271A55a7A1F0142170F821Ea",
    "weight": 100
}
```
## Leitura
#### GET /location/{id}
---
###### Resposta:
```json
{
    "name": "O nome do local",
    "description": "A descrição do local",
    "latitude": "40.7128",
    "longitude": "-74.0060"
}
```
#### GET /animal/{id}
---
###### Resposta:
```json
{
    "name": "Nome do animal",
    "sex": true,
    "breed": "Raça do animal"
}
```
#### GET /event/{id}
---
###### Resposta:
> [!WARNING]\
> Estará disponível na versão v0.2.1

#### GET /events/animal{id}
---
Retorna todos os eventos cadastrados a um animal
###### Resposta:
```json
[
  {
    "eventType": "1",
    "description": "Descrição do evento, como a vacinação",
    "date": 1739931426,
    "weight": 100,
    "location": {
        "name": "O nome do local",
        "description": "A descrição do local",
        "latitude": "40.7128",
        "longitude": "-74.0060"
    }
  }
]
```
