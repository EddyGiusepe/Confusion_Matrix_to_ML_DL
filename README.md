# Tudo o que você deve saber sobre a Matriz de Confusão para Aprendizado de Máquina


![image](https://user-images.githubusercontent.com/69597971/153123378-ebc97af4-a597-4fe1-a44c-a4c1beb0d9c0.png)

A seguinte imagem está baseada [neste link](https://yassineelkhal.medium.com/confusion-matrix-auc-and-roc-curve-and-gini-clearly-explained-221788618eb2):
![image](https://user-images.githubusercontent.com/69597971/153124088-04567069-88cc-49f2-b48c-6858d5830455.png)


Você já esteve em uma situação em que esperava que seu modelo de aprendizado de máquina tivesse um desempenho muito bom, ``mas teve uma precisão ruim?`` Você fez todo o trabalho duro - então, ``onde o modelo de classificação deu errado?`` ``Como você pode corrigir isso?``

Existem muitas maneiras de avaliar o desempenho do seu modelo de classificação, mas nenhuma resistiu ao teste do tempo como a ``matriz de confusão``. Ele nos ajuda a avaliar o desempenho do nosso modelo, onde ele deu errado e nos oferece orientação para corrigir nosso caminho.

Neste artigo, exploraremos como uma matriz de confusão fornece uma visão holística do desempenho do seu modelo. E, ao contrário do nome, você perceberá que uma matriz de confusão é um conceito bastante simples, mas poderoso.


## Abordaremos:

* O que é uma Matriz de Confusão?
  * Verdadeiro Positivo
  * Verdadeiro Negativo
  * Falso Positivo - Erro Tipo 1
  * Falso Negativo - Erro Tipo 2
  
* Por que precisa de uma matriz de confusão?
* Precisão x Recall
* Pontuação F1
* Matriz de confusão no Scikit-learn
* Matriz de confusão para classificação multiclasse


## O que é uma Matriz de Confusão?

Uma matriz Confusion é uma matriz ``N x N`` usada para avaliar o desempenho de um modelo de classificação, onde **N** é o número de classes alvo. A matriz compara os valores de destino ``reais`` com os ``previstos`` pelo modelo de aprendizado de máquina. Isso nos dá uma visão holística do desempenho do nosso modelo de classificação e quais tipos de erros ele está cometendo.

**Por exemplo:** para um problema de ``classificação binária``, teríamos uma matriz ``2 x 2`` como mostrado abaixo com 4 valores:

![image](https://user-images.githubusercontent.com/69597971/153303752-7cbcff7e-53ae-4f19-aa1d-ffa6db195cc9.png)

No gráfico, temos:
* A variável de destino (target) tem dois valores: **Positivo** ou **Negativo**
* As colunas representam os valores reais da variável de destino
* As linhas representam os valores previstos da variável de destino

## Compreendendo o VP, o VN, o FP e o FN em uma Matriz de Confusão 

* **Verdadeiro Positivo (TP ou VP)** 
  * O valor previsto corresponde ao valor real
  * O valor real foi positivo e o modelo previu um valor positivo

* **Verdadeiro Negativo (TN ou VN)** 
  * O valor previsto corresponde ao valor real
  * O valor real foi negativo e o modelo previu um valor negativo

* **Falso Positivo (FP) - Erro tipo 1**
  * O valor previsto foi falsamente previsto
  * O valor real foi negativo, mas o modelo previu um valor positivo
  * Também conhecido como ``erro tipo 1``

* **Falso Negativo (FN) - Erro tipo 2**
  * O valor previsto foi falsamente previsto
  * O valor real foi positivo, mas o modelo previu um valor negativo
  * Também conhecido como ``erro tipo 2``

**Por exemplo:** Suponha que tivéssemos um conjunto de dados de classificação com ``1000 pontos de dados``. Colocamos um classificador nele e obtemos a matriz de confusão abaixo:

<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153305710-9f2c5a3e-7f11-4123-a8a5-fdef4d7b8ae5.png" />
</p>

Os diferentes valores da matriz Confusion seriam os seguintes:

* **Verdadeiro Positivo (TP) = 560**; o que significa que 560 pontos de dados de classe positivos foram classificados corretamente pelo modelo
* **Verdadeiro Negativo (TN) = 330**; significando que 330 pontos de dados de classe negativa foram classificados corretamente pelo modelo
* **Falso Positivo (FP) = 60**; o que significa que 60 pontos de dados de classe negativa foram classificados incorretamente como pertencentes à classe positiva pelo modelo
* **Falso Negativo (FN) = 50**; significando que 50 pontos de dados de classe positiva foram incorretamente classificados como pertencentes à classe negativa pelo modelo


Isso acabou sendo um classificador bastante decente para nosso conjunto de dados, considerando o número relativamente maior de valores verdadeiros positivos e verdadeiros negativos.


## Por que precisamos de uma Matriz de Confusão?

**Por exemplo:** 
Vamos pensar em um problema de classificação hipotética. Digamos que você queira prever quantas pessoas estão infectadas com um vírus contagioso antes de apresentarem os sintomas e isolá-las da população saudável. Os dois valores para nossa variável de destino seriam: ``Sick`` e ``Not Sick``.

Agora, você deve estar se perguntando – por que precisamos de uma ``matriz de confusão`` quando temos nosso amigo para todos os tempos – ``Precisão?`` Bem, vamos ver onde a **precisão falha**. 

Nosso conjunto de dados é um exemplo de um conjunto de [dados desbalanceado](https://www.analyticsvidhya.com/blog/2017/03/imbalanced-data-classification/?utm_source=blog&utm_medium=confusion-matrix-machine-learning) . Existem ``947`` pontos de dados para a classe negativa e ``3`` pontos de dados para a classe positiva. 
Lembrando que a precisão, se calcula assim:

<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153308515-cc8840d0-8963-47f5-8436-bd70af6057c5.png" />
</p>

Nosso modelo se comportou assim:

<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153308714-62977af9-8ede-4220-b6d1-855926213c24.png" />
</p>

Os valores totais do resultado são:``TP = 30``, ``TN = 930``, ``FP = 30``, ``FN = 10``

Então, a precisão do nosso modelo acaba sendo:
<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153309271-dbfbf170-b2e1-4682-b787-432afd772653.png" />
</p>

96% de PRECISÃO, nada mal. Mas **CUIDADO:** está dando a ideia errada sobre o resultado.

Nosso modelo está dizendo ``“Posso prever pessoas doentes 96% das vezes”``. ``No entanto, está fazendo o contrário``. Está prevendo as pessoas que não ficarão doentes com 96% de precisão enquanto os doentes estão espalhando o vírus!

Você acha que essa é uma métrica correta para o nosso modelo, dada a gravidade do problema? Não deveríamos estar medindo quantos casos positivos podemos prever corretamente para impedir a propagação do vírus contagioso? Ou talvez, dos casos corretamente previstos, quantos são casos positivos para verificar a confiabilidade do nosso modelo?

É aqui que nos deparamos com o conceito duplo de ``Precisão`` e ``Recall``.


## Precisão vs. Recall

* A ``precisão`` nos diz quantos dos casos corretamente previstos foram realmente positivos. A precisão se determina, assim:

<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153317507-fe46389e-6556-4c48-8efe-61f89b866c85.png" />
</p>
Isso determinaria se nosso modelo é confiável ou não.


* ``Recall`` nos diz quantos dos casos positivos reais fomos capazes de prever corretamente com nosso modelo. O recall se calcula, assim:

<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153318334-8c716741-f63f-4537-b535-fd4c76f0b5e1.png" />
</p>



<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153319962-766ba603-a7d3-4606-8419-3095517741f5.png" />
</p>


Podemos calcular facilmente ``Precision`` e ``Recall`` para nosso modelo inserindo os valores nas fórmulas acima:

<p align="center">
<img src="https://user-images.githubusercontent.com/69597971/153321495-0c17eda0-5fbb-4139-b602-26d39677736d.png" />
</p>





































Links de estudo:

* [Site de Analytics Vidhya](https://www.analyticsvidhya.com/?s=ROC+and+AUC)

* [Matriz de confusão](https://www.analyticsvidhya.com/blog/2020/04/confusion-matrix-machine-learning/)

* [Confusion Matrix](https://www.scikit-yb.org/en/latest/api/classifier/confusion_matrix.html)

* [Scikit Learn - plot_confusion_matrix.ipynb](https://scikit-learn.org/stable/auto_examples/model_selection/plot_confusion_matrix.html)

* [Exemplos de Confusion Matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)

* [How to Make Predictions with Keras](https://machinelearningmastery.com/how-to-make-classification-and-regression-predictions-for-deep-learning-models-in-keras/)

* [Confusion matrix, AUC and ROC curve and Gini clearly explained](https://yassineelkhal.medium.com/confusion-matrix-auc-and-roc-curve-and-gini-clearly-explained-221788618eb2)



Thanks God!

