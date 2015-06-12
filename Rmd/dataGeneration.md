

- You can use predefined generators, e.g. for spatially correlated variates, or include univariate random number generators from `R`.
- `sim_gen` defines the position in the chain. `gen_generic` controls the generation process and accepts any random number generator. Also we defined shortcuts like `sim_gen_generic` to be less verbose.
- In the following you see a definition for drawing numbers from a linear mixed model. The response is constructed with an R expression and set by `sim_resp_eq`.


```r
setup <- sim_base() %>% # default with 100 areas (domains) and 100 units each
  sim_gen(gen_generic(rnorm, sd = 4, name = "x")) %>% 
  sim_gen(gen_generic(rnorm, sd = 4, name = "e")) %>%
  sim_gen_generic(rnorm, sd = 2, groupVars = "idD", name = "v") %>%
  sim_resp_eq(y = 100 + 2 * x + v + e)
setup
```

```
## data.frame [10,000 x 6]
## 
##    idD idU            x          e         v         y
## 1    1   1 -0.341367085 -5.8689371 -2.237349  91.21098
## 2    1   2 -3.496910745 -1.4657426 -2.237349  89.30309
## 3    1   3  2.793777378 -6.6365887 -2.237349  96.71362
## 4    1   4 -7.451192075  0.7091784 -2.237349  83.56945
## 5    1   5  0.005423844 -3.5601176 -2.237349  94.21338
## 6    1   6  2.639683043 -0.8874050 -2.237349 102.15461
## .. ... ...          ...        ...       ...       ...
```

