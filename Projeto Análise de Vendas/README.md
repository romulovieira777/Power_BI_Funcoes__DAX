### Funções Data Analysis Expressions (DAX) utilizadas para a execução do dashboard:

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

**O que a função BLANK faz:**

Retorna um espaço em branco.

**Sintaxe**

~~~py
BLANK()
~~~

**Exemplo**

~~~py
IF(SUM(InternetSales_USD[SalesAmount_USD])= 0, BLANK(), SUM(ResellerSales_USD[SalesAmount_USD]) / SUM(InternetSales_USD[SalesAmount_USD]))
~~~

**O que a função CALCULATE faz:**

Avalia uma expressão em um contexto de filtro modificado.

**Sintaxe**

~~~py
CALCULATE(<expression>[, <filter1> [, <filter2> [, …]]])
~~~

**Exemplo**

~~~py
CALCULATE(
    SUM(Sales[Sales Amount]),
    'Product'[Color] = "Blue"
)
~~~

**O que a função CALENDAR faz:**

Retorna uma tabela com apenas uma coluna chamada "Date" que contém um conjunto contíguo de datas. 
O intervalo de datas é da data de início especificada até a data de término especificada, inclusive essas duas datas.

**Sintaxe**

~~~py
CALENDAR(<start_date>, <end_date>)
~~~

**Exemplo**

~~~py
CALENDAR(DATE(2005, 1, 1), DATE(2015, 12, 31))
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

**O que a função COUNTROWS faz:**

Conta o número de linhas na tabela especificada ou em uma tabela definida por uma expressão.

**Sintaxe**

~~~py
COUNTROWS(<table>)
~~~

**Exemplo**

~~~py
COUNTROWS('Orders')
~~~

**O que a função DATEADD faz:**

Retorna uma tabela que contém uma coluna de datas, deslocada para frente ou para trás no tempo pelo número especificado de intervalos começando nas datas do contexto atual.

**Sintaxe**

~~~py
DATEADD(<dates>, <number_of_intervals>, <interval>)
~~~

**Exemplo**

~~~py
DATEADD(DateTime[DateKey], -1, year) 
~~~

**O que a função DAY faz:**

Retorna o dia do mês, um número de 1 a 31.

**Sintaxe**

~~~py
DAY(<date>) 
~~~

**Exemplo**

~~~py
DAY("3-4-1007")
~~~

**O que a função DISTINCTCOUNT faz:**

Conta o número de valores distintos de uma coluna.

**Sintaxe**

~~~py
DISTINCTCOUNT(<column>) 
~~~

**Exemplo**

~~~py
DISTINCTCOUNT(ResellerSales_USD[SalesOrderNumber])
~~~

**O que a função EARLIER faz:**

Retorna o valor atual da coluna especificada em uma etapa de avaliação externa da coluna mencionada.

**Sintaxe**

~~~py
EARLIER(<column>, <number>)
~~~

**Exemplo**

~~~py
COUNTROWS(FILTER(ProductSubcategory, EARLIER(ProductSubcategory[TotalSubcategorySales]) <ProductSubcategory[TotalSubcategorySales])) + 1
~~~

**O que a função FILTER faz:**

Retorna uma tabela que representa um subconjunto de outra tabela ou expressão.

**Sintaxe**

~~~py
FILTER(<table>, <filter>)  
~~~

**Exemplo**

~~~py
FILTER('InternetSales_USD', RELATED('SalesTerritory'[SalesTerritoryCountry]) <> "United States")
~~~

**O que a função FORMAT faz:**

Converte um valor em texto de acordo com o formato especificado.

**Sintaxe**

~~~py
FORMAT(<value>, <format_string>)   
~~~

**Exemplo**

~~~py
FORMAT('Date'[Date], "dd/mm/yyyy")
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

**O que a função ISERROR faz:**

Verifica se um valor está errado e retorna TRUE ou FALSE.

**Sintaxe**

~~~py
ISERROR(<value>)
~~~

**Exemplo**

