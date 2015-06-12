

- You can use predefined generators, e.g. for spatially correlated variates, or include univariate random number generators from `R`.
- `sim_gen` defines the position in the chain. `gen_generic` controls the generation process and accepts any random number generator as argument. Also we defined shortcuts like `sim_gen_generic` to be less verbose.
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
##    idD idU          x          e        v         y
## 1    1   1  0.7454883  3.6822042 1.459663 106.63284
## 2    1   2  5.6934259 -0.2506387 1.459663 112.59588
## 3    1   3  1.6492738 -1.2109953 1.459663 103.54722
## 4    1   4  2.4255113  2.5900518 1.459663 108.90074
## 5    1   5 -0.6598988 -5.8960966 1.459663  94.24377
## 6    1   6 -8.6498785 -1.6075882 1.459663  82.55232
## .. ... ...        ...        ...      ...       ...
```

