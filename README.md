# Análise de Risco de Crédito

## Resumo
<p>O objetivo deste notebook é demonstrar de forma breve o uso de Auto Machine Learning (AutoML) através do framework AutoKeras (https://autokeras.com)
no aprendizado supervisionado. Neste caso, utilizou-se AutoML
para criação de modelos de classificação para análise de risco de crédito.</p>
<p>A base de dados utilizada pode ser encontrada na fonte https://www.kaggle.com/datasets/kabure/german-credit-data-with-risk/metadata.</p>
Overview do dataset:

```
RangeIndex: 1000 entries, 0 to 999
Data columns (total 11 columns):
 #   Column            Non-Null Count  Dtype 
---  ------            --------------  ----- 
 0   Unnamed: 0        1000 non-null   int64 
 1   Age               1000 non-null   int64 
 2   Sex               1000 non-null   object
 3   Job               1000 non-null   int64 
 4   Housing           1000 non-null   object
 5   Saving accounts   817 non-null    object
 6   Checking account  606 non-null    object
 7   Credit amount     1000 non-null   int64 
 8   Duration          1000 non-null   int64 
 9   Purpose           1000 non-null   object
 10  Risk              1000 non-null   object
```

## Como foi feito ?
Os dados foram pré-processados somente para que fossem tratados os valores missing, no caso, os valores NaN foram substituídos pela moda nas colunas `Saving accounts` e `Checking account`.
O único parâmetro definido, foi o número máximo de tentativas, o qual foi de 100.

## O que foi obtido ?
O melhor modelo obtido dentre as 100 tentativas, foi uma rede neural do tipo Multilayer Perceptron (Deep Learning), a qual possui 3 camadas ocultas e 2518 parâmetros, podendo esta ser considerada uma rede relativamente pequena. 
```
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 input_1 (InputLayer)        [(None, 10)]              0         
                                                                 
 multi_category_encoding (Mu  (None, 10)               0         
 ltiCategoryEncoding)                                            
                                                                 
 normalization (Normalizatio  (None, 10)               21        
 n)                                                              
                                                                 
 dense (Dense)               (None, 32)                352       
                                                                 
 re_lu (ReLU)                (None, 32)                0         
                                                                 
 dense_1 (Dense)             (None, 32)                1056      
                                                                 
 re_lu_1 (ReLU)              (None, 32)                0         
                                                                 
 dense_2 (Dense)             (None, 32)                1056      
                                                                 
 re_lu_2 (ReLU)              (None, 32)                0         
                                                                 
 dropout (Dropout)           (None, 32)                0         
...
Total params: 2,518
Trainable params: 2,497
Non-trainable params: 21
```
O modelo obteve uma acurácia de 72% em treino  e 73% em teste, um resultado satisfatório visto o baixo tempo de treinamento do modelo (menos de 20 min em uma máquina sem GPU).
Para mais detalhes, consulte o notebook.


## Contato
Pedro G Dubiela (pedrodubielabio@gmail.com)