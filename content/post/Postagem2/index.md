---
title: "Acessando as variações mensais do IPCA em R"
author: "Prof. Dr. Helson Gomes"
date: "2025-01-02"
output: html_document
draft: false
---


<hr>



# Introdução

O Índice de Preços ao Consumidor Amplo (IPCA) é um indicador divulgado pelo Instituto Brasileiro de Geografia e Estatística (IBGE) que tem como finalidade expressar periodicamente o preço médio de uma cesta representativa de produtos no Brasil. Para a construção do índice, os preços dos produtos são consultados em um conjunto de regiões representativas do Brasil, as quais teoricamente poderiam refletir de modo geral o comportamento do consumidor mediano brasileiro.

A cesta representativa do índice é composta por ítens de consumo pertencentes a nove categorias de produtos: (i) Alimentação e bebidas; (ii) Habitação; (iii) Artigos de residência; (iv) Vestuário; (v) Transportes; (vi) Saúde e cuidados pessoais; (vii) Despesas pessoais; (viii) Educação; e (ix) Comunicação. Os preços da cesta representativa geralmente são pesquisados em 10 regiões metropolitanas do Brasil, sendo: (i) 1501. Belém (PA); (ii) Fortaleza (CE); (iii) Recife (PE); (iv) Salvador (BA); (v) Belo Horizonte (MG); (vi) 3201. Grande Vitória (ES); (vii) Rio de Janeiro (RJ); (viii) São Paulo (SP); (ix) Curitiba (PR); e (x) Porto Alegre (RS).

