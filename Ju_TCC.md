# Resumo

Avaliar diferentes modelos para a de predição de preço de venda de imóveis anunciados em plataformas plataformas online. 
Particularmente, comparar o uso de modelos de regressão linear, indicados como modelo padrão pela ABNT, com modelos de aprendizado de máquina
adicionando textos descritivos dos imóveis nos anúncios e suas imagens. No uso das imagens como preditoras do preço, adota-se uma abordagem
alternativa. No lugar de uso direto das imagens no modelo, com o emprego de redes convolucionais, são detectados e quantificados alguns dos objetos 
presentes na imagens, empregando-se esse vetor de objetos identificados como preditor. 

# Introdução

- Importância do mercado de imóveis em São Paulo e/ou no Brasil e/ou no Mundo (referências). Dados do mercado, % de participação, volume de vendas, emprego.
- Importância e o desafio de se fazer previsões para esse mercado (referências)

- Descritivo do site (sem identificar), justificativa do site escolhido, dados obtidos. 

- Desse modo as contribuições desse trabalho são:
1. Fornece uma grande base de dados aberta de preços de venda de imóveis anunciados em plataformas online, incluindo dados dos imóveis e imagens, para exploração e desenvolvimento de outros modelos na área.
2. Compara diferentes modelos, incluindo modelos de regressão e de aprendizado de máquina, na previsão de preços.  
3. Explora a abordagem de uso de texto dos anúncios e de imagens, a partir de objetos nelas detectados, como variáveis preditoras para os preços.

Fornece, assim, um modelo aplicável de predição de preços, e conhecimentos e dados úteis para análise e contrução de novos modelos.

# Referencial Teórico

- Previsões de preços de imóveis (ou outros) são de grande interesse e vem sendo apicados em inúmeros trabalhos (ver tabela 1). 

- A tabela 1, apresenta alguns dos trabalhos recentes na área.

| Referência | Resumo | Modelos Empregados | Tipo de Dados | Resultados |
|----------------|-----------------|------------------------------------|-|------------------|
| Joao (2022) | Preços de Imóveis (USA), 8000 instâncias | Regressão Linear, XGboost | tabulares | MedAPE = 40.000 |
| Maria, et al. (2023) | Preços de Imóveis (Taiwan), 20000 instâncias | Regressão Linear, RandomForest  | tabulares e texto | - |
| Daniel & Ana (2024) | Preços de Imóveis (China), 1.5M instâncias | Regressão Linear, DeepLearning  | tabulares e imagem | MAPE=0.22 |

> Comente 

- Modelo ABNT...

A exemplo desses estudos, empregam-se aqui tanto modelos lineares como de aprendizado de máquina...
(em cada seção alinhamos o conteúdo com o trabalho!)

## Modelos Lineares (mais ou menos de 1 página)

- Modelos de regressão encontram-se entre os modelos mais empregados e populares em uma série de problemas como na predição de preços vendas, ... (incluir umas 2-3 referências).

- Um modelo de regressão consiste em \<definir, falar de variáveis preditoras e variável alvo\>, algo como:

>> Um modelo linear aproxima o valor de variável objetivo $Y$ a partir de uma combinação linear das variáveis preditoras $X$. 

>> $$ \widehat y = a_0 + a_{1} x_1 + a_{2} x_2 + ... + a_{n} x_n $$
 
>> A cada variável preditora corresponde um coeficiente $a_n$, havendo um coeficiente independente que corresponte ao valor de $\widehat y$ para $X=0$ (*intercept*). Se temos uma única variável preditora $x_1$ nosso modelo é uma reta e temos um modelo de **Regressão Simples**. Se temos mais dimensões temos um *hiperplano* e o modelo é uma **Regressão Múltipla**.

>> https://colab.research.google.com/github/Rogerio-mack/Machine-Learning-I/blob/main/ML2_Regressao.ipynb#scrollTo=qzlZWciD8tOj

Os coeficientes desses modelos são obtidos, em geral, por algum método numérico de minimização do erro $E = y - y_{pred}$.

### Premissas dos Modelos de Regressão Linear e Coeficiente de Determinação

- Discutir brevemente homocedasticidade e R2

- Na prática, em muitos casos, adotam-se modelos lineares sem haver uma concordância plena desses requisitos.

### Transformações de variáveis

- Algo como,... (incluir 1 referência).

>> $$ \ln \widehat y = a_0 + a_{1} ln x_1 + a_{2} x_2 + ... + a_{n} x_n $$

>> Transformações como essas são úteis muita vezes para se reduzir a heterocedasticidade dos dados, o que é particularmente comum no caso de preços.

### Regressão com termos de Interação

- Algo como,... (incluir 1 referência).
 
>> Um conceito importante na análise de regressão é o de termos de interação. Os termos de interação permitem examinar como a relação entre o alvo e a variável independente muda dependendo do valor de outra variável independente.

