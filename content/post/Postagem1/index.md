---
title: "Explorando o mercado de capitais em R"
author: "Helson Gomes de Souza"
date: "2025-09-01"
output: html_document
---


<hr>

# Introdução

Na área de finanças, conhecer as cotações e as tendências do mercado de capitais é fundamental para uma tomada de decisão eficiente. Bancos, corretoras e intermediadoras financeiras geralmente dispõem de ferramentas que auxiliam o tomador de decisão quanto à escolha de ativos por meio de gráficos de cotações e indicadores financeiros. Contudo, essa tarefa pode ser facilmente executada na linguagem *R* usando a biblioteca *quantmod* e bibliotecas auxiliares. O objetivo desse post é mostrar como essa biblioteca pode auxiliar na análise financeira, no aprendizado e na resolução de problemas referentes ao mercado de capitais.

# Importando dados do mercado de capitais

O primeiro passo para explorar os dados do mercado de capitais é instalar e liberar a biblioteca.


``` r
#install.packages("quantmod")
library(quantmod)
```

```
FALSE Carregando pacotes exigidos: xts
```

```
FALSE Carregando pacotes exigidos: zoo
```

```
FALSE 
FALSE Anexando pacote: 'zoo'
```

```
FALSE Os seguintes objetos são mascarados por 'package:base':
FALSE 
FALSE     as.Date, as.Date.numeric
```

```
FALSE Carregando pacotes exigidos: TTR
```

```
FALSE Registered S3 method overwritten by 'quantmod':
FALSE   method            from
FALSE   as.zoo.data.frame zoo
```


Tendo instalado e liberado a biblioteca, o próximo passo é importar as cotações dos ativos. Essa tarefa é feita usando a função *getSymbols*, a qual requer o código de negociação do ativo, de tal modo que, se o ativo for brasileiro esse código deve ser precedido da string *".SA"*. Para exemplificar, considere importar as cotações da empresa Vale, com código de negociação *"VALE3"*.


``` r
getSymbols("VALE3.SA")
```

```
FALSE [1] "VALE3.SA"
```

O resultado é um dataframe com o preço de abertura *"VALE3.SA.Open"*, o preço máximo *"VALE3.SA.High"*, o preço mínimo *"VALE3.SA.Low"*, o preço de fechamento *"VALE3.SA.Close"*, o volume negociado *"VALE3.SA.Volume"* e o preço ajustado no *after market* *"VALE3.SA.Adjusted"*.

Um gráfico simples da série pode ser gerado com o seguinte comando:


``` r
plot(Cl(VALE3.SA), col = 'black')
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

# Visualizando os dados

Um gráfico de velas pode ser elaborado usando a função *candleChart*. Para facilitar a visualização, considere representar na figura apenas o ano de 2023.


``` r
candleChart(VALE3.SA["2023"])
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

A biblioteca dispões de temas prontos que facilitam a visualização das cotações e personalizam a figura gerada. Por exemplo:


``` r
candleChart(
  VALE3.SA,
  theme = "white",
  subset = '2023-06::2023-12'
)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />

Agora considere que seja interessante mudar a cor dos candles de acordo com a variação da cotação, de modo que, caso a cotação suba, então o candle deve ter cor azul e caso a cotação caia o candle deve ter cor vermelha. Nesse caso, deve-se proceder da seguinte maneira:


``` r
candleChart(
  VALE3.SA,
  theme = chartTheme("white", up.col = "blue", dn.col = "red"),
  subset = '2023-06::2023-12'
)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />

Alguns indicadores podem ser incluídos na figura. Por exemplo, uma média móvel pode ser adicionada com a função *addSMA*, que deve ser requerida logo após a geração do gráfico de velas. No caso de uma média móvel de sete semanas, deve-se proceder como:




``` r
addSMA(n = 7*5)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-8-1.png" width="672" />

Use a função *addBBands()* para adicionar bandas de bollinger ao gráfico de velas.




``` r
addBBands()
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-10-1.png" width="672" />

# Conclusões

A linguagem *R* dispõe de ferramentas bastante úteis para lidar com o mercado de capitais e a biblioteca *quantmod* é uma das mais completas e eficientes na parte de visualização dos dados. Maiores detalhes podem ser consultados em https://www.quantmod.com/.


# Referências

quantmod. **Quantitative Financial Modelling & Trading Framework for R**. https://www.quantmod.com/. 

<hr>

<p></p>
<p></p>
<p></p>
<p></p>

