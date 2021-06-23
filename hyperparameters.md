
##### Table of Contents  
- [Duration model ](#Duration-model)  
- [Random forest](#Random-forest)  
  - [normal claims](#normal-claims )  
  - [extreme claims](#extreme-claims )  
  - [classification](#classification )  
- [Gradient boosting](#Gradient-boosting)  
  - [normal claims](#normal-claims )  
  - [extreme claims](#extreme-claims )  
  - [classification](#classification ) 
- [Fully Connected model](#Fully-Connected-model)  
- [Text model ](#Text-model )  

# Duration model 

goal : maximize concordance index 

hyperparameters grid: 
* penalizer : 1 *10^-4 to 1.0 
* l1 ration :  1 *10^-4 to 1.0 

best hyperparameters: 
* penalizer 0.004835
* l1_ratio 0.059547

baseline estimation breslow 
* number of observation 121524
* number of events observed 95009
* partial log likelihood -1012723.30

* Concordance 0.71
* Partial AIC 2025718.61
* log likelihood ration test 32391.77 calculate on 137 observation from training data randomly draw


# Random forest
hyperparameters grid: 
* max features : auto, sort, log2
* Numbers of trees 10 to 300
* max depth 1 to 10
* min_sample split 2 to 100
* min sample leaf 2 to 100

## normal claims 

goal : minimize MSE



|   Time in month   |   max features  |   Numbers of trees  |   max depth  |   min_sample split  |   min sample leaf  |
|:-----------------:|:---------------:|:-------------------:|:------------:|:-------------------:|:------------------:|
|          0        |       auto      |          252        |       10     |           2         |          70        |
|          6        |       auto      |          294        |       10     |          98         |          60        |
|         12        |       auto      |          241        |       10     |          73         |          41        |
|         18        |       auto      |          103        |       9      |          75         |          26        |
|         24        |       auto      |          271        |       10     |          52         |         100        |
|         30        |       auto      |          287        |       10     |          37         |          40        |
|         36        |       auto      |          146        |       10     |           5         |          46        |
|         42        |       auto      |          224        |       10     |          23         |          26        |
|         48        |       auto      |          193        |       10     |           9         |          28        |
|         54        |       auto      |          36         |       10     |          66         |          43        |

## extreme claims 

goal : minimize MSE

|   Time in month   |   max features  |   Numbers of trees  |   max depth  |   min_sample split  |   min sample leaf  |
|:-----------------:|:---------------:|:-------------------:|:------------:|:-------------------:|:------------------:|
|          0        |       log2      |          209        |       7      |          70         |          5         |
|          6        |       log2      |          134        |       7      |          86         |          9         |
|         12        |       auto      |          154        |       8      |          91         |          7         |
|         18        |       auto      |          231        |       9      |          74         |          35        |
|         24        |       auto      |          125        |       10     |          17         |          11        |
|         30        |       auto      |          165        |       10     |          37         |          22        |
|         36        |       auto      |          14         |       8      |          71         |          33        |
|         42        |       auto      |          147        |       9      |          47         |          30        |
|         48        |       auto      |          92         |       9      |          87         |          21        |
|         54        |       log2      |          15         |       9      |          14         |          18        |

## classification


goal : maximize F1 score


|   Time in month   |   max features  |   Numbers of trees  |   max depth  |   min_sample split  |   min sample leaf  |
|:-----------------:|:---------------:|:-------------------:|:------------:|:-------------------:|:------------------:|
|          0        |       sqrt      |          10         |       9      |          61         |         100        |
|          6        |       sqrt      |          222        |       10     |          92         |          2         |
|         12        |       auto      |          10         |       10     |          100        |          2         |
|         18        |       auto      |          300        |       10     |          79         |          2         |
|         24        |       auto      |          251        |       3      |           2         |          15        |
|         30        |       sqrt      |          183        |       7      |           8         |          19        |
|         36        |       auto      |          76         |       10     |          100        |          33        |
|         42        |       sqrt      |          84         |       8      |          91         |          35        |
|         48        |       sqrt      |          213        |       8      |          89         |          21        |
|         54        |       sqrt      |          10         |       5      |           2         |          27        |


# Gradient boosting
hyperparameters grid:
* max features : auto, sort, log2
* Numbers of trees 10 to 100
* max depth 1 to 10
* min_sample split 2 to 100
* min sample leaf 2 to 100
* loss: deviance, exponential for classification ls, lad, huber, quantile for regression
* learning rate 0.1,0.01,0.001


## normal claims 

goal : minimize MSE

|   Time in month   |   max features  |    loss  |   learning rate  |   Numbers of trees  |   max depth  |   min_sample split  |   min sample leaf  |
|:-----------------:|:---------------:|:--------:|:----------------:|:-------------------:|:------------:|:-------------------:|:------------------:|
|          0        |       sqrt      |     ls   |        0.1       |          150        |       6      |          100        |         100        |
|          6        |       auto      |   huber  |        0.1       |          118        |       9      |          74         |          51        |
|         12        |       sqrt      |     ls   |        0.1       |          127        |       8      |          15         |          41        |
|         18        |       auto      |   huber  |        0.1       |          117        |       8      |          30         |          87        |
|         24        |       auto      |   huber  |        0.1       |          150        |       7      |          46         |          18        |
|         30        |       auto      |     ls   |        0.1       |          138        |       8      |          41         |          37        |
|         36        |       sqrt      |     ls   |        0.1       |          150        |       10     |          88         |          79        |
|         42        |       auto      |     ls   |        0.1       |          131        |       8      |           2         |          51        |
|         48        |       sqrt      |     ls   |        0.01      |          150        |       10     |          68         |          80        |
|         54        |       auto      |   huber  |        0.1       |          66         |       10     |          100        |          2         |

## extreme claims 

goal : minimize MSE

|   Time in month   |   max features  |     loss    |   learning rate  |   Numbers of trees  |   max depth  |   min_sample split  |   min sample leaf  |
|:-----------------:|:---------------:|:-----------:|:----------------:|:-------------------:|:------------:|:-------------------:|:------------------:|
|          0        |       log2      |      ls     |        0.1       |          103        |       4      |           2         |          26        |
|          6        |       log2      |      ls     |        0.1       |          116        |       6      |          16         |          92        |
|         12        |       sqrt      |   quantile  |        0.1       |          150        |       10     |          100        |         100        |
|         18        |       auto      |   quantile  |        0.01      |          150        |       10     |          77         |         100        |
|         24        |       sqrt      |      ls     |        0.1       |          73         |       4      |          34         |          30        |
|         30        |       log2      |      ls     |        0.1       |          18         |       6      |          88         |          40        |
|         36        |       log2      |   quantile  |        0.1       |          134        |       3      |          11         |          49        |
|         42        |       log2      |      ls     |        0.1       |          148        |       6      |          11         |          58        |
|         48        |       log2      |      ls     |        0.1       |          56         |       10     |          42         |          4         |
|         54        |       log2      |      ls     |        0.1       |          50         |       8      |          57         |          20        |

## classification


goal : maximize F1 score

|   Time in month   |   max features  |       loss     |   learning rate  |   Numbers of trees  |   max depth  |   min_sample split  |   min sample leaf  |
|:-----------------:|:---------------:|:--------------:|:----------------:|:-------------------:|:------------:|:-------------------:|:------------------:|
|          0        |       sqrt      |     deviance   |        0.1       |          90         |       3      |           9         |          8         |
|          6        |       auto      |     deviance   |        0.1       |          47         |       4      |          36         |          54        |
|         12        |       auto      |     deviance   |        0.1       |          91         |       10     |          96         |          86        |
|         18        |       sqrt      |     deviance   |        0.1       |          100        |       9      |           2         |         100        |
|         24        |       sqrt      |   exponential  |        0.1       |          78         |       8      |          94         |          73        |
|         30        |       auto      |   exponential  |        0.1       |          97         |       6      |          99         |          6         |
|         36        |       log2      |     deviance   |        0.1       |          100        |       10     |          33         |          68        |
|         42        |       auto      |     deviance   |        0.1       |          82         |       10     |          24         |          53        |
|         48        |       auto      |   exponential  |        0.1       |          48         |       10     |           2         |          2         |
|         54        |       sqrt      |   exponential  |        0.1       |          71         |       3      |          39         |          64        |


# Fully Connected model

goal : maximize F1 score

hyperparameters grid: 
* input neurons : 16-32-64-128-256-512-1024 
* number of Hidden Layer : 0 to 5
* number of neurones in their Hidden Layer : 16-32-64-128-256-512-1024
* optimizer : Adam, Adagrad, SGD
* LR: 0.1,0.01,0.001,0.0001
* activation : swish, sigmoid, relu, linear, hard sigmoid, tanh,
* dropout : 0.01, 0.05;0.1,0.15,0.2,0.25,0.3,0.35,0.4
* batch size 8 or 16
* loss : custom loss 1, custom loss 2, custom loss 3
custom loss is a weighted cross entropy with different weights

* (1,6) (15,0.5)
* (1,4) (10,0.5)
* (1,1.5) (4,0.5)
best hyperparameters: 

* input neurons : 512
* number of Hidden Layer : 2
* number of neurones in their Hidden Layer  :064
* optimizer : Adam
* LR: 0.0001
* activation : tanh,
* dropout : 0.05
* batch size 16
* loss : custom loss 2


# Text model

goal : maximize F1 score


Each Fully Connected layer is followed by a BatchNormalization layer.

hyperparameters grid: 
* input neurons : 16-32-64-128-256-512-1024 
* number of additionnal LSTM layer : 0 to 3
* number of neurones in their additionnal LSTM layer : 16-32-64-128-256-512-1024
* input neurons in the first Fully Connected layer: 16-32-64-128-256-512-10241
* number of additionnal Fully Connected  layer : 0 to 3
* number of neurones in their Fully Connected  layer: 16-32-64-128-256-512-1024
* optimizer : Adam, Adagrad, SGD
* LR: 0.1,0.01,0.001,0.0001
* activation : swish, sigmoid, relu, linear, hard sigmoid, tanh,
* batch size 8 or 16
* loss : custom loss 1, custom loss 2, custom loss 3

best hyperparameters: 
* input neurons : 32
* number of additionnal LSTM layer : 0
* number of neurones in their additionnal LSTM layer : 0
* input neurons in the first Fully Connected layer: 64
* number of additionnal Fully Connected  layer : 2
* number of neurones in their Fully Connected  layer: 1024
* optimizer : Adagrad
* LR: 0.01
* activation : linear
* batch size 8
* loss : custom loss 1


