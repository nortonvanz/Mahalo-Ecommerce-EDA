# Mahalo E-Commerce EDA

<img src="https://github.com/nortonvanz/Mahalo-Ecommerce-EDA/blob/main/images/ecommerce.jpg?raw=true" width=70% height=70% title="Mahalo-Ecommerce-EDA" alt="project_cover_image"/>

Projeto de Insights a partir dos dados de vendas uma empresa de e-commerce, chamada Mahalo Holding.

Contextualização: A Mahalo Holding é uma empresa de e-commerce que atuou entre 2019 e 2022 no varejo brasileiro. Teve como modelo de negócios a venda de produtos diversos através da internet, por meio de marketplaces.

Os dados do projeto foram obtidos do Google Sheets, onde a gestão das vendas era realizada, como um complemento aos processos de ERP.

O contexto de negócios é real, bem como seu planejamento e desenvolvimento.

## 1. Problema de negócios
### 1.1 Problema
Após o encerramento das atividades da empresa, seus sócios desejam validar alguma crenças sobre o negócio, bem como obter respostas para alguma questões através dos dados.

Com isto, buscam ter uma melhor visão do negócio, e extrair lições aprendidas valiosas para aplicação em futuros empreendimentos.

### 1.2 Objetivo
Realizar uma análise exploratória nos dados de vendas da empresa de comércio eletrônico Mahalo, validando algumas hipóteses e respondendo algumas questões de negócio elaboradas pelos sócios.

Hipóteses para validar:
- H1 - Em média, os produtos mais caros foram vendidos para a região sul.
- H2 - Proporcionalmente, o estado do Rio Grande do Sul compra mais do fornecedor Carlu que os demais.
- H3 - O Lucro dos produtos vendidos no estado do Paraná foi maior, em média, que nos demais estados.
- H4 - Mais de 50% das vendas ocorreram nos finais de semana.

Questões para responder:
- Q1 - Os produtos de diferentes preços venderam de forma homogênea nos diversos marketplaces?
- Q2 - Qual marketplace vendeu os produtos de maior valor?
- Q3 - Qual foi o número de vendas por fornecedor em cada marketplace?
- Q4 - Qual fornecedor mais vendeu para cada região do Brasil?
- Q5 - Qual marketplace mais vendeu para cada região do Brasil?
- Q6 - Qual foi o lucro médio por fornecedor?
- Q8 - Qual foi o faturamento por trimeste? E por mês?
- Q9 - Qual foi o lucro por trimeste? E por mês?

## 2. Premissas de negócio
- Os dados da planilha do Google Sheets não estão todos tratados, logo deve haver um trabalho de limpeza e padronização nestes dados.
- Antes da utilização dos dados, por questões de privacidade, os nomes dos clientes devem ser todos anonimizados.
- Os sócios tem ciência que pelo fato da gestão de custos ser realizada via ERP, e este projeto utilizar apenas os dados de vendas, aqui não estão sendo considerados todos os custos da operação, apenas os envolvidos nas vendas.  

As variáveis do dataset são:

Variável | Definição
------------ | -------------
 | data_compra | data de emissão da NFE de compra dos produtos |
 | sku | código SKU do produto, sendo SKU seu código de controle de estoque |
 | produto | nome do produto |
 | fornecedor | nome do fornecedor |
 | custo_bruto | composto pelo custo_bruto_nfe + frete SIF (pago pelo comprador) rateado pelos produtos, quando aplicável + valor de impostos IPI e ST |
 | comissoes_mktplace | comissões pagas aos marketplaces para venda dos produtos |
 | frete | custos com fretes para envio dos produtos, quando zerado, está imbutido na comissão |
 | preco_venda | preço pelo qual o produto foi vendido |
 | lucro_venda | lucro ou prejuízo (se valor negativo), obtido na venda do produto |
 | dias_estoque | número de dias que o produto ficou em estoque |
 | data_venda | data da venda do produto |
 | marketplace_venda | marketplaces no qual o produto foi vendido, exceto quando valor for "entrega em mãos" |
 | cliente | nome do cliente anonimizado |
 | localizacao | UF do cliente |


