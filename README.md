# API de Atletas

Esta API permite a criação, consulta e paginação de atletas utilizando FastAPI, SQLAlchemy e FastAPI Pagination.

## Endpoints

### Criar Atleta

#### `POST /atletas/`

Cria um novo atleta.

- **Request Body**:
  ```json
  {
    "nome": "Nome do Atleta",
    "cpf": "12345678900",
    "centro_treinamento": "Centro de Treinamento X",
    "categoria": "Categoria Y"
  }

- **Response**:
  ```json
  {
  "id": 1,
  "nome": "Nome do Atleta",
  "cpf": "12345678900",
  "centro_treinamento": "Centro de Treinamento X",
  "categoria": "Categoria Y"
  }

 **Exceções:**
* 303 See Other: Já existe um atleta cadastrado com o CPF fornecido.
* Mensagem de erro: "Já existe um atleta cadastrado com o cpf: {cpf}"

### Consultar Atletas

`GET /atletas/`

Consulta a lista de atletas, com suporte a filtros por nome e CPF, e paginação.

- **Query Parameters:**

* nome (opcional): Filtra atletas pelo nome.
* cpf (opcional): Filtra atletas pelo CPF.
* limit (opcional): Número máximo de atletas a serem retornados (padrão: 10).
* offset (opcional): Deslocamento dos atletas a serem retornados (padrão: 0).

-**Response:**
  ```json
  {
  "items": [
    {
      "id": 1,
      "nome": "Nome do Atleta",
      "cpf": "12345678900",
      "centro_treinamento": "Centro de Treinamento X",
      "categoria": "Categoria Y"
    },
    ...
  ],
  "limit": 10,
  "offset": 0,
  "total": 100
  }
```

### Dependências
* fastapi: Framework web moderno e rápido para Python.
* sqlalchemy: Biblioteca SQL toolkit e ORM.
* fastapi-pagination: Biblioteca para paginação de resultados em FastAPI.