~~~py
  IF(ISERROR(  
       SUM('ResellerSales_USD'[SalesAmount_USD])  
       / SUM('InternetSales_USD'[SalesAmount_USD])  
             )  
    , BLANK()  
    , SUM('ResellerSales_USD'[SalesAmount_USD])  
      / SUM('InternetSales_USD'[SalesAmount_USD])  
    )
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

**O que a função MAX faz:**

Retorna o maior valor de uma coluna ou entre duas expressões escalares.

**Sintaxe**

~~~py
MAX(<column>)  
~~~

**Exemplo**

~~~py
Max([TotalSales]) 
~~~

**O que a função MIN faz:**

Retorna o menor valor de uma coluna ou entre duas expressões escalares.

**Sintaxe**

~~~py
MIN(<column>)
~~~

**Exemplo**

~~~py
MIN([ResellerMargin]) 
~~~

**O que a função MONTH faz:**

Retorna o mês como um número entre 1 (janeiro) e 12 (dezembro).

**Sintaxe**

~~~py
MONTH(<datetime>)   
~~~

**Exemplo**

~~~py
MONTH("March 3, 2008 3:45 PM")
~~~

**O que a função RANK.EQ faz:**

Retorna a classificação de um número em uma lista de números.

**Sintaxe**

~~~py
RANK.EQ(<value>, <columnName> [, <order>])   
~~~

**Exemplo**

~~~py
RANK.EQ(InternetSales_USD[SalesAmount_USD], InternetSales_USD[SalesAmount_USD])
~~~

**O que a função RANKX faz:**

Retorna a classificação de um número em uma lista de números para cada linha no argumento table.

**Sintaxe**

~~~py
RANKX(<table>, <expression> [, <value> [, <order> [, <ties>]]]) 
~~~

**Exemplo**

~~~py
RANKX(ALL(Products), SUMX(RELATEDTABLE(InternetSales), [SalesAmount]))
~~~

**O que a função RELATED faz:**

Retorna um valor relacionado de outra tabela.

**Sintaxe**

~~~py
RELATED(<column>)
~~~

**Exemplo**

~~~py
  SUMX(FILTER( 'InternetSales_USD'  
            ,  RELATED('SalesTerritory'[SalesTerritoryCountry])  
               <> "United States"  
             )  
     ,'InternetSales_USD'[SalesAmount_USD])
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

**O que a função SUMMARIZE faz:**

Retorna uma tabela de resumo para os totais solicitados sobre um conjunto de grupos.

**Sintaxe**

~~~py
SUMMARIZE (<table>, <groupBy_columnName> [, <groupBy_columnName> ]…[, <name>, <expression>]…)
~~~

**Exemplo**

~~~py
SUMMARIZE(ResellerSales_USD  
      , DateTime[CalendarYear]  
      , ProductCategory[ProductCategoryName]  
      , "Sales Amount (USD)", SUM(ResellerSales_USD[SalesAmount_USD])  
      , "Discount Amount (USD)", SUM(ResellerSales_USD[DiscountAmount])  
      )
~~~

**O que a função SUMX faz:**

Retorna a soma de uma expressão avaliada para cada linha de uma tabela.

**Sintaxe**

~~~py
SUMX(<table>, <expression>)
~~~

**Exemplo**

~~~py
SUMX(FILTER(InternetSales, InternetSales[SalesTerritoryID] = 5), [Freight])
~~~

**O que a função UNICHAR faz:**

Retorna o caractere Unicode referenciado pelo valor numérico.

**Sintaxe**

~~~py
SUMX(<table>, <expression>)
~~~

**Exemplo**

~~~py
UNICHAR(65)
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

**O que a função WEEKDAY faz:**

Retorna um número de 1 a 7 que identifica o dia da semana de uma data. Por padrão, o dia varia entre 1 (domingo) e 7 (sábado).

**Sintaxe**

~~~py
WEEKDAY(<date>, <return_type>)
~~~

**Exemplo**

~~~py
WEEKDAY([HireDate] + 1)
~~~

**O que a função YEAR faz:**

Retorna o ano de uma data como um inteiro de quatro dígitos no intervalo 1900-9999.

**Sintaxe**

~~~py
YEAR(<date>)   
~~~

**Exemplo**

~~~py
YEAR("March 2007")
~~~
