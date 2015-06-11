
```r
setup1 <- sim_base_lm() %>% sim_sample(sample_number(5))
setup2 <- sim_base_lm() %>% sim_sample(sample_fraction(0.05))
```

- `setup1` and `setup2` differ in the specific way samples are drawn. `sim_sample` is responsible to find the position in the process
- Every `sim_*` function expects a simulation setup or `data.frame` as first argument
- Every `sim_*` controls at which position in the process a function is called
- For every step in the process tools are named using the corresponding prefix, i.e. `gen_generic` or `sample_fraction`