>> O modelo de regressão linear assume que o efeito de cada característica ou preditor na variável dependente (alvo) é independente de outros preditores no modelo. Por isso escrevemos algo como,

>> $$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \epsilon$$

>> Em um modelo com termos de interação escreveremos algo como:

>> $$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_1 x_2 + \epsilon$$

>> Em que $ x_1 x_2 $ representa a interação entre as duas variáveis preditoras $ x_1$ e $ x_2 $.

>> https://colab.research.google.com/github/Rogerio-mack/IMT_CD_2024/blob/main/IMT_robust_regression.ipynb#scrollTo=nE8vZY40K8nJ

Neste estudo, diferentes modelos de regressão linear são empregados e analisados, incluindo-se modelos com transformações das variáveis e variáveis de interação.
(em cada seção alinhamos o conteúdo com o trabalho!)

## Modelos de Aprendizado de Máquina 

- Modelos de Aprendizado de Máquina vem sendo aplicados com sucesso em uma série de problemas... (referências). 

- Predições de preços podem ser obtidas pelo emprego de modelos de aprendizado de máquina supervisionado... \<definir, dados rotulados, classificadores e regressores, \> (incluir referência).

- Figuras como essas podem ser úteis
> - <img src="https://github.com/Rogerio-mack/Machine-Learning-I/raw/main/Figures/ClassificationRegressionBreastCancer2.png" width=300, align="center">
> - <img src="https://github.com/Rogerio-mack/Machine-Learning-I/raw/main/Figures/ML/Slide4.PNG" width=300, align="center">
> Estão em https://colab.research.google.com/github/Rogerio-mack/Machine-Learning-I/blob/main/ML3_RegressaoLogistica.ipynb, e se precisar do .ppt para regerar é só pedir

- Existem muitos algoritmos de aprendizado de máquina. Cada um deles emprega critérios próprios e diferentes para otimizar os resultados (a redução do erro) e levam, portanto, cada um, a diferentes predições. Alguns desses modelos são avaliados aqui,

-    'Decision Tree' 
-    'Random Forest' 
-    'Ridge Regression'
-    'Lasso Regression'
-    'Gradient Boosting'
-    'K-Nearest Neighbors'

Detalhes sobre cada um desses modelos pode ser encontrado em [referência]. Random Forest e Gradient Boosting, pertencem a uma classe de modelos que empregam média de vários estimadores conjuntos em um classe de modelos [referência].

### Avaliação dos Modelos: Conjuntos de Treinamento e Teste, *Cross Validation*

- No contexto do aprendizado de máquina a seleção dos modelos, em geral, se faz por alguma métrica de erro das predições com relação aos valores reais observados, $y - y{pred}$. Isso pode ser feito separando-se uma parte do conjunto de dados para teste... e as métricas mais empregadas são R2, RMSE, MAE, MedAE, MAPE (ver [referência], para definição e maiores detalhes dessas métricas).

- \<explicar conjuntos de treinamento, teste, validação e cross validation\>, incluir ao menos 1 referência

- Importante destacar que os modelos lineares, e estatísticos em geral, são avaliados mais comumente sobre todo conjunto de dados, pois assume-se *apriori* que o dado se ajusta ao modelo e o erro, medido sobre todo o conjunto de dados representa o ajuste do modelo. No contexto do aprendizado de máquina, por outro lado, diferentes modelos são selecionados a partir do menor erro médio sobre as partições do conjunto de treinamento, que representa o ajuste dos dados ao modelo. Selecionado o melhor modelo, o erro sobre o conjunto de teste, permite avaliar a *generalização* do modelo, e a ausência de sobreajuste (ver [referência]). Assim, diferentes métricas de erro podem ser obtidas, seja sobre o conjunto total dos dados, sobre os dados de validação ou sobre os dados de teste. 



Dentre os diferentes modelos de aprendizado de máquina destacam os modelos *ensemble models*, que são \< definir, explicar, aprendizado híbrido \>. Esses modelos apresentam em geral um desempenho melhor que modelos mais simples. Neste estudo, optou-se pelo uso do modelo XGBOOST, por sua... (referências). 

# Metodologia

Descrevemos a seguir... 

## Pré-processamento dos Dados

Um único dataset de receitas:

| categoria 			| 1     | 2     | 3     | ... | 35   | 36   | 
|----------------------------------|------|------|------|------|------|------|	
| brinquedos 			| 200 | 100 | 50   | ... | 50   | 150 |
| escritório			| 200 | 100 | 50   | ... | 50   | 150 |
| ...  			| ...| ...| ...   | ... | ...   | ... |
| total   			| 200 | 100 | 50   | ... | 50   | 150 |

