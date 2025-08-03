
# Task API (ToDo List with Authentication)

Uma API RESTful desenvolvida com **FastAPI** para gestão pessoal de tarefas. Permite registro de usuários, login, criação e gerenciamento de tarefas com **autenticação baseada em JWT**. Ideal para aprender operações CRUD, autenticação e design de APIs.

## Features

* Registro e login de usuários (JWT)
* CRUD completo para tarefas (criar, listar, atualizar, excluir)
* Filtro de tarefas por status (pendente, concluída)
* Proteção de rotas com autenticação
* Integração com banco de dados SQLite ou PostgreSQL

## Technologies Used

* **Python 3.11+**
* **FastAPI**
* **Pydantic**
* **SQLite** (pode ser trocado por PostgreSQL)
* **Autenticação JWT (OAuth2)**
* **Uvicorn** (servidor ASGI)

## Authentication Endpoints

### 📌 POST `/auth/register`

**Descrição:** Registra um novo usuário.

**Payload:**

```json
{
  "username": "anabelmo",
  "email": "ana@email.com",
  "password": "123456"
}
```

**Resposta:**

```json
{
  "message": "User successfully registered"
}
```


### POST `/auth/login`

**Descrição:** Login do usuário e geração do token JWT.

**Payload:**

```json
{
  "email": "ana@email.com",
  "password": "123456"
}
```

**Resposta:**

```json
{
  "access_token": "<jwt_token_here>",
  "token_type": "bearer"
}
```

## Task Endpoints

> ⚠️ Todos os endpoints abaixo requerem autenticação JWT via cabeçalho:

```
Authorization: Bearer <access_token>
```


### POST `/tasks`

**Descrição:** Cria uma nova tarefa.

**Payload:**

```json
{
  "title": "Study FastAPI",
  "description": "Complete the lesson on authentication",
  "due_date": "2025-08-05T23:59:00",
  "status": "pending"
}
```

**Resposta:**

```json
{
  "id": 1,
  "title": "Study FastAPI",
  "description": "Complete the lesson on authentication",
  "due_date": "2025-08-05T23:59:00",
  "status": "pending",
  "owner_id": 1
}
```


### GET `/tasks`

**Descrição:** Lista todas as tarefas do usuário autenticado.

**Parâmetro opcional de consulta:**

```
/tasks?status=pending
```

**Resposta:**

```json
[
  {
    "id": 1,
    "title": "Study FastAPI",
    "description": "Complete the lesson on authentication",
    "due_date": "2025-08-05T23:59:00",
    "status": "pending"
  }
]
```


### GET `/tasks/{id}`

**Descrição:** Obtém detalhes de uma tarefa específica.

**Resposta:**

```json
{
  "id": 1,
  "title": "Study FastAPI",
  "description": "Complete the lesson on authentication",
  "due_date": "2025-08-05T23:59:00",
  "status": "pending"
}
```


### PUT `/tasks/{id}`

**Descrição:** Atualiza uma tarefa existente.

**Payload:**

```json
{
  "title": "Study FastAPI",
  "description": "Update the description",
  "due_date": "2025-08-06T12:00:00",
  "status": "done"
}
```

**Resposta:**

```json
{
  "message": "Task successfully updated"
}
```


### DELETE `/tasks/{id}`

**Descrição:** Exclui uma tarefa.

**Resposta:**

```json
{
  "message": "Task successfully deleted"
}
```

## O Que Você Vai Aprender com Este Projeto

* Como construir APIs RESTful com FastAPI
* Autenticação JWT com OAuth2 (Password Flow)
* Modelagem e validação de dados com Pydantic
* CRUD completo com rotas protegidas
* Filtros, parâmetros de query e gerenciamento de dados por usuário
* Uso prático de banco de dados (SQLite/PostgreSQL)

## ▶️ Como Rodar Localmente

1. **Clone o repositório:**

```bash
git clone https://github.com/yourusername/todo-api.git
cd todo-api
```

2. **Crie um ambiente virtual e instale as dependências:**

```bash
python -m venv venv
source venv/bin/activate  # ou venv\Scripts\activate no Windows
pip install -r requirements.txt
```

3. **Inicie o servidor:**

```bash
uvicorn main:app --reload
```

## 📄 Licença

Este projeto está licenciado sob a Licença MIT. Sinta-se à vontade para usar e modificar.

## Autor

Desenvolvido por **Anabelmo Feijó** — apaixonado por tecnologia, APIs e soluções práticas para os problemas do dia a dia.