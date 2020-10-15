## Dashboard Construído

[Arquivo Power BI](https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Gr%C3%A1fico%20Curva%20ABC/Projeto%2007.pbix)

**Dashboard Construído**

<br>
<img height="500" src="https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Gr%C3%A1fico%20Curva%20ABC/Dashboard.jpg"/>
<br/>

**Modelagem dos Dados**
<br>
<img height="400" src="https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Gr%C3%A1fico%20Curva%20ABC/Modelagem%20de%20Dados.jpg"/>
<br/>

### Funções DAX (Data Analysis Expressions) utilizadas para a execução do dashboard:

**O que a função ALL faz:**

Retorna todas as linhas de uma tabela ou todos os valores de uma coluna, ignorando todos os filtros que estiverem aplicados.
Essa função é útil para limpar filtros e criar cálculos em todas as linhas em uma tabela.

**Sintaxe**

~~~py
ALL( [<table> | <column>[, <column>[, <column>[,…]]]] )
~~~

**Exemplo**

~~~py
SUMX(ResellerSales_USD, ResellerSales_USD[SalesAmount_USD])
/
SUMX(ALL(ResellerSales_USD), ResellerSales_USD[SalesAmount_USD])
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

**O que a função CALENDARAUTO faz:**

Retorna uma tabela com apenas uma coluna chamada "Date" que contém um conjunto contíguo de datas.
O intervalo de datas é calculado automaticamente com base nos dados no modelo.

**Sintaxe**

~~~py
CALENDARAUTO([fiscal_year_end_month])
~~~

**Exemplo**

~~~py
CALENDARAUTO()
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

**O que a função HASONEFILTER faz:**

Retorna TRUE quando o número de valores filtrados diretamente em columnName é um; caso contrário, retorna FALSE.

**Sintaxe**

~~~py
HASONEFILTER(<columnName>)  
~~~

**Exemplo**

~~~py
IF(HASONEFILTER(ResellerSales_USD[ProductKey]), FILTERS(ResellerSales_USD[ProductKey]), BLANK())
~~~

**O que a função HASONEVALUE faz:**

Retorna TRUE quando o contexto para columnName foi filtrado para apenas um valor distinto. Caso contrário, será FALSE.

**Sintaxe**

~~~py
HASONEVALUE(<columnName>)
~~~

**Exemplo**

~~~py
IF(HASONEVALUE(DateTime[CalendarYear]), SUM(ResellerSales_USD[SalesAmount_USD])
/
CALCULATE(SUM(ResellerSales_USD[SalesAmount_USD]), DateTime[CalendarYear] = 2007), BLANK())
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

**O que a função LOOKUPVALUE faz:**

Retorna o valor da linha que atende a todos os critérios especificados pelos critérios de pesquisa. A função pode aplicar um ou mais critérios de pesquisa.

**Sintaxe**

~~~py
LOOKUPVALUE(
    <result_columnName>,
    <search_columnName>,
    <search_value>
    [, <search2_columnName>, <search2_value>]…
    [, <alternateResult>]
)
~~~

**Exemplo**

~~~py
[Region] = LOOKUPVALUE(Employee[Region], Employee[Email], USERNAME(), BLANK())
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

**O que a função SAMEPERIODLASTYEAR faz:**

Retorna uma tabela que contém uma coluna de datas deslocadas para um ano antes das datas na coluna dates especificada, no contexto atual.

**Sintaxe**

~~~py
SAMEPERIODLASTYEAR(<dates>)
~~~

**Exemplo**

~~~py
CALCULATE(SUM(ResellerSales_USD[SalesAmount_USD]), SAMEPERIODLASTYEAR(DateTime[DateKey]))
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

**O que a função SWITCH faz:**

Avalia uma expressão em relação a uma lista de valores e retorna uma das várias expressões de resultado possíveis.

**Sintaxe**

~~~py
SWITCH(<expression>, <value>, <result>[, <value>, <result>]…[, <else>])
~~~

**Exemplo**

~~~py
SWITCH([Month], 1, "January", 2, "February", 3, "March", 4, "April"  
               , 5, "May", 6, "June", 7, "July", 8, "August"  
               , 9, "September", 10, "October", 11, "November", 12, "December"  
               , "Unknown month number" )
~~~

**O que a função TRUE faz:**

Retorna o valor lógico TRUE.

**Sintaxe**

~~~py
TRUE()
~~~

**Exemplo**

~~~py
IF(SUM('InternetSales_USD'[SalesAmount_USD]) >200000, TRUE(), false())
~~~

**O que a função USERELATIONSHIP faz:**

Especifica a relação a ser usada em um cálculo específico como aquela que existe entre columnName1 e columnName2.

**Sintaxe**

~~~py
USERELATIONSHIP(<columnName1>,<columnName2>)
~~~

**Exemplo**

~~~py
CALCULATE(SUM(InternetSales[SalesAmount]), USERELATIONSHIP(InternetSales[ShippingDate], DateTime[Date]))
~~~

**O que a função VALUES faz:**

Quando o parâmetro de entrada é um nome de coluna, retorna uma tabela de coluna única que contém os valores distintos da coluna especificada. 
Valores duplicados são removidos e apenas valores exclusivos são retornados. Um valor BLANK pode ser adicionado. 
Quando o parâmetro de entrada é um nome de tabela, retorna as linhas da tabela especificada. Linhas duplicadas são preservadas. 
Uma linha BLANK pode ser adicionada.

**Sintaxe**

~~~py
VALUES(<TableNameOrColumnName>)
~~~

**Exemplo**

~~~py
COUNTROWS(VALUES('InternetSales_USD'[SalesOrderNumber]))
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
