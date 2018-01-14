# Directional Co-clustering (an R package)

###### Please install the following packages first:
- devtools
- Bessel 
- mclut
- Matrix

###### Install DirecCoclus
- install_github("DirecCoclus", "dbmovMFs")

###### Preparing the data
- Download the cstr dataset avaible in In folder Data of DirecCoclus repository
- Install R.matlab package, necessary for the next step
- Load data: cstr <- readMat("your local path to cstr.mat"), 

###### Fit dbmovMF to the data, see documentation for parameter specification
- res_saemb = dbmovMF(cstr$fea,k=4,max_iter = 150,n_init = 10,fit_algo="SAEMb")

###### Evaluate the resulting row clustering using ARI (mclust package is needed for this step)
- adjustedRandIndex(res_saemb$rowcluster-1,cstr$gnd)

###### Plot the classification log-likelihood
- plot(res_saemb$ll[1:res_saemb$iter],type = "l")