> Os dados estão muito, muito, desorganizados. Não faz sentido ter tantos arquivos quando, o que você precisa é uma tabela como essa.
> Crie uma tabela no mesmo formato para os produtos x preços e outra para produtos x receita. Essa acima, é a consolidação das duas mais a tabela de categoria dos produtos.

> Comente e justifique: exclusões, tratamento de dados nulos ou ‘zerados’, desafio. NÃO PARECE FAZER SENTIDO, TRATANDO-SE DE RECEITA AGREGADA, EXCLUIR PRODUTOS E SÓ FICAR COM OS 10 MAIS VENDIDOS.

## Análise Exploratória dos Dados

Gráfico de receita total ao longo do tempo
Gráfico de algumas categorias 
> Comente: sazonalidade, variações, maiores e menores, padrões de comportamento mensal, desafio de fazer as previsões etc.

Para cada série aplique a o teste adfuller sobre estacionariedade

| categoria 			| estacionariedade   | p-value | 
|----------------------------------|---------------------------|-----------|	
| brinquedos 			| estacionária | 0.01 |
| escritório			| estacionária | 0.04 |
| ...   			| ... | ... |
| total   			| estacionária | 0.05 |

> Comente

### ACF (Função de Autocorrelação) 
É utilizada para identificar a presença de sazonalidade em uma série temporal.
Gráfico das 15 categorias+total, 

| categoria 			| sazonalidade  |   
|----------------------------------|---------------------------| 	
| brinquedos 			| 12  |  
| escritório			| 12 |  
| limpeza			|  0  |  
| ...   			| ... | 
| total   			| 12 |  

0 = produtos de ano inteiro

> Comente
 
### PACF (Função de Autocorrelação Parcial) 
É empregada para identificar a ordem do componente autoregressivo (p) em um modelo ARIMA.
Gráfico das 15 categorias+total

| categoria 			| sazonalidade  |   
|----------------------------------|---------------------------| 	
| brinquedos 			| 1  |  
| escritório			| 2 |  
| limpeza			| 1 |  
| ... | ... |
| total   			| 3 |  

> Comente

### Métricas 

A seleção dos modelos estatísticos emprega a métrica AIC (referência), tradicional para seleção do melhor ajuste de modelos estatísticos e implementada pode padrão no pmdarima. Para avaliação dos resultados são empregadas as métricas de erro RMSE ( ), MAE ( ), MAPE ( ) e MedAE (Median Absolute error). O RMSE é empregado para comparar os modelos. As demais métricas são empregadas ao final para o entendimento do erro das previsões.

### Rolling Window

Utiliza-se aqui uma janela deslizante (rolling window) para dividir seus dados em conjuntos de treinamento e teste. Emprega-se a receita total para estimar o uso de previsões com base em 30 ou 36 meses. Busca-se empregar a maior quantidade de dados (36 meses), mas essa, pela limitação dos dados disponíveis, não permite a previsão de 12 meses.

Execuções pmdarima sobre receita total
```
  pmdarima 30 -> 1 (x 12 execuções) -> média AIC, média RMSE 
  pmdarima 36 -> 1 (x 6 execuções) -> média AIC, média RMSE
```

Mostrar a diferença, mas apesar do erro, vamos empregar 30 -> 1

### Pmdarima, SARIMA

O pmdarima otimiza somente os parâmetros A(p, q, d). Para os parâmetros S(p, q, d) emprega-se os valores obtidos de... (veja a analise que fez antes do ACF, espera-se empregar 0, aí é sazonal False, ou 12, com sazonal True).      Os valores A(p, q, d) são otimizados então entre... (ver os valores que emprega... padrão?, o PACF pode dar uma dica melhor e você pode empregar menos valores)

Pode justificar isso?
error_action='ignore',  # Ignora erros em combinações inválidas
suppress_warnings=True  # Suprime avisos

Execuções pmdarima sobre receita total e categorias
```
  Para cada categoria (inclui a total):
  	pmdarima 30 -> 1 (x 12 execuções) -> melhor modelo A(p,q,d) S(p,q,d)
```

Modelo escolhido, isso é mostrado nos resultados.  
Empregar A(p,q,d) S(p,q,d) 

| categoria 			| modelo  |   freq. |
|----------------------------------|---------------------------|------| 	
| brinquedos 			| A(1,1,0) S(0,12,0)  |  12 |
| escritório			| A(1,2,1) S(0,12,0) |  7 |
| limpeza			| A(1,2,1) S(0,0,0) |  9 |
| ...| ... |...|
| total   			| A(1,2,0) S(0,0,0) |  8 | 

> Comente
Salve em um dicionário ou em um dataframe, parm_SARIMA[‘categoria’] -> A(1,2,0) S(0,0,0)

> Comente
Salve em um dicionário ou em um dataframe, parm_SARIMA[‘categoria’] -> A(1,2,0) S(0,0,0)

