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

{:.center}
![image](https://user-images.githubusercontent.com/69597971/153305710-9f2c5a3e-7f11-4123-a8a5-fdef4d7b8ae5.png)
.center {
  text-align: center;
}













Links de estudo:

* [Site de Analytics Vidhya](https://www.analyticsvidhya.com/?s=ROC+and+AUC)

* [Matriz de confusão](https://www.analyticsvidhya.com/blog/2020/04/confusion-matrix-machine-learning/)

* [Confusion Matrix](https://www.scikit-yb.org/en/latest/api/classifier/confusion_matrix.html)

* [Scikit Learn - plot_confusion_matrix.ipynb](https://scikit-learn.org/stable/auto_examples/model_selection/plot_confusion_matrix.html)

* [Exemplos de Confusion Matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)

* [How to Make Predictions with Keras](https://machinelearningmastery.com/how-to-make-classification-and-regression-predictions-for-deep-learning-models-in-keras/)

* [Confusion matrix, AUC and ROC curve and Gini clearly explained](https://yassineelkhal.medium.com/confusion-matrix-auc-and-roc-curve-and-gini-clearly-explained-221788618eb2)



Thanks God!

