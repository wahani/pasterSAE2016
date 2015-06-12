

- To start the simulation use the function `sim` and specify the number of runs.
- To start the simulation in parallel define the `mode` and number of `cpus`.
- Packages and also objects can be loaded on all nodes with extra arguments to `sim`.
- Here the we perform 16 runs on 4 cores. `sim` always returns a `list` and here we combine the results directly using `rbind_all`.


```r
sim(setup, R = 16, mode = "socket", cpus = 4) %>% (dplyr::rbind_all) %>% dim
```

```
## Starting parallelization in mode=socket with cpus=4.
## Mapping in parallel: mode = socket; cpus = 4; elements = 16.
## Stopped parallelization. All cleaned up.
```

```
## [1] 160000      8
```