Execuções SARIMA (não é o pmdarima, ou se é o modelo é fixo) sobre receita total e categorias
Para cada categoria (inclui a total):
	SARIMA ou pdmaria com parm_SARIMA[‘categoria’]: 30 -> 1 (x 12 execuções) -> RMSE
	SARIMA ou pdmaria com parm_SARIMA[‘categoria’]: 30 -> 1 (x 9 execuções) -> RMSE

Resultados, isso é mostrado nos resultados.  

SARIMA -> 1m

| categoria 			| 1  | 2 | ... | 12 | Média |  
|-----------------|-----|----|-----|-----|-----------| 
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse | 
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  

SARIMA -> 3m

| categoria 			| 1  | 2 | ... | 9 | Média |  
|-----------------|-----|----|-----|-----|-----------|
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse |  
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  


### XGBOOST

Para a construção das lags (os valores defasados), empregam-se 12 valores passados com base na sazonalidade da maior parte dos produtos (recomendo avaliar com 6 também). Os mesmos procedimentos e previsões empregados nos modelos SARIMA são então aplicados. Outros parâmetros do XGBOOST? Verifique se não tem melhores resultados com 200, 500 ou 1000 estimadores.

Execuções XGBOOST sobre receita total e categorias
Para cada categoria (inclui a total):
	XGBOOST: 30 -> 1 (x 12 execuções) -> RMSE

Resultados, isso é mostrado nos resultados.  

XGBOOST -> 1m

| categoria 			| 1  | 2 | ... | 12 | Média |  
|-----------------|-----|----|-----|-----|-----------| 
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse | 
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  

XGBOOST -> 3m

| categoria 			| 1  | 2 | ... | 9 | Média |  
|-----------------|-----|----|-----|-----|-----------|
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse |  
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  


### Escolha dos melhores modelos

Os dados do RMSE dos modelos são então empregados para seleção dos melhores modelos para previsões de 1 ou 3 meses. 

### Diagrama

Para concluir, crie um diagrama com todo o fluxo e fases dessa metodologia.

# Resultados

Bla bla bla..

**SARIMA**
SARIMA -> 1m

| categoria 			| 1  | 2 | ... | 12 | Média |  
|-----------------|-----|----|-----|-----|-----------| 
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse | 
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  

SARIMA -> 3m

| categoria 			| 1  | 2 | ... | 9 | Média |  
|-----------------|-----|----|-----|-----|-----------|
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse |  
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  


> Comente 

**XGBOOST**
XGBOOST -> 1m

| categoria 			| 1  | 2 | ... | 12 | Média |  
|-----------------|-----|----|-----|-----|-----------| 
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse | 
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  

XGBOOST -> 3m

| categoria 			| 1  | 2 | ... | 9 | Média |  
|-----------------|-----|----|-----|-----|-----------|
| brinquedos 			|rmse|rmse| ... |  rmse | rmse | 
| escritório			| rmse  | rmse  | ... |  rmse | rmse |  
| limpeza			| rmse  | rmse  | ... |  rmse | rmse |  
|||| ... ||| 
| total   			| rmse  | rmse  | ... |  rmse | rmse |  

## Melhores Modelos 

|                         |   SARIMA   | SARIMA |  XGBOOST |  XGBOOST |   |
|-|-|-| - |-|-|
| categoria 			| **1m**  |  **3m** | **1m**  |  **3m** |  Melhor |
|-|-|-| - |-|-|
| brinquedos 			| **rmse**  | **rmse**  |  rmse | rmse | **SARIMA** |
| escritório			| **rmse**  | **rmse**  |  rmse | rmse | **SARIMA** |
| limpeza		|  rmse | rmse |   **rmse**  | **rmse** | **XGBOOST** |
|-|-|-| - |-|-|
| total   			| **rmse**  | **rmse**  |  rmse | rmse | **SARIMA** |

## Visualização dos Resultados

Somente para os melhores modelos 3 meses de forecast, incluir nos gráficos as outras métricas.

> Comentar,
Que categorias apresentam bons modelos  
Que categorias apresentam maus modelos, por que?
Discuta as métricas dos resultados, MAPE, MAE, MedAE (qual a implicação prática, é o % de erro ou erro médio).

# Conclusão 
Aplicabilidade, importância
Trabalhos futuros: análises complementares como a análise de erros dos modelos, aplicação de outros modelos de ML como modelos de redes neurais e transformers.

# Referências

[1] Marzagão, T., Ferreira, R., & Sales, L. (2021). A note on real estate appraisal in Brazil. Revista Brasileira de Economia, 75(1), 29-36.

[2] Poursaeed, O., Matera, T., & Belongie, S. (2018). Vision-based real estate price estimation. Machine Vision and Applications, 29(4), 667-676.

(...)

