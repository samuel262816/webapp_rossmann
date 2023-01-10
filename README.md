<img src= 'https://github.com/samuel262816/webapp_rossmann/blob/main/img/logo_rossmann.png' width= 900 height= 180>

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
|:---------   |:----------|
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
Foi utilizado o método CRISP-DS para seguir o passo a passo e entregar uma primeira solução do problema de forma mais rápida ao CFO.

O método CRISP-DS segue 9 passos cíclicos, no qual, a cada ciclo completo o projeto vai se aperfeiçoando. A utilização desse método permite que já na primeira iteração do ciclo, seja possível ter uma versão do projeto minimamente utilizável para que o mesmo seja aperfeiçoado ao longo do tempo.

<img src= 'https://github.com/samuel262816/webapp_rossmann/blob/main/img/ciclo_crisp2.PNG'>

## 3.1 Etapas do método CRISP-DS

  **1. Problema de Negócio:** Receber o problema de negócio a ser resolvido.
  
  **2. Entendimento do Negócio:** Entender qual a real queixa e necessidade do dono do problema.
  
  **3. Coletar os Dados:** Coletar os dados nos bancos de dados da empresa. Nesse projeto, os dados foram coletados na plataforma do Kaggle.
  
  **4. Limpeza dos Dados:** Realizar a limpeza dos dados, retirar caracteres especiais, verificar se o tipo dos dados estão corretos.
  
  **5. Exploração dos Dados:** Entender quais variáveis influenciam na variável resposta e também criar novas variáveis que serão utilizadas na modelagem dos dados. Nesse projeto, será avaliado quais variáveis mais impactam nas vendas. Nessa etapa também são criadas várias hipóteses de negócio que serão validadas com técnicas de análise dos dados.
  
  **6. Modelagem dos Dados:** Preparar os dados para receber os modelos de Machine Learning. Separar os dados em treino e teste, e realizar os _encoding_ dos dados para facilitar o aprendizado dos algoritmos utilizados.
  
  **7. Algoritmos de Machine Learning:** Aplicar os algotimos de Machine Learning dos dados preparados anteriormente.
  
  **8. Avaliação dos Algoritmos:** Verificar a performance dos algoritmos, comparando-os entre eles e selecionando o melhor algorítmo. Caso a performance esteja minimamente utilizável, poderá seguir para publicação do modelo em produção. Caso não esteja, é necessário voltar à etapa de entendimento do negócio e passar por um novo ciclo do CRISP-DS até atingir a performance desejada.
  
  **9. Modelo em Produção:** Publicar o modelo em produção para que a solução seja utilizado pelos donos do problema.
  
## 3.2 Ferramentas Utilizadas
Para criar a solução foram utilizadas as seguintes ferramentas:
 - Linguagem de Programação Python 3.9.13
 - Jupyter Notebook para prototipar a solução
 - VSCode para implementação da solução
 - Técnicas de manipulação de dados com Python
 - Técnicas de redução de dimensionalidade e seleção de atributos
 - Algoritmos de Machile Learning da biblioteca scikit-learnig em Python
 - Versionador de código Git
 - Hospedagem em Nuvem Render 


# 4.	Top 3 Insiths de dados

  ## Insight 1: Lojas com maior sortimento deveriam vender mais.
**Hipótese Falsa:** Lojas com maior sortimento vendem menos em comparação às de menor sortimento.

<img src= 'https://github.com/samuel262816/webapp_rossmann/blob/main/img/hipotese1.PNG'>

  ## Insight 2: Lojas com competidores mais próximos deveriam vender menos.
**Hipótese Falsa:** Lojas com competidores próximos vendem mais.

<img src= 'https://github.com/samuel262816/webapp_rossmann/blob/main/img/hipotese2.PNG'>

  ## Insight 3: Lojas abertas durante feriado de Natal vendem mais.
**Hipótese Falsa:** Lojas abertas no Natal vendem menos em comparação aos outros feriados.

<img src= 'https://github.com/samuel262816/webapp_rossmann/blob/main/img/hipotese3.PNG'>


# 5.	O produto final do projeto
Foi combinado com o CFO que seria entregue um Bot no aplicativo Telegram, no qual o usuário digitará o código da loja e o Bot retornará a previsão de vendas das próximas 6 semanas da loja solicitada.

Além disso, será criado uma API que utilizará o modelo de machine learning desenvolvido para retornar as previsões de venda das lojas. 
 

# 6.	Modelos de Machine Learning


## 6.1 Seleção dos Modelos
 
 
# 7.	Resultado de Negócio
 
 
 
# 8.	Conclusões


# 9.	Lições Aprendidadas



# 10.	Próximos Passos
  1.	
  2.	
