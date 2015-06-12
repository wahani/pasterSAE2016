


```r
comp_lm <- function(dat) {
  dat$lm <- predict(lm(y ~ x, data = dat))
  dat
}

simDat <- setup %>% sim_sample() %>% 
  sim_comp_popMean() %>% 
  sim_comp_sample(comp_lm) %>% 
  sim_agg() %>% sim(R = 100) %>% 
  rbind_all() %>% group_by(idD) %>% 
  summarise(
    MSE_direct = mean((y - popMean)^2), 
    MSE_lm = mean((lm - popMean)^2)
    )
boxplot(simDat$MSE_direct, simDat$MSE_lm, 
        names = c("sample mean", "lm"),
        main = "Comparison of MSE")
```


