Funções DAX (Data Analysis Expressions) utilizadas para a execução do dashboard:

[Arquivo em JPG](https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Relat%C3%B3rio%20de%20Notas%20Fiscais/Dashboard.jpg)
<br>
<img heigth="550" src="https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Relat%C3%B3rio%20de%20Notas%20Fiscais/Dashboard.jpg"/>
<br/>

**O que a função AND faz:**

Verifica se ambos os argumentos são TRUE e retorna TRUE se isso se confirmar. Caso contrário, retorna false.

**Sintaxe**

~~~py
AND(<logical1>,<logical2>)
~~~

**Exemplo**

~~~py
IF(AND(10 > 9, -10 < -1), "All true", "One or more false"
~~~

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

**O que a função COUNT faz:**

Conta o número de células de uma coluna que contém valores que não estão em branco.

**Sintaxe**

~~~py
COUNT(<column>)
~~~

**Exemplo**

~~~py
COUNT([ShipDate])
~~~

**O que a função IF faz:**

Verifica uma condição e retorna um valor quando é TRUE; caso contrário, retorna um segundo valor.

**Sintaxe**

~~~py
IF(<logical_test>, <value_if_true> [, <value_if_false>])  
~~~

**Exemplo**

~~~py
IF(
    'Product'[List Price] < 500,
    "Low",
    "High"
)
~~~

**O que a função LEFT faz:**

Retorna o número especificado de caracteres do início de uma cadeia de texto.

**Sintaxe**

~~~py
LEFT(<text>, <num_chars>)
~~~

**Exemplo**

~~~py
CONCATENATE(LEFT('Reseller'[ResellerName],LEFT(GeographyKey,3))
~~~

**O que a função OR faz:**

Verifica se um dos argumentos é TRUE para retornar TRUE. A função retornará FALSE se os dois argumentos forem FALSE.

**Sintaxe**

~~~py
OR(<logical1>,<logical2>)
~~~

**Exemplo**

~~~py
IF(   OR(   CALCULATE(SUM('ResellerSales_USD'[SalesAmount_USD]), 'ProductSubcategory'[ProductSubcategoryName]="Touring Bikes") > 1000000  
         ,   CALCULATE(SUM('ResellerSales_USD'[SalesAmount_USD]), 'DateTime'[CalendarYear]=2007) > 2500000  
         )  
   , "Circle of Excellence"  
   , ""  
   )
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

**O que a função UPPER faz:**

Converte uma cadeia de texto em letras maiúsculas.

**Sintaxe**

~~~py
UPPER(<text>)     
~~~

**Exemplo**

~~~py
UPPER(['New Products'[Product Code]) 
~~~
