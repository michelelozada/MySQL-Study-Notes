> **Implementando procedimentos (comando CREATE PROCEDURE)**  
> Repositório: Banco de Dados SQL - Fundamentos  
> GitHub: @michelelozada
&nbsp;
     
&nbsp;  
## Procedimento armazenado (aka store procedure) 
```
- É uma subrotina, armazenada de maneira persistente no SGBD, organizada para receber parâmetros e 
executar uma ou mais tarefas    

- É o comando `CALL`, que junto ao nome de identificação, invoca o procedimento armazenado  
```

&nbsp;  

↳ A tabela a ser utilizada para os exemplos abaixo:
```
+---------+----------------+-------+-------------+
| idCurso |   nomeCurso    | Turno | Mensalidade |
+---------+----------------+-------+-------------+
|       1 | Direito        | M     |      876.28 |
|       2 | Direito        | N     |      950.28 |
|       5 | Pedagogia      | M     |      249.50 |
|       6 | Pedagogia      | N     |      278.50 |
|       7 | Design Gráfico | M     |      622.05 |
|       8 | Design Gráfico | N     |      670.10 |
+---------+----------------+-------+-------------+
```

&nbsp;
    
Declarando um procedimento:
```mysql

CREATE PROCEDURE consultaMensalidade(pesquisaCurso varchar(50))
SELECT CONCAT('O valor da mensalidade do curso ' , nomeCurso , ' (turno ' , turnoCurso , ') é R$ ', mensalidadeCurso , '.') AS Consulta_Mensalidade
FROM tb_curso
WHERE nomeCurso = pesquisaCurso;
```

&nbsp;    

Invocando o procedimento:
```mysql

CALL consultaMensalidade('Direito');
```

↳ Saída gerada:
```
+----------------------------------------------------------------+
|                      Consulta_Mensalidade                      |
+----------------------------------------------------------------+
| O valor da mensalidade do curso Direito (turno M) é R$ 876.28. |
| O valor da mensalidade do curso Direito (turno N) é R$ 950.28. |
+----------------------------------------------------------------+
```

&nbsp;

Invocando o procedimento novamente, usando outro argumento:
```mysql

CALL consultaMensalidade('Design Gráfico');
```

↳ Saída gerada:
```
+-----------------------------------------------------------------------+
|                         Consulta_Mensalidade                          |
+-----------------------------------------------------------------------+
| O valor da mensalidade do curso Design Gráfico (turno M) é R$ 622.05. |
| O valor da mensalidade do curso Design Gráfico (turno N) é R$ 670.10. |
+-----------------------------------------------------------------------+
```

&nbsp;

Excluindo o procedimento acima:
```mysql

DROP PROCEDURE consultaMensalidade;
```

&nbsp;

<div align="center">
<a href="https://github.com/michelelozada/SQL-Study-Notes">[Voltar à tela inicial do repositório]</a>
</div>