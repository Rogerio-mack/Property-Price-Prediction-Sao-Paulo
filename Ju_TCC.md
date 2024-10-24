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

- Importante destacar que os modelos lineares, e estatísticos em geral, são avaliados mais comumente sobre todo conjunto de dados, pois assume-se *apriori* que o dado se ajusta ao modelo e o erro, medido sobre todo o conjunto de dados representa o ajuste do modelo. No contexto do aprendizado de máquina, por outro lado, diferentes modelos são selecionados a partir do menor erro médio sobre as partições do conjunto de treinamento, que representa o ajuste dos dados ao modelo. Selecionado o melhor modelo, o erro sobre o conjunto de teste, permite avaliar a *generalização* do modelo, e a ausência de sobreajuste (ver [referência]). Assim, diferentes métricas de erro podem ser obtidas, seja sobre o conjunto total dos dados, sobre os dados de validação ou sobre os dados de teste. Aqui, sendo de interesse o modelo que melhor se ajusta aos dados e por concisão, são apresentadas as métricas de erro sobre todo o conjunto de dados. Todas as métricas, sobre dados de teste e de validação, entretanto, podem ser consultadas em detalhe em [referência do GitHub do projeto], e foram consideradas ao longo da análise para a seleção de modelos sem sobreajuste (por exemplo, o modelo de Árvore de Decisão, embora apresente o menor erro de treinamento, é sobreajustado, e é descartado nos resultados aqui). 

# Metodologia

## Dados

- Descrição sumária dos dados... por que esses dados, compatível em quantidade com outros trabalhos, etc.

## *Scraping*, coleta dos dados

- Discuta os pontos principais, os desafios, por que não outros sites, pode incluir o número aproximado de horas... Não fornecer o código, apenas um pseudo, ou esquemático.

## Yolo, Detecção dos Objetos nas Imagens

- Explicar, incluir o código no GitHub

## **DAQUI EM DIANTE É MAIS OU MENOS O QUE ESTÁ NO README DO GITHUB...**

## Pre process... 
- Isso tem lá no GitHub, mas vamos suprimir... apenas comente na Seção seguinte. A ideia é preservar o anonimato do site.

Anonymize data (extract URL information)

Rename files field names

## Preparação dos Dados

# Resultados

## Análise Exploratória do Dados

- Isso não tem no readme, mas estão nos notebooks alguns highlights importantes

## Modelos de Regressão Linear 

## Seleção dos Modelos de Aprendizado de Máquina 

## Aplicação dos Modelos de Aprendizado: dados numéricos, texto e imagem

### Dados numéricos

### Dados numéricos e vetor de objetos das imagens

### Dados numéricos e texto descritivo dos anúncios 

### Dados numéricos, texto descritivo dos anúncios e vetor de objetos das imagens

# Conclusão

...

Uma nota sobre a disponibilidade dos dados (Kaggle, DOI) e fontes (GitHub, organização), incluindo aqui os links, incluindo também nas referências.

# Referências

[1] Marzagão, T., Ferreira, R., & Sales, L. (2021). A note on real estate appraisal in Brazil. Revista Brasileira de Economia, 75(1), 29-36.

[2] Poursaeed, O., Matera, T., & Belongie, S. (2018). Vision-based real estate price estimation. Machine Vision and Applications, 29(4), 667-676.

(...)

