

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
## 
## # data.frame [10,000 x 6]
##     idD   idU          x         e        v         y
## * <int> <int>      <dbl>     <dbl>    <dbl>     <dbl>
## 1     1     1  3.9462670  1.841257 2.443888 112.17768
## 2     1     2 -5.7587514  7.802529 2.443888  98.72891
## 3     1     3  0.7469758 -1.089258 2.443888 102.84858
## 4     1     4 -5.2633582  3.373478 2.443888  95.29065
## 5     1     5 -1.8117415  8.351238 2.443888 107.17164
## 6     1     6 -1.3475448  1.510108 2.443888 101.25891
## # ... with 9,994 more rows
```

