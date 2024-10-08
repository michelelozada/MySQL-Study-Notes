> **Atualizando valores em tabelas (comando UPDATE)**     
> Repositório: Banco de Dados SQL - Fundamentos    
> GitHub: @michelelozada
&nbsp;
     
&nbsp;  
## Comando UPDATE
```
- Atualiza/altera dados pré-cadastrados em uma tabela do banco de dados

- Deve ser utilizado juntamente com a cláusula `SET`, que tem a função de determinar qual o campo será atualizado
```
  
&nbsp;

↳ A tabela a ser utilizada para os exemplos abaixo:
```
+---------+-------------------+----------------+-------------+
| idAluno |     nomeAluno     |  cidadeAluno   | estadoAluno |
+---------+-------------------+----------------+-------------+
|       1 | Luana Borba       | Curitiba       | PR          |
|       2 | Mariana Fernandes | Rio de Janeiro | RJ          |
|       3 | Cátia Marcondes   | Santo André    | SP          |
|       4 | Marcos Góes       | Florianópolis  | SC          |
+---------+-------------------+----------------+-------------+

```
&nbsp;

## Atualizando um registro da tabela:
O comando `UPDATE` deve ser utilizado juntamente com a cláusula `WHERE`, quando for necessária a especificação de qual registro terá seus dados atualizados

```mysql

UPDATE tb_aluno -- nome da tabela
SET nomeAluno = 'Marcos Góes Filho'  -- nome da coluna e valor a ser atualizado
WHERE idAluno = 4;  -- foi retificado o nome deste aluno  -- condição para atualização
```

↳ Saída gerada: 
```
+---------+-------------------+----------------+-------------+
| idAluno |     nomeAluno     |  cidadeAluno   | estadoAluno |
+---------+-------------------+----------------+-------------+
|       1 | Luana Borba       | Curitiba       | PR          |
|       2 | Mariana Fernandes | Rio de Janeiro | RJ          |
|       3 | Cátia Marcondes   | Santo André    | SP          |
|       4 | Marcos Góes Filho | Florianópolis  | SC          |
+---------+-------------------+----------------+-------------+
```
&nbsp;

## Atualizando mais de um campo:

```mysql

UPDATE tb_aluno 
SET cidadeAluno = 'Porto Alegre', estadoAluno='RS' 
WHERE idAluno = 4; 
```

↳ Saída gerada: 
```
+---------+--------------------+----------------+-------------+
| idAluno |     nomeAluno      |  cidadeAluno   | estadoAluno |
+---------+--------------------+----------------+-------------+
|      1  | Luana Borba        | Curitiba       | PR          |
|      2  | Mariana Fernandes  | Rio de Janeiro | RJ          |
|      3  | Cátia Marcondes    | Santo André    | SP          |
|      4  | Marcos Góes Filho  | Porto Alegre   | RS          |
+---------+--------------------+----------------+-------------+

```
&nbsp;
  
**Caso não seja utilizada a cláusula `WHERE`, todos os registros da tabela serão atualizados com a mesma informação!**

```mysql

UPDATE tb_aluno 
SET cidadeAluno = 'Curitiba', estadoAluno="PR";
```

↳ Saída gerada: 
```
+---------+-------------------+-------------+-------------+
| idAluno |     nomeAluno     | cidadeAluno | estadoAluno |
+---------+-------------------+-------------+-------------+
|       1 | Luana Borba       | Curitiba    | PR          |
|       2 | Mariana Fernandes | Curitiba    | PR          |
|       3 | Cátia Marcondes   | Curitiba    | PR          |
|       4 | Marcos Góes Filho | Curitiba    | PR          |
+---------+-------------------+-------------+-------------+
```

&nbsp;

<div align="center">
<a href="https://github.com/michelelozada/SQL-Study-Notes">[Voltar à tela inicial do repositório]</a>
</div>