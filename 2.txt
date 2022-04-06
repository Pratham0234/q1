data("iris")
head(iris)
names(iris)
a<-subset(iris,select=c(-Species))
a
b<-kmeans(a,3)
b
data<-a
wss<-sapply(1:15,function(k){kmeans(data,k)$tot.withinss})
wss
plot(1:15,wss,type="b",pch=19,frame=FALSE,xlab="Number of clusters k",yab="Total within cluster sumof square")
clusplot(a,b$cluster,color=TRUE,shade=TRUE,labels=2,lines=0)
b$cluster
b$centers
cl<-hclust(dist(iris[,3:4]))
plot(cl)
cl_cut<-cutree(cl,3)
table(cl_cut,iris$Species)
