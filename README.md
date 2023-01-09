# Conhecendo o negócio

Criada em 1972, a Rossmann é uma rede de drogaria Alemã que atua em 8 países na Europa, conta com mais de 4 mil lojas e com mais de 56 mil colaboradores.

A empresa disponibilizou 1.027.209 registros de vendas de suas lojas na plataforma de competições do Kaggle, no qual, cada registro contém 18 atributos únicos.

# 1.	O problema de negócio
  O CFO da empresa fez uma reunião com todos os gerentes de loja e pediu para que cada um deles trouxessem uma previsão das próximas 6 semanas de vendas para que parte desse valor fosse designado na reformar as lojas da rede.
  
  Atualmente, esses valores são calculados de forma individual, sendo que cada gerente realiza a entrega dessa previsão. Como cada loja possui fatores distintos que influenciam em seus resultados, como promoções, competições por clientes, feriados, sazonalidade e etc, e os cálculos são feitos de forma manual, os resultados variam muito.
  
  Portanto, a ideia desse projeto é auxiliar o CFO na tomada de decisão, fornecendo a previsão de vendas individual de cada loja de forma automática, para que essa consulta possa ser realizada rapidamente através de um celular por um Bot no aplicativo Telegram.


# 2.	Premissas assumidas para a análise
Para a construção desse projeto foi considerado as seguintes premissas:
  1. Os dias em que as lojas estavam fechadas foram descartados na análise.
  2. Somente foi considerado para a previsão, lojas com vendas superior a 0.
  3. Lojas que não possuiam dados de competidores próximos foi considerado uma distância fixa de 200.000 metros.
  
## 2.1. Descrição dos dados:
| Atributo    | Descrição |
|:---------   |----------:|
| Store       | Identificador único para cada loja |
| Date        | Date em que ocorreu a venda |
| DateOfWeek  | dia da semana em que ocorreu a venda |
| Sales       | Valor de vendas no dia |
| Custumers   | Quantidade de clientes na loja no dia |
| Open        | Indicador se a loja está aberta = 1 ou fechada = 0 |
| StateHoliday  | Indica se é feriado estadual no dia.  a = Feriado público, b = Feriado de páscoa, c = Natal, 0 = Não há feriado |
| SchoolHoliday | Indica se a loja foi ou não fechada durante o feriado escolar |
| StoreType     | Indica o tipo de loja. Pode variar entre a, b, c, d|
| Assortment    | Indica o nível de variedade de produtos da loja: a = básico, b = extra, c = estendido |
| CompetitionDistance               | Distância em metros da loja competidora mais próxima |
| CompetitionOpenSince[Month/Year]  | Indica o ano e mês que o competidor mais próximo abriu |
| Promo         | Indica se a loja está com alguma promoção ativa no dia |
| Promo2        | Indica se a loja deu continuidade na promoção: 0 = não continuou, 1 = continuou |
| Promo2Since[Year/Week]   | Indica o ano e semana de quando a loja começa a promoção extendida |
| PromoInterval | Descreve os meses em que a loja iniciou a promo2, ex.: "Feb,May,Aug,Nov" significa que a loja iniciou as promoções estendidas em cada um desses meses |

# 3.	Estratégia da solução
  1. Coletar os dados no kaggle
  2. 



# 4.	Top 4 Insiths de dados

  1. 

  2. 

  3. 

  4. 

# 5.	O produto final do projeto




# 6.	Conclusão



# 7.	Próximos Passos
  1.	
  2.	
