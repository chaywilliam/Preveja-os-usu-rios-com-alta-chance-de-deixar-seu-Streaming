# Preveja-os-usuarios-com-alta-chance-de-deixar-seu-Streaming

## Repositório de Análise Exploratória e Modelagem de Dados de Streaming
Este repositório contém um script Python para análise exploratória e modelagem preditiva de dados de streaming. O objetivo principal é prever a rotatividade de clientes (Churn) usando Regressão Logística e Random Forest.

## Descrição do Projeto
O arquivo streaming_data.csv contém dados sobre usuários de um serviço de streaming, incluindo informações demográficas, tempo de uso, tipo de assinatura, número de serviços de streaming, número de perfis ativos, avaliação média e se o cliente cancelou ou não a assinatura (Churn).

## O script Python realiza as seguintes etapas:

### 1.Análise Exploratória dos Dados (Data Understanding): Carrega os dados, exibe estatísticas descritivas, informações sobre os dados e verifica valores ausentes.
### 2.Tratamento dos Dados (Data Preparation): Limpa e pré-processa os dados, tratando valores ausentes, removendo linhas com valores nulos e convertendo variáveis categóricas para numéricas.
Modelagem:
### * Regressão Logística: Cria e treina um modelo de Regressão Logística para prever a rotatividade de clientes.
### * Random Forest: Realiza o tuning de hiperparâmetros para um modelo Random Forest usando GridSearchCV.

## Estrutura do Repositório
.
├── README.md
└── streaming_data_analysis.ipynb

## Como Executar o Código
### 1.Clone este repositório:

Bash

git clone https://github.com/seu-usuario/nome-do-repositorio.git

### 2.Instale as dependências:

Bash

pip install pandas numpy scikit-learn

### 3.Execute o notebook Jupyter:

Bash

jupyter notebook streaming_data_analysis.ipynb

# Análise Exploratória dos Dados (Data Understanding)
O script começa carregando os dados do arquivo CSV usando a biblioteca Pandas:

Python

import pandas as pd
df = pd.read_csv('/content/streaming_data.csv')
print(df.head())
Em seguida, são exibidas estatísticas descritivas das variáveis numéricas usando df.describe(), informações sobre o tipo de dados e valores ausentes em cada coluna usando df.info() e a quantidade de valores ausentes em cada coluna usando df.isna().sum().

# Tratamento dos Dados (Data Preparation)
Os dados são tratados para lidar com valores ausentes e variáveis categóricas:

### 1.Valores Ausentes: Valores NaN em colunas específicas são substituídos por 0.

Python

df = df.fillna({'Subscription_type': 0, 'Num_streaming_services': 0, 'Churned': 0, 'Avg_rating': 0, 'Devices_connected': 0})

### 2.Remoção de Linhas Nulas: Linhas com valores ausentes em colunas específicas são removidas.

Python

df.dropna(subset=['Gender', 'Subscription_type', 'Age'], inplace=True)

#### 3.Conversão de Churned: A coluna Churned é convertida de numérica para categórica.

Python

df['Churned'] = df['Churned'].replace({0: 'No', 1: 'Yes'})

### 4.Codificação de Subscription_type: A coluna Subscription_type é convertida de categórica para numérica.

Python

subscription_mapping = {'Basic': 1, 'Standard': 2, 'Premium': 3}
df['Subscription_type'] = df['Subscription_type'].map(subscription_mapping).fillna(0).astype(int)
df = df.astype({'Num_streaming_services': 'int'})

# Modelagem
## Regressão Logística
### 1.Definição de X e y: As variáveis preditoras (X) e a variável alvo (y) são definidas.
### 2.Codificação de Variáveis Categóricas: As variáveis categóricas em X são codificadas usando one-hot encoding.
### 3.Divisão em Treino e Teste: Os dados são divididos em conjuntos de treino e teste.
### 4.Escalonamento: As variáveis numéricas são escalonadas usando MinMaxScaler().
### 5.Tratamento de Valores Infinitos e NaN: Valores infinitos e NaN são tratados em X_train e X_test.
### 6.Treinamento do Modelo: Um modelo de Regressão Logística é treinado nos dados de treino.
### 7.Previsões: Previsões são feitas nos dados de teste.
### 8.Matriz de Confusão: A matriz de confusão é exibida para avaliar o desempenho do modelo.

## Tunning (Random Forest com GridSearchCV)
### 1.Definição da Grade de Hiperparâmetros: Uma grade de hiperparâmetros a serem testados é definida.
### 2.Inicialização do Modelo e GridSearchCV: Um modelo RandomForestClassifier e um objeto GridSearchCV são inicializados.
### 3.Tratamento de NaN em X_train: Valores NaN são tratados em X_train para garantir que o GridSearchCV funcione corretamente.
### 4.Imputação de NaN: Valores NaN são imputados em X_train usando SimpleImputer.
### 5.Treinamento do GridSearchCV: O GridSearchCV é treinado nos dados de treino.
### 6.Melhores Parâmetros: Os melhores parâmetros encontrados pelo GridSearchCV são exibidos.
### 7.Previsões: Previsões são feitas com o melhor modelo.
### 8.Matriz de Confusão: A matriz de confusão é exibida para avaliar o desempenho do modelo.

# Resultados
Os resultados da modelagem são exibidos através da matriz de confusão, que permite avaliar o desempenho dos modelos de Regressão Logística e Random Forest na previsão da rotatividade de clientes.

# Próximos Passos
* Explorar outros modelos de classificação.
* Realizar uma análise mais aprofundada dos dados para identificar padrões e insights relevantes.
* Implementar técnicas de Feature Engineering para melhorar o desempenho dos modelos.

Este README fornece uma visão geral do projeto e como executar o código. 
Sinta-se à vontade para explorar o notebook Jupyter para obter mais detalhes sobre a implementação e os resultados da análise.

# Charles William
c_wasouza@outlook.com
