# Random forest
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
