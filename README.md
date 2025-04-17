# teste-de-desenvolvimento


# Gerenciador de Tarefas - CodeIgniter 4

Este é um sistema simples de gerenciamento de tarefas desenvolvido com **CodeIgniter 4**, que oferece:

- Uma **interface web** para criar, listar, editar e excluir tarefas
- Uma **API RESTful** para integração com front-ends ou apps

---

## Tecnologias Utilizadas

- PHP 8+
- CodeIgniter 4
- MySQL
- Composer
- Bootstrap 5 
- RESTful API (JSON)

---

## Requisitos

- PHP 7.4 ou superior
- Composer
- MySQL/MariaDB
- Navegador
- (Opcional) XAMPP

---

##  Instalação

1. Clone ou extraia o projeto:

```bash
git  https://github.com/rafaelvsantos03/teste-de-desenvolvimento.git

```

Ou extraia o `.zip` e abra no terminal.

2. Instale as dependências:

```bash
composer install
```

3. Copie o arquivo `.env` e configure:

```bash
cp env .env
```

4. Configure o banco de dados no `.env`:

```dotenv
CI_ENVIRONMENT = development

database.default.hostname = localhost
database.default.database = tarefas
database.default.username = root
database.default.password =
database.default.DBDriver = MySQLi
```

5. Crie o banco e a tabela:

```sql
CREATE TABLE tasks (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    status ENUM('pendente', 'em andamento', 'concluída') DEFAULT 'pendente',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

6. Inicie o servidor local:

```bash
php spark serve
```

Acesse:  
```
http://localhost:8080
```

---

## Interface Web

- Página inicial: lista de tarefas
- Botão de criação
- Botão de edição
- Botão de exclusão

---

##  API RESTful

| Método | Endpoint            | Ação                 |
|--------|---------------------|----------------------|
| GET    | `/api/tasks`        | Listar todas         |
| GET    | `/api/tasks/{id}`   | Buscar tarefa        |
| POST   | `/api/tasks`        | Criar nova tarefa    |
| PUT    | `/api/tasks/{id}`   | Atualizar tarefa     |
| DELETE | `/api/tasks/{id}`   | Deletar tarefa       |

### JSON exemplo:

```json
{
  "title": "Estudar CodeIgniter",
  "description": "Aprender a criar APIs",
  "status": "em andamento"
}
```

---

## Validações

- Título: obrigatório, mínimo 3 caracteres
- Status: obrigatório, deve ser um dos: `pendente`, `em andamento`, `concluída`


