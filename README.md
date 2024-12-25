# Backend de Autenticação

Este repositório contém o backend de autenticação para a aplicação de login. Ele fornece a infraestrutura necessária para autenticação de usuários utilizando JWT (JSON Web Tokens).

## Tecnologias Utilizadas

- **Java**: Linguagem principal utilizada no backend.
- **Spring Boot**: Framework para construção de APIs RESTful.
- **JWT**: Utilizado para autenticação e autorização.
- **MySQL**: Banco de dados relacional para armazenamento de informações de usuários.

## Funcionalidades

- Cadastro de novos usuários
- Login com validação de credenciais
- Geração e validação de tokens JWT
- Gerenciamento de sessão com segurança (stateless)

## Configuração

### Pré-requisitos

- Java 17 ou superior
- Maven
- MySQL

### Passos para Configuração

1. Clone este repositório:

   ```bash
   git clone https://github.com/TN-Junior/login-app-backend.git
   ```

2. Configure o arquivo `application.properties` com as credenciais do seu banco de dados:

   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/seu_banco
   spring.datasource.username=seu_usuario
   spring.datasource.password=sua_senha
   
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   jwt.secret=seu-segredo-jwt
   jwt.expiration=3600000
   ```

3. Execute a aplicação:

   ```bash
   mvn spring-boot:run
   ```

A aplicação estará disponível em `http://localhost:8080`.

## Integração com o Frontend

O frontend correspondente para este backend está disponível no seguinte repositório:

[Login Page - Frontend](https://github.com/TN-Junior/login-page.git)

## Endpoints

### **Autenticação**

- **POST** `/auth/login`: Realiza o login do usuário e retorna um token JWT.
  - Corpo da requisição:
    ```json
    {
      "username": "seu_usuario",
      "password": "sua_senha"
    }
    ```
  - Resposta:
    ```json
    {
      "token": "jwt-gerado"
    }
    ```

- **POST** `/auth/register`: Registra um novo usuário.
  - Corpo da requisição:
    ```json
    {
      "username": "seu_usuario",
      "password": "sua_senha"
    }
    ```

### **Usuários**

- **GET** `/users/me`: Retorna os dados do usuário autenticado.
  - Requer cabeçalho com token JWT:
    ```
    Authorization: Bearer jwt-gerado
    ```


