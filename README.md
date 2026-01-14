# Banco de Dados de Filmes com Neo4j

Este projeto consiste na criação de um banco de dados de filmes utilizando o **banco de dados orientado a grafos Neo4j**.
O objetivo é modelar relações entre **usuários, filmes, atores, diretores e gêneros**, permitindo análises como:

* Quem assistiu cada filme
* Avaliações dadas pelos usuários
* Quais atores atuaram em cada filme
* Quem dirigiu cada obra
* Classificação por gênero

## 🧠 Tecnologias Utilizadas

* **Neo4j**
* **Linguagem Cypher**


## 📂 Estrutura do Grafo

O banco utiliza os seguintes tipos de nós:

* `Usuario`
* `Filme`
* `Gênero`
* `Ator`
* `Diretor`

E relações como:

* `WATCHED` – Usuário assistiu um filme e deu nota
* `ACTED_IN` – Ator participou de um filme
* `DIRECTED` – Diretor dirigiu o filme
* `IN_GENRE` – Filme pertence a um gênero


## 🗄 Inserção dos Dados

O script cria automaticamente todos os nós e relacionamentos usando instruções `MERGE`.

### Exemplos de nós criados

```cypher
MERGE (:Usuario {id: 1, nome: 'Evilly'});
MERGE (:Filme {id: 101, titulo: 'Cisne Negro'});
MERGE (:Genero {id: 201, nome: 'Drama/Fantasia'});
MERGE (:Ator {id: 301, nome: 'Natalie Portman'});
MERGE (:Diretor {id: 401, nome: 'Darren Aronofsky'});
```

### Exemplo de relacionamento

```cypher
MATCH (u:Usuario {id: 1}), (f:Filme {id: 101}) 
MERGE (u)-[:WATCHED {rating: 9.0}]->(f);
```


## 📊 Possíveis Consultas

Após a execução deste projeto, é possível rodar consultas como:

### 🎥 Filmes assistidos por um usuário

```cypher
MATCH (u:Usuario {nome: "Evilly"})-[r:WATCHED]->(f:Filme)
RETURN f.titulo, r.rating;
```

### ⭐ Atores de um filme

```cypher
MATCH (f:Filme {titulo: "Cisne Negro"})<-[:ACTED_IN]-(a:Ator)
RETURN a.nome;
```

### 🎬 Filmes de um diretor

```cypher
MATCH (d:Diretor {nome: "James Cameron"})-[:DIRECTED]->(f)
RETURN f.titulo;
```


## 🚀 Como Executar

1. Instale e abra o **Neo4j Desktop**, ou use Neo4j Aura.
2. Crie um novo banco de dados.
3. Abra o **Neo4j Browser**.
4. Cole todo o conteúdo do script Cypher.
5. Execute e visualize o grafo.


## 📌 Objetivo do Projeto

Este banco foi criado como parte de um estudo prático de **modelagem de grafo em Neo4j**, ideal para:

* Experimentar consultas Cypher
* Aprender relacionamentos complexos
* Visualizar conexões no estilo redes sociais e conteúdo


##  Autora

**Evilly Rolim**