Algumas ferramentas viabilizam o acesso aos resultados do IPCA, como o portal [SIDRA](https://sidra.ibge.gov.br/tabela/7060), o portal IPEADATA ou o pacote do Banco Central do Brasil para uso em R, o [rbcb](https://cran.r-project.org/web/packages/rbcb/index.html). Contudo, o usuário pode acessar esses resultados de maneira direta no portal SIDRA por meio da linguagem R (ou quaisquer outras linguagens) usando técnicas simples de manipulação de dados sem a necessidade de recorrer a um pacote de terceiros.

O objetivo desse post é, portanto, demonstrar uma maneira simples e factível de como obter acesso aos resultados mensais do IPCA usando R.

# Construindo a função

## Bibliotecas

Para replicar os códigos aqui apresentados, é necessário que o leitor tenha instalado as bibliotecas *dplyr, tidyr, openxlsx, lubridate* e *ggplot2*. A instalação pode ser feita por meio da seguinte lógica: *install.packages("nome da biblioteca")*. Tendo instalado as bibliotecas, o próximo passo é liberá-las para o uso.


``` r
lapply(list("dplyr", "tidyr", "ggplot2", "lubridate", "openxlsx"), require, character.only = T)
```

```
FALSE [[1]]
FALSE [1] TRUE
FALSE 
FALSE [[2]]
FALSE [1] TRUE
FALSE 
FALSE [[3]]
FALSE [1] TRUE
FALSE 
FALSE [[4]]
FALSE [1] TRUE
FALSE 
FALSE [[5]]
FALSE [1] TRUE
```

## Parâmetros da função
A ideia central é construir uma função em que o usuário possa escolher um período e uma região metropolitana para obter as informações. Assim, a função será elaborada com base nos seguintes parâmetros.

* *mes_inicial*: Argumento numérico \{1,2,...,12\} que indica o número do mês que inicia o período de interesse.

* *mes_final*: Argumento numérico \{1,2,...,12\} que indica o número do mês que finaliza o período de interesse.

* *ano_inicial*: Argumento numérico \{2020, 2021, ..., 2024\} que indica o número do ano que inicia o período de interesse.

* *ano_final*: Argumento numérico \{2020, 2021, ..., 2024\} que indica o número do ano que finaliza o período de interesse.

* *capital*: Argumento não numérico que indica o código da região metropolitaba de interesse, possuindo os seguintes valores válidos: (i) "all" para o Brasil; (ii) "1501" para Belém (PA); (iii) "2301" para Fortaleza (CE); (iv) "2601" para Recife (PE); (v) "2901" para Salvador (BA); (vi) "3101" para Belo Horizonte (MG); (vii) "3201" para Grande Vitória (ES); (viii) "3301" para Rio de Janeiro (RJ); (ix) "3501" para São Paulo (SP); (x) "4101" para Curitiba (PR); e (xi) "4301" para Porto Alegre (RS).

*plot*: Argumento lógico. TRUE se o usuário deseja que a função retorne um gráfico de linhas com as variações mensais e FALSE se o usuário deseja que a função retorne um dataframe.

Dadas essas definições, a função para acesso aos resultados do IPCA pode assumir a seguinte forma:

## Especificação da função


``` r
ipca = function(mes_inicial, mes_final, ano_inicial, ano_final, capital = "all", plot = TRUE){
  rmet = data.frame(
    codigo = c("all", 1501, 2301, 2601, 2901, 3101, 3201, 3301, 3501, 4101, 4301),
    capital = c("Brasil", "Belém (PA)", "Fortaleza (CE)", "Recife (PE)", "Salvador (BA)", "Belo Horizonte (MG)", "Grande Vitória (ES)",
                "Rio de Janeiro (RJ)", "São Paulo (SP)", "Curitiba (PR)", "Porto Alegre (RS)"
    ))
  dt = data.frame()
  tipo = ifelse(capital == "all", "n1", "n7")
  for(ano in ano_inicial:ano_final){
    for(mes in mes_inicial:mes_final){
      if(nchar(mes) == 1){
        link = sprintf("https://sidra.ibge.gov.br/geratabela?format=xlsx&name=tabela7060.xlsx&terr=N&rank=-&query=t/7060/%s/%s/v/63/p/%i0%i/c315/7169/d/v63%%202/l/,p%%2Bt%%2Bv,c315",
                       tipo,
                       capital,
                       ano,
                       mes
        )
      }else{
        link = sprintf("https://sidra.ibge.gov.br/geratabela?format=xlsx&name=tabela7060.xlsx&terr=N&rank=-&query=t/7060/%s/%s/v/63/p/%i%i/c315/7169/d/v63%%202/l/,p%%2Bt%%2Bv,c315",
                       tipo,
                       capital,
                       ano,
                       mes
        )
      }
      
      dt1 = read.xlsx(link, startRow = 4)
      dt1 = dt1[2,]
      datas = my(sprintf("%i-%i", mes, ano))
      names(dt1) = c("Produto", c(as.character(datas)))
      dt1 = dt1 %>% 
        gather(key = "data", value = "ipca", 2:ncol(dt1))
      dt = rbind(dt, dt1)
    }
  }
  
  
  
  p = ggplot(dt)+
    geom_line(aes(x = as.Date(data), y = as.numeric(ipca)), color = "cyan")+
    ylab("Variação no IPCA (%)") +
    xlab("Período")+
    theme_bw()+
    labs(
      caption = "Fonte: IBGE",
      title = sprintf("Variação nensal do IPCA (%s)", rmet$capital[rmet$codigo == as.character(capital)])
    ) +
    theme(
      plot.caption = element_text(size = 10, color = "blue", face = "italic"),
      plot.title = element_text(hjust = 0.5, face = "italic")
    )
  if(plot == FALSE){
    return(dt)
  }else{
    show(p)
  }
}
```


# Testando a função 

O comando a seguir demonstra um exemplo onde são solicitadas as variações mensais do IPCA na forma de um gráfico de linhas para o Brasil desde janeiro até dezembro de 2024.



``` r
ipca(ano_inicial = 2024, ano_final = 2024, mes_inicial = 1, mes_final = 12, capital = "all", plot = T)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

Em um exemplo complementar, caso o usuário deseje acessar os dados para a região metropolitana de Recife-PE, basta substituir *capital = "all"* por *capital = "2601"* na função, isto é:


``` r
ipca(ano_inicial = 2024, ano_final = 2024, mes_inicial = 1, mes_final = 12, capital = "2601", plot = T)
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

# Considerações finais

A tarefa proposta nesse post pode ser executada de diversas maneiras. A função anteriormente apresentada demonstra apenas um dos vários modos de acessar os resultados do IPCA diretamente da plataforma SIDRA usando a linguagem R. A função possui alguns detalhes que a tornam pouco eficiente em termos de tempo de execução e de escrita do código. Esses detalhes, contudo, podem ser aperfeiçoados e melhorados pelos usuários. Por fim, espera-se que haja utilidade e usuabilidade das informações aqui repassadas no cotidiano dos colegas que acessa a página do NIPE.


<p style="font-family: times, serif; font-size:8pt; font-style:italic">
Nota: Eventuais dúvidas podem ser sanadas por meio de um contato via e-mail com o <a href = "helsongsouza.netlify.app"> Prof. Dr. Helson Gomes </a> atravéz do endereço eletrônico helson.gomes@urca.br
</p>


