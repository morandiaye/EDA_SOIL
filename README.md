# EDA_SOIL
Exploratory data analysis provided by SOTER

This dataset is provided by SOTER and I have make some cleaning in order to obtain data in which i can carry out somme exploratory data analysis without any problems.

## Import dataset
```{r,data_sol,cache=TRUE}
data_sol<-read.csv2("C:\\Users\\pc\\Downloads\\Modelisation_Soter_data_Senegal-master\\Modelisation_Soter_data_Senegal-master\\donnees soter.csv")

```
## Structure of dataset
let's take a look in the data set
```{r,eval=TRUE}
str(data_sol)
```
## Cut some variable
To make sure that the other analysis run without problem we decided to cut some variable that doesn't use in the future .
```{r}
varq<-data_sol[,c("sable_total","Limon","Argile","PH","PHKC","EXCA","EXMG","EXNA","epais_hor","total_carbone","CECS")]
```
we use summary to take a look in certain parameter of differents variables 
```{r,echo=TRUE}
print(summary(varq))
```
check the normality of some variables with function qqnorm and qqline
```{r}
qqnorm(varq$Argile)
qqline(varq$Argile)
```
I make this for one argile we can make this for th othe r variable in the dataset
```{r}
mod_1<-lm(EXMG~Limon+CECS,data=na.omit(varq))
summary(mod_1)
```



