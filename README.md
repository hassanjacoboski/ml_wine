# Teste Data Scientis Cognitivo
## Estratégia de modelagem:
Primeiramente explorei os dados para avaliar se seria necessário realizar processos como: alterar tipo de variavel ou remover dados inconsistentes ou nulos.

Verifiquei que seria necessária a mudança do campo alcohol do tipo string para float, e com isso exclui alguns registros que possuiam valores estranhos. Na sequência transformei o campo type para um equivalente númerico, deixando o vinho do tipo 'White' com o valor 0 e o vinho do tipo 'Red' com o valor 1.

Dividi a classificação da avaliação dos vinhos em 3 sendo:  0 - 4 como Ruim (valor 0); 5 - 6 como médio (valor 1), e 7 - 10 como bom (valor 2)

Selecionei 3 modelos de machine-learning com caracteristicas distintas de avaliação de tendência e variância. Acessei o site [Scikilearn](https://scikit-learn.org/stable/auto_examples/classification/plot_classifier_comparison.html)

Escolhi os modelos Gaussian Process, Random Forest e Neural Net, pois cada um demonstrava uma forma diferente de avaliar os limites das bordas de classificação.

Rodei um teste para avaliar o tempo de processamento e avaliar a acurácia e a pontuação F1 de cada um dos modelos.

Dividi os resultados de cada um dos modelos em 3 faixas para rodar em cima dos dados de treinamento (5%, 25% e 100%), e testei também com os dados de teste. Utilizei as funções de split da bibliotéca do scikitlearn para facilitar a divisão dos dataframes de treinamento e teste, e também para medir acurácia e pontuação F1.

Dentre os três modelos o Gaussian Process foi o que demorou mais tempo para processar devido a complexidade do algoritmo.

O que apresentou os valores de acurácia e pontuação F1 mais elevados foi o de Random Forest, muito provavelmente por ser um modelo que acompanha mais a tendência do que os outros dois modelos escolhidos.

Devido aos resultados apresentados e avaliando que os dados não apresentavam uma variância muito grande, terminei por selecionar o modelo de Random Forest como modelo para predição, já que seu tempo de processamento foi aceitável e os resultados significativamente melhor do que os outros dois modelos.

A biblioteca do Scikitlearn é muito bem conceituada no meio dos cientistas de dados, e possui uma fácil utilização, facilitando também o tuning de parâmetros e teste de efetividade de modelos, por essa razão utilizei suas ferramentas como forma de avaliação e seleção de modelo de ML.

O modelo selecionado conseguiu ter uma taxa de acertividade de classificação superior a 80% com os dados de teste utilizados. Foi identificado que alguns parâmetros como o 'alcohol' e 'density' possuem uma maior influência sobre a qualidade do vinho. Se realizado um tuning sobre o modelo de Random Forests, ajustando a quantidade de nós mínimo e máximo, a quantidade de campos a serem avaliados e o número de árvores de decisão dentro do modelo. Testando o afinamento dessas variáveis pode-se ter um aumento na taxa de acertividade e em sua pontuação F1.