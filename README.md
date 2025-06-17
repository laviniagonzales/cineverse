# 🎥 Cineverse - Microserviço de Filmes com Spring Boot

O **Cineverse** é um microserviço desenvolvido em Java com Spring Boot que simula uma versão simplificada do IMDB. Permite realizar operações de CRUD (Create, Read, Update, Delete) sobre uma entidade `Filme`, além de realizar buscas por nome do diretor.

---

🎯 Propósito do Microserviço:

O Cineverse tem como objetivo proporcionar uma API RESTful simples, organizada e funcional para gerenciamento de filmes, com validações de entrada, estrutura MVC, e documentação completa. Ele pode ser utilizado para:
Registrar filmes assistidos
Criar um catálogo pessoal ou público
Filtrar filmes por diretor
Editar ou excluir registros
Exemplo de uso com cURL para cadastrar um filme:

curl -X POST http://localhost:8080/filmes \
-H "Content-Type: application/json" \
-d '{
  "titulo": "Matrix",
  "ano": 1999,
  "diretor": "Wachowski",
  "genero": "Ficção Científica",
  "avaliacao": 9.5
}'




## 🔎 Funcionalidades da API - ROTAS

| Ação                   | Verbo  | Endpoint                  | Descrição                                                                   |
| ---------------------- | ------ | --------------------------| --------------------------------------------------------------------------- |
| Listar todos os filmes | GET    | /filmes                   | Retorna a lista completa de filmes cadastrados.                             |
| Buscar por ID          | GET    | /filmes/{id}              | Retorna os dados de um filme específico.                                    |
| Criar novo filme       | POST   | /filmes                   | Cadastra um novo filme no sistema.                                          |
| Atualizar filme        | PUT    | /filmes/{id}              | Altera as informações de um filme existente.                                |
| Remover filme          | DELETE | /filmes/{id}              | Exclui um filme do banco.                                                   |
| Buscar por diretor     | GET    | /filmes/por-diretor?nome= | Lista filmes com o nome do diretor (busca ignorando maiúsculas/minúsculas). |

---

## Tecnologias utilizadas 

| Tecnologia              | Finalidade                                                        |
| ----------------------- | ----------------------------------------------------------------- |
| **Java 17**             | Linguagem principal do projeto                                    |
| **Spring Boot 3.2.5**   | Framework principal para criação do microserviço REST             |
| **Spring Web**          | Responsável por criar os endpoints HTTP                           |
| **Spring Data JPA**     | Abstração para interação com banco de dados relacional            |
| **H2 Database**         | Banco de dados em memória, usado para testes                      |
| **Spring Validation**   | Validação automática dos dados recebidos na API (`@Valid`)        |
| **Swagger (Springdoc)** | Geração automática da documentação da API com interface de testes |
| **Maven**               | Gerenciador de dependências e build tool                          |


## 🎓 Conceitos de POO aplicados

- **Encapsulamento**: uso de `private` nos atributos e `getters/setters`
- **Abstração**: lógica de negócio separada em `FilmeService`
- **Herança**: `FilmeRepository` herda de `JpaRepository`
- **Polimorfismo**: `save()` do repositório aceita várias formas da entidade
- **Injeção de dependência**: Spring gerencia os componentes

---

## 📄 Entidade Filme

java
public class Filme {
    private Long id;
    private String titulo;
    private int ano;
    private String diretor;
    private String genero;
    private double avaliacao;
}


## 🔧 Como Executar

✅ Pré-requisitos

-Java 17 instalado
-Maven instalado ou usar o wrapper ./mvnw

▶️ Passos para rodar o projeto

Clone o projeto:
-git clone https://github.com/laviniagonzales/cineverse.git
Navegue até a pasta do projeto:
cd cineverse
Execute com Maven:
./mvnw spring-boot:run

⚙️ Configuração do Banco de Dados (H2)

A configuração atual utiliza H2 Database (em memória):

# src/main/resources/application.properties
spring.datasource.url=jdbc:h2:mem:cineverse
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
spring.jpa.hibernate.ddl-auto=update

Acesse o console H2 em:
http://localhost:8080/h2-console


---

## 👥 Divisão de Tarefas

### 👤 **Lavinia Gonzales**
- Definiu a entidade `Filme` e o propósito do microserviço.
- Criou o spring boot, vinculou no Github e no VSCODE
- Modelou a classe `Filme.java` com validações (`@NotBlank`, `@Min`, `@DecimalMax`, etc).
- Estruturou os pacotes do projeto (`model`, `service`, `controller`, `repository`).
- Criou e documentou o `README.md` com todas as instruções detalhadas e descrição do projeto.

---

### 👤 **Samuel Fonseca**
- Implementou a classe `FilmeController` com todos os endpoints REST:
  - `POST /filmes`
  - `GET /filmes`
  - `GET /filmes/{id}`
  - `PUT /filmes/{id}`
  - `DELETE /filmes/{id}`
  - `GET /filmes/por-diretor`
- Utilizou corretamente as anotações REST do Spring: `@RestController`, `@RequestMapping`, `@PathVariable`, `@RequestBody`, `@Valid`.
- Configurou e testou a documentação Swagger (OpenAPI).
- Realizou os testes nos endpoints através da interface gráfica do Swagger.
---

### 👤 **Nicolas Mendes**
- Criou o repositório `FilmeRepository`, estendendo `JpaRepository`.
- Implementou método customizado `findByDiretorContainingIgnoreCase`.
- Desenvolveu a camada `FilmeService` com as operações de:
  - criação, leitura, atualização, exclusão e busca por diretor.
---

### 👤 **Gabriel Soares**
- Configurou o projeto Maven com as dependências corretas no `pom.xml`:
  - Spring Boot, Spring Web, Spring Data JPA, H2, Validation e Swagger.
- Configurou o banco H2 para ambiente local de testes.
- Aplicou princípios de abstração e injeção de dependência.

---


