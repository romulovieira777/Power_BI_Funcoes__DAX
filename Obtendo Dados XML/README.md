  ## Dashboard Construído
  
[Arquivo Power BI](https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Obtendo%20Dados%20XML/Projeto%2008%20XML.pbix)

<br>
<img height="500" src="https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Obtendo%20Dados%20XML/Dashboard.jpg"/>
<br/>

### Funções DAX (Data Analysis Expressions) utilizadas para a execução do dashboard:

**O que a função AVERAGE faz:**

Retorna a média aritmética de todos os números de uma coluna.

**Sintaxe**

~~~py
AVERAGE(<column>)
~~~

**Exemplo**

~~~py
AVERAGE(InternetSales[ExtendedSalesAmount])
~~~

**O que a função COUNTA faz:**

A função COUNTA conta o número de células de uma coluna que não estão vazias.

**Sintaxe**

~~~py
COUNTA(<column>)
~~~

**Exemplo**

~~~py
COUNTA('Reseller'[Phone])
~~~

**O que a função LOWER faz:**

Converte todas as letras de uma cadeia de texto em minúsculas.

**Sintaxe**

~~~py
LOWER(<text>)  
~~~

**Exemplo**

~~~py
LOWER('New Products'[ProductCode])
~~~

**O que a função RIGHT faz:**

RIGHT retorna o último caractere ou caracteres em uma cadeia de texto, com base no número de caracteres que você especificar.

**Sintaxe**

~~~py
RIGHT(<text>, <num_chars>)
~~~

**Exemplo**

~~~py
RIGHT('New Products'[ProductCode],[MyCount])
~~~

**O que a função SUM faz:**

Adiciona todos os números de uma coluna.

**Sintaxe**

~~~py
SUM(<column>)
~~~

**Exemplo**

~~~py
SUM(Sales[Amt])
~~~