## 3. Planejamento da solução
### 3.1. Produto final
O que será entregue efetivamente?
- Relatório exibindo o comportamento geral dos dados na ferramenta de visualização Sweetviz. Será apresentado via nagador Chrome.
- Validação das hipóteses e resposta às questões de negócio dentro do jupyter notebook. Será apresentado no próprio jupyter notebook.

### 3.2. Ferramentas
Quais ferramentas serão usadas no processo?
- Python 3.8.12;
- Jupyter Notebook;
- Git e Github;
- Pandas, Matplotlib e Seaborn;
- SweetViz;
- Hashlib;

### 3.3 Processo
#### 3.3.1 Estratégia de solução
Com base no objetivo já descrito, trata-se de um projeto de Insights.

Minha estratégia para resolver esse desafio, baseado na metodologia CRISP-DS, é detalhada pelo plano abaixo:

1. Compreender o problema de negócios;
2. Coletar os dados do Google Sheets e anonimizar os sensíveis;
3. Realizar a limpeza e padronização dos dados;
4. Aplicar estatística descritiva;
5. Criar as novas features necessárias para realizar a EDA;
6. Iniciar a análise exploratória de dados com Sweetviz;
7. Seguir a EDA validando as 4 hipóteses, e respondendo as 9 questões de negócio.
8. Apresentar resultados aos sócios, compartilhando os insights e lições aprendidas.

## 4. Os 3 principais insights dos dados
Durante a análise exploratória de dados, foram gerados insights ao time de negócio, através da validação das hipóteses.

Insights são informações novas, ou que contrapõe crenças até então estabelecidas. São também acionáveis, possibilitando ação para direcionar resultados futuros.

#### H1 - Em média, os produtos mais caros foram vendidos para a região sul.

Hipótese falsa: Em média, foram vendidos mais produtos caros para a região Norte. Das 5 regiões, a sul fica em quarto em termos de produtos mais caros vendidos, na média.

* Insight de negócio: Realizar promoções/marketing direcionado às regiões norte, nordeste e centro oeste pode ajudar a aumentar o ticket médio nestas regiões, aumentando a representatividade delas na proporção das vendas.

#### H3 - O Lucro dos produtos vendidos no estado do Paraná foi maior, em média, que nos demais estados.

Hipótese falsa: O Lucro dos produtos vendidos no PR foi o menor entre todos os estados.

* Insight de negócio: Rever a política da empresa de desconto aos sócios na aquisição de produtos, visto que são do PR, e possivelmente parte deste resultado é devido a ela.

#### H4 - Mais de 50% das vendas ocorreram nos finais de semana.

Hipótese falsa: Mais de 95% das vendas ocorreram nos dias de semana.

* Insight de negócio: Obter dados de pedidos de vendas concretizados do ERP, e cruzar as datas de venda com estes dados, visando avaliar se houveram erros operacionais de lançamentos nas vendas da planilha, visto que o resultado contraria bastante a percepção da realidade da operação.
Muito provavelmente, por não haver entregas nos sábados e domingos, parte das vendas nestes dias foram lançadas na planilha como sendo realizadas na segunda-feira.

## 5. Conclusões
Foram validadas as hipóteses dos sócios da empresa, e respondidas as suas questões de negócio.
A partir disso, poderão ter uma visão mais assertiva do business, e extrair lições aprendidas valiosas para futuros empreendimentos.

## 6. Melhorias futuras
- Realizar as análises considerando antes e depois do período de liquidação dos produtos para o fechamento da empresa.
- Utilizar ferramenta de visualização de mercado como Power BI ou Tableau para a exibição dos resultados.

## 7 Referências
* O Dataset é de propriedade do autor do projeto.
* A imagem utilizada é de uso livre e foi obtida no [Pexels](https://www.pexels.com/pt-br/foto/comercio-eletronico-ecommerce-e-commerce-compras-online-6667686/).
