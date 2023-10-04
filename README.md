# Projeto 12
# Projeto Rusty Bargain - Previsão de Preços de Carros Usados

![car]([https://images.unsplash.com/photo-1560807707-8cc77767d783](https://www.google.com/url?sa=i&url=https%3A%2F%2Fnewsrondonia.com.br%2Fnoticias%2F2023%2F02%2F24%2Fipva-do-carro-aumentando-entenda%2F&psig=AOvVaw0BJJHZNo1BVXeE_-jC3RtD&ust=1696540086119000&source=images&cd=vfe&opi=89978449&ved=0CBEQjRxqFwoTCMCYhrum3YEDFQAAAAAdAAAAABAE))

O serviço de vendas de carros usados Rusty Bargain está desenvolvendo um aplicativo para atrair novos clientes. Nesse aplicativo, os usuários podem descobrir rapidamente o valor de mercado de seus carros usados. O objetivo deste projeto é construir um modelo de aprendizado de máquina que determine o valor dos carros com base em dados históricos, especificações técnicas, versões de acabamento e preços.

## Preparação de Dados

A preparação de dados é uma etapa crítica em qualquer projeto de aprendizado de máquina. Nesta seção, realizamos as seguintes tarefas:

1. Importação de Bibliotecas: Importamos as bibliotecas necessárias, como pandas, matplotlib e scikit-learn.

2. Leitura do Conjunto de Dados: Carregamos os dados a partir do arquivo `car_data.csv` ou do caminho `/datasets/car_data.csv`, garantindo que os dados estejam disponíveis para análise e modelagem.

3. Visualização Inicial do Conjunto de Dados: Exibimos as primeiras linhas do conjunto de dados para entender sua estrutura.

4. Informações Gerais sobre o Conjunto de Dados: Verificamos informações como número de entradas, colunas e tipos de dados para entender a qualidade dos dados.

5. Verificação de Valores Nulos: Calculamos a porcentagem de valores nulos em cada coluna para identificar a necessidade de tratamento.

6. Conversão de Colunas de Data: Convertemos as colunas de data para o formato apropriado.

7. Tratamento de Valores Nulos: Preenchemos valores nulos nas colunas `NotRepaired` e `Model` com "unknown" e "other", respectivamente.

8. Análise da Coluna `RegistrationYear`: Filtramos anos de registro dentro de um intervalo razoável.

9. Análise da Coluna `Price`: Removemos valores iguais ou menores a zero, pois preços não positivos não fazem sentido.

10. Análise da Coluna `Power`: Identificamos outliers e removemos valores discrepantes.

11. Imputação de Valores Ausentes: Imputamos valores ausentes nas colunas categóricas `FuelType`, `Gearbox` e `VehicleType` com base no valor mais comum no grupo `Model`.

12. Remoção da Coluna `NumberOfPictures`: Removemos a coluna `NumberOfPictures` porque todos os valores eram zero, não contribuindo para análises futuras.

13. Remoção de Duplicatas: Identificamos e removemos duplicatas do conjunto de dados.

14. Criação da Coluna `UserDays`: Criamos uma nova coluna `UserDays` para representar o número de dias entre `LastSeen` e `DateCreated`.

## Treinamento do Modelo

Nesta seção, treinamos diferentes modelos de machine learning e avaliamos seu desempenho. Os modelos considerados incluem:

- Regressão Linear
- Árvore de Decisão
- Floresta Aleatória
- CatBoost
- LGBM

Para cada modelo, realizamos as seguintes etapas:

1. Divisão dos Dados: Dividimos o conjunto de dados em conjuntos de treinamento, validação e teste.

2. Pré-processamento: Realizamos a codificação de características categóricas usando uma combinação de técnicas, como One-Hot Encoding e Label Encoding. Além disso, normalizamos as características numéricas.

3. Treinamento do Modelo: Treinamos o modelo com os conjuntos de treinamento e validação.

4. Avaliação do Modelo: Avaliamos o desempenho do modelo usando a métrica REQM (Root Mean Squared Error).

## Análise do Modelo

Após treinar e avaliar vários modelos, chegamos a conclusões importantes:

- O **CatBoostRegressor** e o **LGBMRegressor** se destacam como os dois melhores modelos em termos de precisão (RMSE) e eficiência de treinamento e predição.
- O **LGBMRegressor** apresenta um equilíbrio sólido entre precisão e eficiência, com um RMSE de aproximadamente 1615.35 e tempos de treinamento e predição rápidos.
- O **CatBoostRegressor** oferece precisão semelhante, mas com um tempo de treinamento mais longo.

Portanto, recomendamos o uso do **LGBMRegressor** como modelo final, pois oferece uma boa combinação de desempenho e eficiência.
