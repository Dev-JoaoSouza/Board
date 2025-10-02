# 📝 Task Board - Console App (Java + MySQL)

## 📌 Sobre o projeto

Este projeto é um **gerenciador de boards de tarefas** em **Java**, executado via console.
Ele permite criar, listar, selecionar e excluir boards, além de organizar tarefas em colunas personalizadas (como *Inicial*, *Pendente*, *Final* e *Cancelada*).

O sistema utiliza **MySQL** para persistência dos dados e o **Gradle** para gerenciamento do build.

## 🚀 Funcionalidades

* Criar novos boards com colunas padrão e adicionais.
* Selecionar boards existentes pelo **ID**.
* Excluir boards do banco de dados.
* Navegação simples via **menu no console**.
* Persistência das informações no **MySQL**.

## 🛠️ Tecnologias utilizadas

* **Java 17+**
* **Gradle** (build e dependências)
* **MySQL** (persistência de dados)
* **JDBC** (conexão com o banco)

## 📂 Estrutura do projeto

```
📦 task-board
 ┣ 📂 src
 ┃ ┣ 📂 main
 ┃ ┃ ┣ 📂 java
 ┃ ┃ ┃ ┗ 📂 br.com.dio.persistence
 ┃ ┃ ┃ ┃ ┣ 📂 config
 ┃ ┃ ┃ ┃ ┃ ┗ 📜 ConnectionConfig.java
 ┃ ┃ ┃ ┃ ┣ 📂 entity
 ┃ ┃ ┃ ┃ ┃ ┣ 📜 BoardEntity.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜 BoardColumnEntity.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜 BoardColumnKindEnum.java
 ┃ ┃ ┃ ┃ ┣ 📂 service
 ┃ ┃ ┃ ┃ ┃ ┣ 📜 BoardService.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜 BoardQueryService.java
 ┃ ┃ ┃ ┃ ┗ 📜 MainMenu.java
 ┃ ┗ 📂 resources
 ┃ ┃ ┗ 📜 application.properties
 ┣ 📜 build.gradle
 ┣ 📜 settings.gradle
 ┗ 📜 README.md
```

## ⚙️ Configuração do Banco de Dados

Antes de rodar o projeto, é necessário configurar o **MySQL**:

1. Criar um banco de dados:

   ```sql
   CREATE DATABASE taskboard;
   ```
2. Criar as tabelas necessárias (exemplo simplificado):

   ```sql
   CREATE TABLE board (
       id BIGINT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255) NOT NULL
   );

   CREATE TABLE board_column (
       id BIGINT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255) NOT NULL,
       kind VARCHAR(50) NOT NULL,
       `order` INT NOT NULL,
       board_id BIGINT,
       FOREIGN KEY (board_id) REFERENCES board(id)
   );
   ```
3. Configurar as credenciais em `application.properties`:

   ```properties
   db.url=jdbc:mysql://localhost:3306/taskboard
   db.user=root
   db.password=senha
   ```

## ▶️ Como executar

1. Clone o repositório:

   ```bash
   git clone https://github.com/seu-usuario/task-board-java.git
   cd task-board-java
   ```
2. Compile e rode o projeto:

   ```bash
   ./gradlew build
   ./gradlew run
   ```
3. O menu será exibido no console:

   ```
   Bem vindo ao gerenciador de boards, escolha a opção desejada
   1 - Criar um novo board
   2 - Selecionar um board existente
   3 - Excluir um board
   4 - Sair
   ```

## ✅ Próximos passos

* Implementar gerenciamento de **tarefas dentro dos boards**.
* Adicionar testes automatizados.
* Criar interface gráfica (JavaFX ou Swing).