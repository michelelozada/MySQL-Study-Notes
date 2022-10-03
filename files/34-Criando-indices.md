> **Criando índices no MySQL**  
> Repositório: Banco de Dados MySQL - Fundamentos  
> GitHub: @michelelozada
&nbsp;

&nbsp;    
**Índices**  
&nbsp;  
São estruturas associadas às tabelas que, uma vez aplicadas, podem ajudar a melhorar a performance na execução de consultas em um 
banco de dados.   
&nbsp;
&nbsp;     
**A tabela para exemplo**
```mysql
CREATE TABLE tb_aluno(
    id_aluno int(11) AUTO_INCREMENT NOT NULL,
    nome_aluno varchar(60) not null,
    telefone_aluno varchar(15) not null,
    PRIMARY KEY (id_aluno)
);
```
&nbsp;
&nbsp;      
**1 - Criando um índice em uma tabela, após a mesma já ter sido criada** 
```mysql
CREATE INDEX idx_nome_aluno
ON tb_aluno(nome_aluno);
```
&nbsp;
&nbsp;     
**Ou, alternativamente:**
```mysql
ALTER TABLE tb_aluno
ADD INDEX idx_nome_aluno(nome_aluno); 
```
&nbsp;
&nbsp;     
**2 - Exibindo os índices já criados nas tabelas do banco de dados**
```mysql
SHOW INDEX FROM tb_aluno;
```
&nbsp;
&nbsp;     
**3 - Excluindo o índice de uma coluna da tabela**
```mysql
DROP INDEX idx_nome_aluno
ON tb_aluno;
```
&nbsp;
&nbsp;      
**Considerando-se a tabela do exemplo acima, populada da seguinte forma:**
| id_aluno | nome_aluno  | telefone_aluno |
| :---     | :---        | :---           |
| 1	       | Ana	     | (41)99999-9999 |
| 2	       | Bernardo	 | (41)99999-8888 |
| 3	       | Cida	     | (41)99999-7777 | 
| 4	       | Daniel	     | (41)99999-6666 |
| 5	       | Elaine	     | (41)99999-5555 |

&nbsp;
&nbsp;    
Se antes da aplicação do indíce, for executado o comando **`EXPLAIN SELECT`** abaixo: 
```mysql 
EXPLAIN SELECT * FROM tb_aluno
WHERE nome_aluno = "Elaine"; 
```
&nbsp;
&nbsp;    
É informado que para encontrar a informação solicitada (ou seja, a aluna de nome Elaine), foi preciso percorrer 5 linhas; ao passo 
que - após a aplicação do indice **`idx_nome_aluno`**, conforme o que foi feito acima -  ao ser executado novamente o comando **`EXPLAIN SELECT`**, é retornado
que agora foi preciso percorrer apenas 1 linha para encontrar a informação solicitada.