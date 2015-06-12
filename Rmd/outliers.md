



- Set the frequency or probability for adding contaminated observations.
- You can choose between unit and area level outliers, i.e. \textit{outlying} units or groups in the data.


```r
setupCont <- setup %>% 
  sim_gen_cont(gen_generic(rnorm, sd = 50, name = "e"), 0.01, "unit") %>%
  sim_gen_vc(sd = 50, areaVar = "idD", nCont = 0.1, type = "area")

autoplot(setup)
autoplot(setupCont)
```



