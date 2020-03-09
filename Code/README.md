getwd()

#Importing Raw Agriculture Data of Indonesia#
agr.data<-read.csv("C:/Users/Dell/Documents/Indonesia/DWBI/Agriculture Data.csv",header=TRUE)
agr.data

#Clean Columns & rows of Agriculture Data Of Indonesia#
agr.data1<-agr.data[-(7:13),c(2,5:13)]
agr.data1

#changing row to Year of agriculture Data#
names(agr.data1)[2:10]<-c(2009,2010,2011,2012,2013,2014,2015,2016,2017)
agr.data1

#creating a new column of id of Agriculture dataset#
Agr_id<-c("agrland","agrexp","agremp","agrfert","foodexp","gdp")
Agr_id

#Adding that column to dataset#
agr.data2=cbind(Agr_id,agr.data1)
agr.data2

#creating Matrix from dataframe and transposing it#
as.matrix(agr.data2)
agr.data2.t=t(agr.data2)
agr.data2.t

#Transforming matrix to dataframe#
as.data.frame(agr.data2.t)
agr.data3<-agr.data2.t
agr.data3

#Doing Modification in column and row by renaming it and deleting NA#
agrdata4<-agr.data3[-c(1:2),]
agrdata4
colnames(agrdata4)[1]<-"agrland"
colnames(agrdata4)[2]<-"agrexp"
colnames(agrdata4)[3]<-"agremp"
colnames(agrdata4)[4]<-"agrfert"
colnames(agrdata4)[5]<-"foodexp"
colnames(agrdata4)[6]<-"gdp"
agrdata4
rownames(agrdata4)<-c(1:9)
agrdata4
agr5<-agrdata4[-(10:49),]
agr5

#Creating previous column of country and year#
year<-c(2009,2010,2011,2012,2013,2014,2015,2016,2017)
year
Country[1:9]<-c("IDN")
Country

#Adding that column to dataset#
agr6=cbind(Country,year,agr5)
agr6

#Importing Data from data frame to csv#
setwd("C:/Users/Dell/Documents/Indonesia/DWBI")
write.csv(agr6,"Agrdata.csv")
write.csv(agr6)


#Importing Raw Crop Yields of Indonesia#
cyd<-read.csv("C:/Users/Dell/Documents/Indonesia/DWBI/crop yields.csv",header=TRUE)
cyd

#Clean Columns of crop yields Of Indonesia#
cyd1<-cyd[,-c(2,5,8)]
cyd1

#Creating Dataframe for matrix#

df=cyd1[(1:9),5]
df
df1=cyd1[(10:18),5]
df1
df2=cyd1[(19:27),5]
df2
df3=cyd1[(28:36),5]
df3

#Creating Matrix of dataframe and adding year values#
as.matrix(df)
as.matrix(df1)
as.matrix(df2)
as.matrix(df3)

Cropyields=df+df1+df2+df3
Cropyields

#again transforming matrix into dataframe#
as.data.frame(Cropyields)

#Clean & renaming Columns & rows of Crop Yields Of Indonesia#
cy2<-cyd1[-(10:36),c(1:4)]
cy2

names(cy2)[1]<-c("Country")
names(cy2)[4]<-c("Year")
cy2[,2]<-c("RWMR")
cy2


#Adding calculated dataframe column to dataset#
cy3=cbind(cy2,Cropyields)
cy3


#Importing Data from data frame to csv#
setwd("C:/Users/Dell/Documents/Indonesia/DWBI")
write.csv(cy3,"Cyields.csv")
write.csv(cy3)

#Importing Raw Cultivated Asset of Indonesia#
ca<-read.csv("C:/Users/Dell/Documents/Indonesia/DWBI/Cultivated Asset.csv",header=TRUE)
ca

#Clean Columns of cultivated asset Of Indonesia#
ca1<-ca[,-c(2,5)]
ca1

names(ca1)[1]<-c("Country")
names(ca1)[4]<-c("Year")
ca1

#Importing Data from data frame to csv#
setwd("C:/Users/Dell/Documents/Indonesia/DWBI")
write.csv(ca1,"Casset.csv")
write.csv(ca1)

#Importing Raw Urban Population of Indonesia#
up<-read.csv("C:/Users/Dell/Documents/Indonesia/DWBI/Urban Population.csv",header=TRUE)
up

#Clean Columns & renaming of urban population Of Indonesia#
up1<-up[-c(1:6,16),]
up1

names(up1)[1]<-c("Year")
names(up1)[2]<-c("Urban Population")
rownames(up1)<-c(1:9)
up1

Country[1:9]<-c("IDN")
Country

#Adding that column to dataset#
up2=cbind(Country,up1)
up2

#Importing Data from data frame to csv#
setwd("C:/Users/Dell/Documents/Indonesia/DWBI")
write.csv(up2,"urbpop.csv")
write.csv(up2)
