



- Set the frequency or probability for adding contaminated observations
- Specify contamination within domains or across the population
- Change between area and unit level contamination


```r
setup %>% 
  sim_gen_cont(gen_generic(rnorm, sd = 150, name = "e"), 0.1, "unit")
```

```
## data.frame [10,000 x 7]
## 
##    idD idU         x         e        v   idC         y
## 1    1   1 -2.166447 -1.029188 1.208294 FALSE  95.84621
## 2    1   2 -4.770198  2.172307 1.208294 FALSE  93.84021
## 3    1   3  2.393438 -4.610486 1.208294 FALSE 101.38468
## 4    1   4  2.754315 -5.162324 1.208294 FALSE 101.55460
## 5    1   5  2.735989 -3.642082 1.208294 FALSE 103.03819
## 6    1   6 -2.055526  5.921647 1.208294 FALSE 103.01889
## .. ... ...       ...       ...      ...   ...       ...
```


```r
autoplot(setup)
autoplot(setup %>% sim_gen_vc()) # contamination on area-level 
```



