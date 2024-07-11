# Praticando SQL Curso Proz...

Lembre-se, cada desafio é uma chance de crescer. Não se desanime com os erros; eles são degraus no caminho do aprendizado. E acima de tudo, divirta-se! 
O aprendizado mais eficaz acontece quando nos engajamos e nos interessamos pelo que estamos fazendo.

#### Tabela Não Normalizada (Exemplo)
```
Suponha que temos a seguinte tabela Estudante com um atributo multivalorado Telefones:

<img src="https://github.com/DanniNascimento/normalizacao-de-dados/issues/1#issue-2402122295.png"/>
```

#### Tabela em Primeira Forma Normal (1FN)
```
Para transformar essa tabela em 1FN, precisamos eliminar os atributos multivalorados e criar linhas distintas para cada valor do atributo multivalorado.
Tabela Estudante:

<img src="https://github.com/DanniNascimento/normalizacao-de-dados/issues/2#issuecomment-2221909548.png"/>
```

#### Tabela Telefones:
```
<img src="https://github.com/DanniNascimento/normalizacao-de-dados/issues/3#issue-2402136229.png"/>
```

SQL para criar as tabelas em 1FN:

```sql
-- Criar a tabela Estudante
CREATE TABLE Estudante (
    ID INT PRIMARY KEY AUTO_INCREMENT,
    NomeCompleto VARCHAR(100),
    DataNascimento DATE
);

-- Criar a tabela Telefones
CREATE TABLE Telefones (
    ID INT PRIMARY KEY AUTO_INCREMENT,
    EstudanteID INT,
    Telefone VARCHAR(15),
    FOREIGN KEY (EstudanteID) REFERENCES Estudante(ID)
);
```
Descrição das Tabelas Normalizadas
Tabela Estudante:

ID: Chave primária para identificar cada estudante.
NomeCompleto: Nome completo do estudante.
DataNascimento: Data de nascimento do estudante.
Tabela Telefones:

ID: Chave primária para identificar cada número de telefone.
EstudanteID: Chave estrangeira que referencia o ID da tabela Estudante.
Telefone: Número de telefone do estudante.
Ao normalizar a tabela para a Primeira Forma Normal (1FN), garantimos que cada coluna contém apenas valores atômicos e que não há repetição de grupos de valores em uma única célula. Isso ajuda a evitar redundância e anomalias de atualização.

