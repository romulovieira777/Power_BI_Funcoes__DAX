## Dashboard Construído

[Arquivo Power BI](https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Relat%C3%B3rio%20de%20Vendas/Projeto%20Consolidando%20Vendas.pbix)

**Dashboard Construído**
<br>
<img heigth="500" src="https://github.com/romulovieira777/Power_BI_Funcoes__DAX/blob/main/Relat%C3%B3rio%20de%20Vendas/Dashboard.jpg"/>
<br/>

### Funções DAX (Data Analysis Expressions) utilizadas para a execução do dashboard:

**O que a função LEFT faz:**

Retorna o número especificado de caracteres do início de uma cadeia de texto.

**Sintaxe**

~~~py
LEFT(<text>, <num_chars>)
~~~

**Exemplo**

~~~py
CONCATENATE(LEFT('Reseller'[ResellerName], LEFT(GeographyKey,3))
~~~

**O que a função LEN faz:**

Retorna o número de caracteres em uma cadeia de texto.

**Sintaxe**

~~~py
LEN(<text>)
~~~

**Exemplo**

~~~py
LEN([AddressLine1]) + LEN([AddressLin2])
~~~
