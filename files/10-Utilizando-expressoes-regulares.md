> **Utilizando expressões regulares no MySQL (operador REGEXP)**  
> Repositório: Banco de Dados MySQL - Fundamentos  
> GitHub: @michelelozada
&nbsp;
     
&nbsp;  
Para pesquisa de banco de dados, o MySQL também suporta operações de correspondência de padrões com base em expressões
regulares. Para isso, deve ser utilizado o operador `REGEXP`, junto da seguinte notação:

&nbsp;
     
`^` - Início da string  
`$` - Fim da string  
`[]` - Os caracteres ficam listados entre colchetes   
`[^]` -	O sinal ^ representa a negação dos caracteres listados entre colchetes  

&nbsp;  

**A tabela a ser usada para os exemplos abaixo:**  
| idCurso | nomeCurso                |
| :---    | :---                     | 
| 1	      | Design                   |
| 2	      | Direito                  |
| 3	      | Engenharia Civil         |
| 4	      | Engenharia da Computação |
| 5	      | Jornalismo               |
| 6	      | Moda                     |
| 7	      | Pedagogia                |
| 8	      | Psicologia               | 

&nbsp;
  
**1 - Correspondências no início da string (`^`)**:

&nbsp;
 
*Retornando os registros que começam com a letra 'd'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP '^[d]';

-- Retorna: Design, Direito
```

&nbsp;

*Retornando os registros que começam com as letras 'd' ou 'p'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP '^[dp]';

-- Retorna: Design, Direito, Pedagogia, Psicologia
```

&nbsp;

**2 - Correspondências no final da string (`$`)**:  

&nbsp;  

*Retornando os registros que terminam com a letra 'n'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP '[n]$';

-- Retorna: Design
```

&nbsp;

*Retornando os registros que terminam com as letras 'a' ou 'n'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP '[a|n]$';

-- Retorna: Design, Moda, Pedagogia, Psicologia
```

&nbsp;
  
**3 - Correspondências no  meio da string**:

&nbsp; 

*Retornando registros que terminam contenham a letra 't'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP '[t]';

-- Retorna: Direito, Engenharia da Computação
```

&nbsp;  

**4 - Não-correspondência com os caracteres indicados entre os colchetes:**

&nbsp;  

*Retornando os registros que não comecem com as letras 'd', 'e' ou 'p'.*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP '^[^dep]';

-- Retorna: Jornalismo, Moda
```

&nbsp;  

**5 - Correspondência com sequências de uma string**:

&nbsp;  

*Retornando os registros que contenham a sequência 'enge'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP 'enge?';

-- Retorna: Engenharia Civil, Engenharia da Computação
```

&nbsp;  

*Retornando os registros que contenham as sequências 'gia' ou 'ria'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP 'gia|ria';

-- Retorna: Engenharia Civil, Engenharia da Computação, Pedagogia, Psicologia
```

&nbsp;  

*Retornando os registros que terminem com a sequência 'gia'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP 'gia[[:>:]]';

-- Retorna: Pedagogia, Psicologia
```

&nbsp;  

*Retornando os registros que comecem com as sequência 'enge'*
```mysql
SELECT * FROM tb_curso 
WHERE nomeCurso REGEXP '[[:<:]]enge'; 

-- Retorna: Engenharia Civil, Engenharia da Computação
```

&nbsp;

<div align="center">
<a href="https://github.com/michelelozada/MySQL-Study-Notes">[Voltar à tela inicial do repositório]</a>
</div>