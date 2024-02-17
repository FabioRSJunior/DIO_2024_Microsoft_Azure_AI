# Lab 01 - Trabalhando com Machine Learning na Prática no Azure ML

![Untitled](Lab%2001%20-%20Trabalhando%20com%20Machine%20Learning%20na%20Pra%CC%81t%2088c8bd256fbe41ee92a17aa044d96992/Untitled.png)

Este repositório em questão abrange a atividade desenvolvida durante o curso **Microsoft Azure AI Fundamentals**. Especificamente, o foco foi em trabalhar com Machine Learning na prática utilizando o Azure ML (Azure Machine Learning). O conteúdo deste repositório documenta os aprendizados, projetos e experimentos realizados ao longo do curso, fornecendo insights e exemplos práticos sobre o uso de Machine Learning no ambiente do Azure ML.

## Introdução:

O experimento foi focado no treinamento de modelos de machine learning utilizando os algoritmos LightGBM, RandomForest e VotingEnsemble, com a métrica de avaliação sendo o normalized_root_mean_squared_error. Cada algoritmo tem características distintas que contribuem para a eficácia do modelo final:

1. **RandomForest**: Baseado em árvores de decisão, o RandomForest cria múltiplas árvores durante o treinamento e combina suas previsões para uma decisão final. Cada árvore é treinada com uma amostra aleatória dos dados e usa uma combinação aleatória de características em cada divisão, reduzindo o overfitting e melhorando a generalização do modelo.
2. **LightGBM**: Esta implementação eficiente e escalável do Gradient Boosting Decision Tree (GBDT) se destaca pela velocidade e eficácia. O LightGBM utiliza técnicas como Gradient-based One-Side Sampling (GOSS) e Exclusive Feature Bundling (EFB) para melhorar o processo de treinamento, resultando em modelos mais rápidos e precisos.
3. **VotingEnsemble**: Um tipo de ensemble learning, o VotingEnsemble combina as previsões de vários modelos individuais para produzir uma previsão final mais robusta. Neste caso, os modelos RandomForest e LightGBM podem ter sido combinados usando uma técnica de votação, como a votação por maioria, para produzir uma previsão final mais precisa do que qualquer modelo individualmente.

## Laboratório:

O relatório a seguir foi elaborado com base no exercício "Explore o Machine Learning Automatizado no Azure Machine Learning". Neste exercício, utilizamos o recurso de aprendizado de máquina automatizado no Azure Machine Learning para treinar e avaliar um modelo de aprendizado de máquina.

[mslearn-ai-fundamentals](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html)

## Desenvolvimento:

Para realizar o experimento, siga todos os passos a seguir:

 

No Azure Machine Learning Studio , veja a página Automated ML (em Authoring ).

Crie um novo trabalho de ML automatizado com as seguintes configurações, usando Next conforme necessário para avançar pela interface do usuário:

Configurações básicas :

Nome do trabalho : mslearn-bike-automl
Novo nome do experimento : mslearn-bike-rental
Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
Marcadores : nenhum

Tipo de tarefa e dados :

Selecione o tipo de tarefa : Regressão
Selecionar conjunto de dados : crie um novo conjunto de dados com as seguintes configurações:
Tipo de dados :
Nome : aluguel de bicicletas
Descrição : dados históricos de aluguel de bicicletas
Tipo : Tabular
Fonte de dados : Selecione Dos arquivos da web

URL da Web :
URL da Web :[https://aka.ms/bike-rentals](https://aka.ms/bike-rentals)
Ignorar validação de dados : não selecionar

Configurações :

Formato de arquivo : Delimitado
Delimitador : Vírgula
Codificação : UTF-8
Cabeçalhos de coluna : apenas o primeiro arquivo possui cabeçalhos
Pular linhas : Nenhum
O conjunto de dados contém dados multilinhas : não selecione

Esquema :

Incluir todas as colunas exceto Caminho
Revise os tipos detectados automaticamente
Selecione Criar . Após a criação do conjunto de dados, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

Configurações de tarefa :

Tipo de tarefa : Regressão
Conjunto de dados : aluguel de bicicletas
Coluna de destino : Aluguéis (inteiro)

Configurações adicionais : (selecione a engrenagem)
Métrica primária : raiz do erro quadrático médio normalizado
Explique o melhor modelo : Não selecionado
Usar todos os modelos suportados : Desmarcado . Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.

Modelos permitidos : Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.

Limites : expanda esta seção
Máximo de testes : 3
Máximo de testes simultâneos : 3
Máximo de nós : 3
Limite de pontuação da métrica : 0,085 ( para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termina. )
Tempo limite : 15
Tempo limite de iteração : 15
Habilitar rescisão antecipada : selecionado

Validação e teste :
Tipo de validação : divisão de validação de treinamento
Porcentagem de dados de validação : 10
Conjunto de dados de teste : Nenhum

Calcular :

Selecione o tipo de computação : sem servidor
Tipo de máquina virtual : CPU
Camada de máquina virtual : Dedicada
Tamanho da máquina virtual : Standard_DS3_V2*
Número de instâncias : 1

Ao final das configurações é necessário que as informações sejam:  

![Untitled](Lab%2001%20-%20Trabalhando%20com%20Machine%20Learning%20na%20Pra%CC%81t%2088c8bd256fbe41ee92a17aa044d96992/Untitled%201.png)

## Resultados:

Diversas configurações foram ajustadas para otimizar o treinamento dos modelos, e o experimento foi conduzido em um ambiente de computação com máquina virtual Standard_DS3_v2 e prioridade dedicada.

**Algoritmos Utilizados:**
Foram utilizados os algoritmos LightGBM, RandomForest e VotingEnsemble. O VotingEnsemble combina os resultados dos modelos individuais para produzir uma previsão final.

**Métrica de Desempenho:**
A métrica normalized_root_mean_squared_error foi utilizada para avaliar o desempenho dos modelos. O valor de 0.08922 indica um desempenho médio dos modelos treinados em relação aos valores reais.

**Configurações de Treinamento:**
Foram ajustadas diversas configurações para otimizar o treinamento dos modelos, incluindo o número de iterações (3), o tipo de treinamento (TrainFull), a função de aquisição (EI) e a quantidade de validação cruzada (0).

**Datasets Utilizados:**
O conjunto de dados de treinamento utilizado está identificado como MLTable e está localizado em uma URI específica.

**Ambiente de Computação:**
O experimento foi conduzido em um ambiente de computação com máquina virtual Standard_DS3_v2 e prioridade dedicada.

**Conclusão:**
O experimento foi bem-sucedido, resultando em modelos de machine learning com bom desempenho. A combinação dos algoritmos e as configurações ajustadas contribuíram para a precisão das previsões finais.