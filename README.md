# Sistema de Cadastro de Livros

## Objetivo do Projeto
O sistema foi desenvolvido para gerenciar o catálogo de livros de uma biblioteca municipal, permitindo realizar operações CRUD completas usando uma arquitetura em **4 camadas**, garantindo separação de responsabilidades, organização e fácil manutenção.

---

## Arquitetura do Projeto (4 camadas)

A aplicação segue uma arquitetura com **separação total de responsabilidades**:

### **1. Interface (API)**

### **2. Aplicação (Service)**


### **3. Domínio (Model + Repository)**


### **4. Infraestrutura (JPA/Database)**

---

##  Stack Tecnológica

- **Java 17+**
- **Spring Boot 3.2+**
- **Spring Data JPA**
- **H2 Database** (banco em memória)
- **JUnit 5**
- **Mockito**
- **Maven**
- IDE recomendada: **IntelliJ IDEA**

---

##  Requisitos Funcionais

### **RF01 – Cadastrar Livro**
- Permitir cadastrar um novo livro.
- Campos obrigatórios: título, autor, ISBN, ano de publicação, quantidade em estoque.
- ISBN deve ser **único**.

---

### **RF02 – Listar Livros**
- Listar todos os livros cadastrados.
- Buscar livro por **ID**.
- Buscar livro por **ISBN**.

---

### **RF03 – Atualizar Livro**
- Permitir atualizar dados de um livro existente.
- Não permitir modificar ISBN para um que já exista no sistema.

---

### **RF04 – Remover Livro**
- Permitir remover um livro do catálogo.
- Validar se o livro existe antes de remover.

---

##  Fluxo de Funcionamento da Aplicação

1. O cliente (Postman) envia uma requisição para o **Controller**.
2. O Controller encaminha os dados para o **Service**.
3. O Service aplica validações e regras de negócio.
4. O Service usa o **Repository (Domínio)**, sem conhecer JPA.
5. O Repository chama a **implementação real (Infraestrutura)**.
6. A Infraestrutura converte:
    - **Domain → Entity** (para salvar no banco)
    - **Entity → Domain** (para retornar ao Service)
7. O JPA executa a operação no banco H2.
8. A resposta volta ao Controller e ao usuário.

---

## Como Executar o Projeto

### **1. Pelo IntelliJ / Maven**
Abra o painel Maven lateral e execute:

cadastralivro -> Lifecycle -> clean -> install


Depois rode a classe:

**CadastraLivroApplication.java**


### **2. Testar os Endpoints**
Use **Postman**, **Insomnia** ou outra ferramenta.

---

##  Endpoints da API

### **GET /livros**
![img_1.png](assets/img_1.png)
Lista todos os livros.

### **GET /livros/{id}**
![img_3.png](assets/img_3.png)
Busca um livro por ID.

### **GET /livros/isbn/{isbn}**
![img_2.png](assets/img_2.png)
Busca um livro pelo ISBN.

### **POST /livros**
![img.png](assets/img.png)
Cadastra um novo livro.

Exemplo JSON:
```json
{
  "isbn": "123456",
  "titulo": "A Hora da Estrela",
  "autor": "Clarice Lispector",
  "anoPublicacao": "2020",
  "quantidadeEstoque": 100
}
```

### **PUT /livros/{id}**
![img_4.png](assets/img_4.png)

Atualiza os dados de um livro existente.

### **DELETE /livros/{id}**
![img_5.png](assets/img_5.png)

Remove um livro do catálogo.

## Para acessar o banco

Abra o navegador e digite
 **http://localhost:8081/h2
**

Use as credenciais

```
JDBC URL: jdbc:h2:mem:livro
User: municipal
Password: municipal

```

![img_6.png](assets/img_6.png)