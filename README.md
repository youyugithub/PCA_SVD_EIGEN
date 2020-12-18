# PCA SVD EIGEN

In R:
```
X<-cbind(rnorm(100),rnorm(100),rnorm(100))

# eigen
eig_vec<-eigen(t(X)%*%X/99)$vectors
eig_val<-eigen(t(X)%*%X/99)$values
max(abs(eig_vec%*%diag(eig_val)%*%t(eig_vec)-t(X)%*%X/99)) # check

# svd
svd_d<-svd(X)$d
svd_u<-svd(X)$u
svd_v<-svd(X)$v
max(abs(svd_u%*%diag(svd_d)%*%t(svd_v)-X)) # check

# 
pca_sdev<-prcomp(X,center=F)$sdev
pca_rotn<-prcomp(X,center=F)$rotation
pca_x<-prcomp(X,center=F)$x
(pca_x/svd_u)
(pca_sdev/svd_d)
max(abs(pca_x%*%t(pca_rotn)-X)) # check
```
