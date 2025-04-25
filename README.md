# Descrição
Este projeto tem como objetivo implementar uma aplicação simples utilizando o Spring Boot com MariaDB, aplicando conceitos de persistência de dados, mapeamento de entidades e operações CRUD (Create, Read, Update, Delete) por meio de APIs REST. A aplicação gerencia duas entidades principais: Produto e Categoria, demonstrando como estruturar relacionamentos entre elas e realizar a persistência dos dados no banco MariaDB.

# Tecnologias Utilizadas
Spring Boot: Framework Java para criação de aplicações robustas e de fácil manutenção.

Spring Web: Para criação de APIs RESTful.

Spring Data JPA: Facilita a interação com o banco de dados através de JPA (Java Persistence API).

Lombok: Biblioteca para reduzir a verbosidade do código, gerando automaticamente métodos como getters, setters, construtores e toString.

Spring DevTools: Para facilitar o desenvolvimento com recarregamento automático durante as modificações no código.

MariaDB: Banco de dados relacional utilizado para armazenar as informações.

# Entidades
Categoria:

id (Long): Identificador único da categoria.

nome (String): Nome da categoria.

descricao (String): Descrição detalhada da categoria.

Relacionamento: Uma categoria pode conter vários produtos, implementado como um relacionamento One-to-Many com a entidade Produto.

Produto:

id (Long): Identificador único do produto.

nome (String): Nome do produto.

quantidade (Integer): Quantidade disponível em estoque.

descricao (String): Descrição do produto.

Relacionamento: Cada produto pertence a uma única categoria, implementado como um relacionamento Many-to-One com a entidade Categoria.

# Relacionamento entre as Entidades
Uma Categoria pode ter vários Produtos.

Cada Produto está associado a uma única Categoria.

O relacionamento entre as entidades é mapeado com as anotações @OneToMany (para a categoria) e @ManyToOne (para o produto), utilizando o JPA.

# Configuração do Banco de Dados
A aplicação utiliza o MariaDB como banco de dados relacional, sendo que o XAMPP é utilizado para gerenciar o servidor MySQL/MariaDB localmente.

# Passos para Configuração
Baixe o XAMPP: Clique aqui para baixar.

Inicie o MariaDB no painel do XAMPP.

Criação do Banco de Dados:

Acesse o phpMyAdmin ou use a linha de comando para criar o banco de dados (ex: projeto_db).

Configuração do arquivo application.yaml: No arquivo src/main/resources/application.yaml, adicione as configurações para conectar sua aplicação ao banco MariaDB:

yaml
Copiar
Editar
spring:
  datasource:
    url: jdbc:mariadb://localhost:3306/provaweb
    username: root
    password: 
    driver-class-name: org.mariadb.jdbc.Driver

  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    database-platform: org.hibernate.dialect.MariaDBDialect
#Endpoints Principais
🔸 Categoria
GET /api/categorias: Retorna todas as categorias cadastradas.

POST /api/categorias: Cria uma nova categoria.

🔸 Produto
GET /api/produtos: Retorna todos os produtos cadastrados.

POST /api/produtos: Cria um novo produto, associando-o a uma categoria existente.

Utilize ferramentas como Postman ou Insomnia para testar as rotas e realizar as requisições.

#Requisitos Atendidos

CRUD completo para as entidades Categoria e Produto.

Relacionamento funcional entre as entidades Categoria e Produto, sendo persistido no banco de dados MariaDB.

Uso do Lombok para simplificação do código e redução de boilerplate.

Endpoints REST implementados e testados para todas as operações de CRUD.

# Conclusão
Este projeto exemplifica como construir uma aplicação Spring Boot conectada a um banco MariaDB para persistir dados. Ele cobre conceitos importantes como JPA, relacionamentos entre entidades, e a criação de APIs RESTful. A estrutura do projeto pode ser facilmente expandida para incluir novas funcionalidades, autenticação de usuários, ou até mesmo novas entidades e relacionamentos complexos.
