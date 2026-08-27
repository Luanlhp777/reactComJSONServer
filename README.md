# React com JSON Server

Repositório desenvolvido durante as aulas de **Programação Web II** para praticar o consumo de APIs no React utilizando o **JSON Server** como backend simulado.

O projeto demonstra como desenvolver e testar o frontend de forma independente, mesmo quando um backend real ainda não está disponível.

---

## Objetivo

Compreender como uma aplicação React pode consumir dados de uma API REST utilizando:

* JSON Server
* Fetch API
* `async/await`
* `useState`
* `useEffect`
* Services
* Métodos HTTP
* CRUD

A aplicação utiliza um arquivo `db.json` como fonte de dados e o JSON Server transforma esse arquivo em uma API REST simulada.

---

## Tecnologias utilizadas

* React
* JavaScript
* Vite
* JSON Server
* Fetch API
* Node.js
* npm
* Git
* GitHub

---

## Estrutura do repositório

```text
reactComJSONServer/
└── ReactComJSONServerV1/
    ├── src/
    ├── db.json
    ├── index.html
    ├── package.json
    ├── package-lock.json
    ├── vite.config.js
    ├── .gitignore
    └── README.md
```

---

# JSON Server

O JSON Server permite transformar rapidamente um arquivo JSON em uma API REST para testes e desenvolvimento.

No projeto, os dados ficam armazenados em:

```text
db.json
```

Quando o servidor é iniciado, os dados podem ser acessados através de endpoints HTTP.

---

## Backend simulado

O JSON Server é iniciado com:

```bash
npm run server
```

Servidor:

```text
http://localhost:3001
```

Endpoint utilizado:

```text
http://localhost:3001/tarefas
```

---

# Aula 1 — Consumo de dados

Na primeira etapa, o foco foi aprender como o React busca informações de uma API.

Foram trabalhados:

* dados mockados;
* JSON Server;
* método `GET`;
* Fetch API;
* `async/await`;
* `useEffect`;
* `useState`;
* organização em service;
* renderização dos dados.

---

## GET

O método:

```text
GET /tarefas
```

é utilizado para buscar as tarefas disponíveis no JSON Server.

Fluxo:

```text
React
   ↓
tarefaService.js
   ↓
fetch()
   ↓
GET /tarefas
   ↓
JSON Server
   ↓
db.json
   ↓
Resposta JSON
   ↓
React
```

---

## Fetch API

A aplicação utiliza:

```javascript
fetch()
```

para realizar requisições HTTP.

A comunicação com a API é feita de forma assíncrona utilizando:

```javascript
async
await
```

---

## useState

O `useState()` é utilizado para armazenar informações dentro dos componentes React.

Exemplo conceitual:

```javascript
const [tarefas, setTarefas] = useState([]);
```

O estado é atualizado quando os dados chegam da API.

---

## useEffect

O `useEffect()` permite executar a busca das tarefas quando o componente é carregado.

Fluxo:

```text
Componente carregado
        ↓
useEffect()
        ↓
Service
        ↓
GET /tarefas
        ↓
JSON Server
        ↓
Estado atualizado
        ↓
Lista renderizada
```

---

# Service

A comunicação com a API é organizada em uma camada de serviço.

Exemplo:

```text
tarefaService.js
```

Essa organização evita colocar toda a lógica de acesso à API diretamente dentro dos componentes React.

Arquitetura:

```text
Componentes React
       ↓
Service
       ↓
API
```

---

# Aula 2 — CRUD

Na segunda etapa, o projeto evolui para trabalhar com as principais operações de uma API REST.

São utilizados:

```text
GET
POST
PATCH
DELETE
```

---

## Rotas

| Método   | Endpoint       | Operação               |
| -------- | -------------- | ---------------------- |
| `GET`    | `/tarefas`     | Listar tarefas         |
| `POST`   | `/tarefas`     | Criar tarefa           |
| `PATCH`  | `/tarefas/:id` | Atualizar parcialmente |
| `DELETE` | `/tarefas/:id` | Excluir tarefa         |

---

## CREATE — POST

Para cadastrar uma nova tarefa:

```text
POST /tarefas
```

O React envia os dados para o JSON Server, que registra o novo objeto no arquivo `db.json`.

---

## READ — GET

Para consultar as tarefas:

```text
GET /tarefas
```

O JSON Server retorna os dados em formato JSON.

---

## UPDATE — PATCH

Para atualizar parte de uma tarefa:

```text
PATCH /tarefas/:id
```

O `PATCH` permite modificar apenas os campos necessários sem substituir todo o objeto.

---

## DELETE

Para remover uma tarefa:

```text
DELETE /tarefas/:id
```

O registro correspondente é removido da base simulada.

---

## CRUD

As operações trabalhadas representam parte do conceito de CRUD:

```text
CREATE
   ↓
POST

READ
   ↓
GET

UPDATE
   ↓
PATCH

DELETE
   ↓
DELETE
```

---

# Independência entre frontend e backend

Um dos principais conceitos da aula é a separação entre a interface e a fonte de dados.

Durante o desenvolvimento:

```text
React
  ↓
Service
  ↓
JSON Server
```

Em um projeto real, posteriormente podemos substituir o JSON Server:

```text
React
  ↓
Service
  ↓
Backend real
  ↓
Banco de Dados
```

A ideia é manter os componentes React independentes da implementação interna do backend.

---

## Vantagem da camada Service

Utilizando uma camada intermediária:

```text
Componente
    ↓
Service
    ↓
API
```

a aplicação fica mais organizada.

Caso o backend seja alterado, grande parte da mudança pode ficar concentrada no service, sem necessidade de reconstruir toda a interface.

---

# Fluxo geral

```text
Usuário
   ↓
React
   ↓
Evento
   ↓
Service
   ↓
Fetch API
   ↓
JSON Server
   ↓
db.json
   ↓
Resposta JSON
   ↓
Atualização do estado
   ↓
Interface atualizada
```

---

## Como executar

Entre na pasta do projeto:

```bash
cd ReactComJSONServerV1
```

Instale as dependências:

```bash
npm install
```

---

### Iniciar JSON Server

Abra um terminal:

```bash
npm run server
```

A API ficará disponível em:

```text
http://localhost:3001
```

Para visualizar as tarefas:

```text
http://localhost:3001/tarefas
```

---

### Iniciar React

Abra outro terminal:

```bash
npm run dev
```

O Vite normalmente disponibiliza a aplicação em:

```text
http://localhost:5173
```

---

## Conceitos trabalhados

* React
* Vite
* JSON Server
* API REST
* Fetch API
* JSON
* dados mockados
* `useState`
* `useEffect`
* `async/await`
* Services
* métodos HTTP
* `GET`
* `POST`
* `PATCH`
* `DELETE`
* CRUD
* gerenciamento de estado
* renderização de listas
* integração frontend/API
* separação de responsabilidades

---

## Objetivos da aula

* Consumir uma API utilizando React
* Compreender o funcionamento do JSON Server
* Simular um backend durante o desenvolvimento
* Trabalhar com requisições HTTP
* Utilizar Fetch API
* Praticar programação assíncrona
* Trabalhar com `useState` e `useEffect`
* Organizar requisições em uma camada de service
* Implementar operações CRUD
* Compreender a independência entre frontend e backend

---

## Autor

**Luan Araujo**

Estudante de Desenvolvimento de Sistemas

GitHub: `Luanlhp777`

---

Projeto acadêmico desenvolvido para prática de **React, JSON Server, APIs REST e integração entre frontend e backend**.
