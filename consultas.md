### Resolução do Desafio de Banco de Dados - DIO

Este documento apresenta as 12 consultas SQL solicitadas no desafio de banco de dados da trilha .NET da DIO. As consultas foram elaboradas com base no modelo de banco de dados fornecido, que inclui tabelas para `Filmes`, `Atores`, `Generos`, `ElencoFilme` e `FilmesGenero`.

Para a realização do desafio, foi utilizado o script `Script Filmes.sql`, que cria o banco de dados e popula as tabelas com os dados necessários.

Abaixo estão as consultas, uma para cada objetivo, seguindo a ordem e os requisitos propostos.

-----

### Consultas SQL

#### 1\. Buscar o nome e ano dos filmes

```sql
SELECT
  Nome,
  Ano
FROM Filmes;
```

#### 2\. Buscar o nome e ano dos filmes, ordenados por ordem crescente pelo ano

```sql
SELECT
  Nome,
  Ano
FROM Filmes
ORDER BY
  Ano;
```

#### 3\. Buscar pelo filme de volta para o futuro, trazendo o nome, ano e a duração

```sql
SELECT
  Nome,
  Ano,
  Duracao
FROM Filmes
WHERE
  Nome = 'De Volta para o Futuro';
```

#### 4\. Buscar os filmes lançados em 1997

```sql
SELECT
  Nome,
  Ano
FROM Filmes
WHERE
  Ano = 1997;
```

#### 5\. Buscar os filmes lançados APÓS o ano 2000

```sql
SELECT
  Nome,
  Ano
FROM Filmes
WHERE
  Ano > 2000;
```

#### 6\. Buscar os filmes com a duracao maior que 100 e menor que 150, ordenando pela duracao em ordem crescente

```sql
SELECT
  Nome,
  Duracao
FROM Filmes
WHERE
  Duracao > 100 AND Duracao < 150
ORDER BY
  Duracao;
```

#### 7\. Buscar a quantidade de filmes lançadas no ano, agrupando por ano, ordenando pela duracao em ordem decrescente

```sql
SELECT
  Ano,
  COUNT(Id) AS Quantidade
FROM Filmes
GROUP BY
  Ano
ORDER BY
  Ano DESC;
```

#### 8\. Buscar os Atores do gênero masculino, retornando o PrimeiroNome, UltimoNome

```sql
SELECT
  PrimeiroNome,
  UltimoNome
FROM Atores
WHERE
  Genero = 'M';
```

#### 9\. Buscar os Atores do gênero feminino, retornando o PrimeiroNome, UltimoNome, e ordenando pelo PrimeiroNome

```sql
SELECT
  PrimeiroNome,
  UltimoNome
FROM Atores
WHERE
  Genero = 'F'
ORDER BY
  PrimeiroNome;
```

#### 10\. Buscar o nome do filme e o gênero

```sql
SELECT
  f.Nome,
  g.Genero
FROM FilmesGenero AS fg
INNER JOIN Filmes AS f
  ON fg.IdFilme = f.Id
INNER JOIN Generos AS g
  ON fg.IdGenero = g.Id;
```

#### 11\. Buscar o nome do filme e o gênero do tipo "Mistério"

```sql
SELECT
  f.Nome,
  g.Genero
FROM FilmesGenero AS fg
INNER JOIN Filmes AS f
  ON fg.IdFilme = f.Id
INNER JOIN Generos AS g
  ON fg.IdGenero = g.Id
WHERE
  g.Genero = 'Mistério';
```

#### 12\. Buscar o nome do filme e os atores, trazendo o PrimeiroNome, UltimoNome e seu Papel

```sql
SELECT
  f.Nome,
  a.PrimeiroNome,
  a.UltimoNome,
  ef.Papel
FROM ElencoFilme AS ef
INNER JOIN Filmes AS f
  ON ef.IdFilme = f.Id
INNER JOIN Atores AS a
  ON ef.IdAtor = a.Id;
```