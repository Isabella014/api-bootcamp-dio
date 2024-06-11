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

-Response:
{
  "id": 1,
  "nome": "Nome do Atleta",
  "cpf": "12345678900",
  "centro_treinamento": "Centro de Treinamento X",
  "categoria": "Categoria Y"
}

Exceções:

303 See Other: Já existe um atleta cadastrado com o CPF fornecido.
Mensagem de erro: "Já existe um atleta cadastrado com o cpf: {cpf}"
Consultar Atletas
GET /atletas/
Consulta a lista de atletas, com suporte a filtros por nome e CPF, e paginação.

Query Parameters:

nome (opcional): Filtra atletas pelo nome.
cpf (opcional): Filtra atletas pelo CPF.
limit (opcional): Número máximo de atletas a serem retornados (padrão: 10).
offset (opcional): Deslocamento dos atletas a serem retornados (padrão: 0).
Response:

json
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
Instalação
Clone o repositório:

bash
git clone https://github.com/seu-usuario/sua-api.git
cd sua-api
Crie um ambiente virtual e ative-o:

bash
python -m venv env
source env/bin/activate  # No Windows use `env\Scripts\activate`
Instale as dependências:

bash
pip install -r requirements.txt
Execute a aplicação:

bash
uvicorn main:app --reload
Estrutura do Projeto
plaintext

.
├── main.py               # Arquivo principal da aplicação FastAPI
├── models.py             # Definições dos modelos SQLAlchemy
├── database.py           # Configuração do banco de dados
├── schemas.py            # Definições dos esquemas Pydantic
├── crud.py               # Funções CRUD para manipulação dos dados
└── requirements.txt      # Arquivo de dependências`

Dependências
fastapi: Framework web moderno e rápido para Python.
sqlalchemy: Biblioteca SQL toolkit e ORM.
fastapi-pagination: Biblioteca para paginação de resultados em FastAPI.
Exceções
A API manipula exceções de integridade dos dados:

IntegrityError: Quando um CPF duplicado é inserido, a API retorna um erro com a mensagem: "Já existe um atleta cadastrado com o cpf: {cpf}" e status code 303.
Paginação
A API utiliza a biblioteca fastapi-pagination para suportar paginação nos resultados do endpoint de consulta de atletas (GET /atletas/).
