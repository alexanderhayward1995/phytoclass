
<!-- README.md is generated from README.Rmd. Please edit that file -->

# phytoclass

The *phytoclass* package uses non-negative matrix factorization and
simulated annealing to determine the biomass of different phytoplankton
groups from pigment concentrations.

## Installation

You can install the development version of phytoclass from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("AndyMcKenzieFromNZ/phytoclass")
```

## Example

For the built-in samples matrix Sm of pigment samples:

``` r
library(phytoclass)
Results <- simulated_annealing(Sm, niter = 5)
#> 
#> Condition number = 384
#> Current error:  0.0283
#> Neighbour's error:  0.0283
#> Temperature (%):  99.1
#> [1] " "
#> Current error:  0.0256
#> Neighbour's error:  0.0256
#> Temperature (%):  98.21
#> [1] " "
#> Current error:  0.0253
#> Neighbour's error:  0.0253
#> Temperature (%):  97.32
#> [1] " "
#> Current error:  0.0253
#> Neighbour's error:  0.0262
#> Temperature (%):  96.45
#> [1] " "
#> Current error:  0.0249
#> Neighbour's error:  0.0249
#> Temperature (%):  95.58
#> [1] " "

Results$RMSE
#> [1] 0.02486108
Results$MAE
#>          Per       X19but         Fuco         Neox          Pra         Viol 
#> 4.817079e-03 2.928202e-05 7.672483e-04 8.017250e-03 1.460943e-03 2.087554e-02 
#>       X19hex         Allo          Zea        Chl.b        Tchla 
#> 1.328648e-04 4.987826e-04 1.054345e-02 1.303880e-03 3.532710e-03
Results$Error
#>                 Per        X19but          Fuco          Neox           Pra
#> 1257  -2.644965e-04  7.192209e-04 -4.922698e-02 -0.0043373439  2.463273e-03
#> 1278  -5.449596e-04  6.621762e-06 -1.916032e-02 -0.0025736577  9.463059e-04
#> 1908  -4.000478e-04  4.860950e-06 -1.406535e-02  0.0002466796  1.414449e-03
#> 1909  -3.505349e-04  4.259322e-06 -1.232451e-02  0.0003541859  1.447247e-03
#> 1914  -6.450594e-05  7.838067e-07 -2.267975e-03  0.0035102673  3.021989e-04
#> 1915  -1.622043e-05  1.970932e-07 -5.702969e-04  0.0036097886  9.346751e-04
#> 5614   0.000000e+00 -2.171926e-06  6.284552e-03  0.0017348537  1.096775e-03
#> 5647   0.000000e+00 -1.055630e-06  3.054507e-03  0.0015691559  1.322887e-03
#> 5653   0.000000e+00 -2.165896e-07  6.267103e-04  0.0014191113  6.695878e-04
#> 6770   0.000000e+00 -1.725415e-06  4.992555e-03  0.0012480020  3.899522e-04
#> 8425   0.000000e+00 -9.084141e-07  2.628531e-03  0.0003838770  3.672947e-05
#> 8426   0.000000e+00 -1.528773e-06  4.423563e-03  0.0074810034 -1.312819e-04
#> 9538   0.000000e+00 -1.273283e-06  3.684292e-03  0.0038079496  3.151375e-05
#> 9568   0.000000e+00 -1.337243e-06  3.869365e-03  0.0044890991  4.570564e-04
#> 9625  -1.145071e-04  1.391366e-06 -4.025972e-03  0.0072968418 -3.340909e-04
#> 9626   0.000000e+00 -2.734347e-08  7.911965e-05  0.0030003859  3.714212e-03
#> 9838  -6.969855e-05  8.469017e-07 -2.450543e-03 -0.0003850642  1.567902e-03
#> 9839   0.000000e+00 -5.918873e-07  1.712649e-03  0.0008817432  2.025898e-03
#> 9845   0.000000e+00 -1.576425e-08  4.561445e-05 -0.0000724780  1.515230e-03
#> 9860   0.000000e+00 -3.734805e-07  1.080680e-03 -0.0033052828  9.241915e-04
#> 9861  -4.255335e-06  5.170624e-08 -1.496140e-04 -0.0018595840  1.618648e-03
#> 9904  -2.203300e-05  2.677212e-07 -7.746617e-04 -0.0019054794  3.102000e-04
#> 9913  -4.556195e-05  5.536197e-07 -1.601920e-03  0.0006449375  4.298080e-04
#> 9938   0.000000e+00 -1.445105e-06  4.181467e-03  0.0097064003 -6.606573e-04
#> 9980   0.000000e+00 -6.915469e-07  2.001018e-03  0.0001912424 -2.632443e-04
#> 10081  0.000000e+00 -3.298936e-07  9.545602e-04  0.0006392285  2.829843e-03
#> 10082  0.000000e+00 -7.630319e-07  2.207862e-03  0.0053617730  2.450698e-04
#> 10089  0.000000e+00 -6.246120e-07  1.807339e-03  0.0036332426  4.501731e-04
#> 10121  0.000000e+00 -1.101307e-06  3.186673e-03  0.0024255575  7.674740e-04
#>                Viol        X19hex          Allo           Zea         Chl.b
#> 1257   0.0043371361  1.366057e-03 -3.167246e-04 -1.119591e-02  7.500024e-03
#> 1278   0.0026043397 -8.418488e-04 -6.525685e-04 -1.112350e-03 -2.545202e-03
#> 1908  -0.0031831370 -6.179903e-04 -4.790421e-04 -3.767918e-03  3.202411e-04
#> 1909  -0.0033520430 -5.415031e-04 -4.197523e-04 -4.281939e-03  1.053872e-03
#> 1914  -0.0034414132 -9.964821e-05 -7.724343e-05 -7.736640e-04 -1.437119e-03
#> 1915  -0.0033177392 -2.505718e-05 -1.942336e-05 -4.438292e-03  1.401070e-03
#> 5614   0.0020953919  2.761249e-04  2.140413e-04 -7.581403e-03  4.742525e-03
#> 5647  -0.0006390576  1.342062e-04  1.040314e-04 -1.872915e-05 -3.648495e-03
#> 5653   0.0014531163  2.753582e-05  2.134470e-05  8.505128e-06 -3.239624e-03
#> 6770   0.0028098711  2.193583e-04  1.700380e-04 -3.740997e-03  1.880608e-03
#> 8425  -0.0042067905  1.154900e-04  8.952337e-05  3.567198e-05  1.704717e-03
#> 8426  -0.0055002346  1.943585e-04  0.000000e+00  6.003248e-05 -2.766786e-03
#> 9538  -0.0070690672  1.618771e-04  0.000000e+00  4.999978e-05  3.427756e-04
#> 9568   0.0028359530  1.700086e-04  1.317841e-04 -4.185411e-03 -4.930994e-04
#> 9625   0.0097320562 -1.768895e-04 -1.371179e-04 -5.463674e-05 -9.606357e-03
#> 9626   0.0133872526  3.476287e-06  2.694683e-06 -1.430538e-02 -2.641616e-04
#> 9838   0.0124479733 -1.076697e-04 -8.346138e-05 -9.979460e-03  2.526424e-03
#> 9839   0.0027524787  7.524879e-05  5.832995e-05 -4.229987e-03 -1.513214e-03
#> 9845   0.0049349009  2.004166e-06  1.553552e-06 -8.803430e-03  4.569043e-03
#> 9860   0.0045226536  4.748194e-05  3.680616e-05 -5.554650e-03  5.082091e-03
#> 9861   0.0047576609 -6.573603e-06 -5.095603e-06 -9.082118e-03  6.113878e-03
#> 9904   0.0021742153 -3.403638e-05 -2.638368e-05 -1.672014e-03  1.685070e-03
#> 9913   0.0022631747 -7.038369e-05 -5.455871e-05 -2.392667e-03  6.689707e-05
#> 9938   0.0077155965  1.837215e-04  1.424138e-04  5.674697e-05 -8.932932e-03
#> 9980   0.0047239598  8.791888e-05  6.815131e-05  3.975377e-06 -1.280507e-03
#> 10081  0.0030869270  4.194059e-05  3.251072e-05 -1.793498e-03 -6.260612e-03
#> 10082  0.0042432927  9.700703e-05  7.519609e-05  2.996305e-05 -6.369410e-03
#> 10089  0.0088757947  7.940922e-05  6.155495e-05  2.452752e-05 -7.495804e-03
#> 10121  0.0009639974  1.400131e-04  1.085328e-04 -5.075495e-03  2.146117e-03
#>               Tchla
#> 1257   0.1280454029
#> 1278   0.2638204133
#> 1908   0.1936671558
#> 1909   0.1696974402
#> 1914   0.0312279728
#> 1915   0.0078524743
#> 5614  -0.0865326197
#> 5647  -0.0420578173
#> 5653  -0.0086292370
#> 6770  -0.0687429816
#> 8425  -0.0361925095
#> 8426  -0.0609084845
#> 9538  -0.0507293878
#> 9568  -0.0532776720
#> 9625   0.0554340141
#> 9626  -0.0010894064
#> 9838   0.0337417674
#> 9839  -0.0235816319
#> 9845  -0.0006280699
#> 9860  -0.0148799951
#> 9861   0.0020600502
#> 9904   0.0106663941
#> 9913   0.0220569962
#> 9938  -0.0575750340
#> 9980  -0.0275522101
#> 10081 -0.0131434349
#> 10082 -0.0304002743
#> 10089 -0.0248854350
#> 10121 -0.0438776229
Results$`F matrix`
#>                      Per     X19but   Fuco   Neox    Pra   Viol X19hex   Allo
#> Prasinophytes     0.0000 0.00000000 0.0000 0.0914 0.2705 0.0490 0.0000 0.0000
#> Chlorophytes      0.0000 0.00000000 0.0000 0.0501 0.0000 0.0226 0.0000 0.0000
#> Cryptophytes      0.0000 0.00000000 0.0000 0.0000 0.0000 0.0000 0.0000 0.4492
#> Diatoms-B         0.0000 0.00000000 0.7786 0.0000 0.0000 0.0000 0.0000 0.0000
#> Dinoflagellates-A 0.5379 0.00000000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000
#> Haptophytes       0.0000 0.09027509 0.4333 0.0000 0.0000 0.0000 0.3952 0.0000
#> Pelagophytes      0.0000 0.86990000 0.7939 0.0000 0.0000 0.0000 0.0000 0.0000
#> Syn               0.0000 0.00000000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000
#>                         Zea  Chl.b Tchla
#> Prasinophytes     0.1330431 0.8119     1
#> Chlorophytes      0.0470000 0.4724     1
#> Cryptophytes      0.0000000 0.0000     1
#> Diatoms-B         0.0000000 0.0000     1
#> Dinoflagellates-A 0.0000000 0.0000     1
#> Haptophytes       0.0000000 0.0000     1
#> Pelagophytes      0.0000000 0.0000     1
#> Syn               1.1273247 0.0000     1
Results$`Class abudances`
#> NULL
Results$Figure
```

<img src="man/figures/README-example-1.png" width="100%" />
