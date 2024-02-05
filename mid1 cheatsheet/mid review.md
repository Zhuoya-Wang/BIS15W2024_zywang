---
title: "BIS_015L_Mid_review"
author: "Zhuoya Wang"
date: "2024-01-30"
output: 
  html_document: 
    keep_md: true
---




# Lab 2.1 Objects, Classes & NAs

```r
##### Lab 2

# sum(A, B, C)
# Mean(c(A, B, C)) # ABC are the object names
# class() # check the type of object
# is.xx() # check if the type of object is xx ### output: True or False
# as.xx() # create an object specified as xx

##### Missing Values

# is.na() # check every element in an object (number of TF = # of elements)

# anyNA() # check if the object has NA inside (only T/F)

# mean(objectname, na.rm = T/F) # caculate the mean of object, na.rm = remove NA

##### Vectors

# my_vector <- c(10, 20, 30) #numeric vector

# days_of_the_week <- c("Monday", "Tuesday", "Wednesday", "Thrusday", "Friday", "Saturday", "Sunday") # Characters always have quotes


# days_of_the_week[3] # the third element of that vector, use `[]` to pull out elements in a vector

# eg: my_vector_sequence[my_vector_sequence <= 10] # get the values in m_v_s that <= 10
```


#Lab 2.2 Vectors and Data Matrices

```r
##### Matrices
# provide vectors
Philosophers_Stone <- c(317.5, 657.1)
Chamber_of_Secrets <- c(261.9, 616.9)
Prisoner_of_Azkaban <- c(249.5, 547.1)
Goblet_of_Fire <- c(290.0, 606.8)
Order_of_the_Phoenix <- c(292.0, 647.8)
Half_Blood_Prince <- c(301.9, 632.4)
Deathly_Hallows_1 <- c(295.9, 664.3)
Deathly_Hallows_2 <- c(381.0, 960.5)


## list values by names
box_office <- c(Philosophers_Stone, Chamber_of_Secrets, Prisoner_of_Azkaban, Goblet_of_Fire, Order_of_the_Phoenix, Half_Blood_Prince, Deathly_Hallows_1, Deathly_Hallows_2)
box_office
```

```
##  [1] 317.5 657.1 261.9 616.9 249.5 547.1 290.0 606.8 292.0 647.8 301.9 632.4
## [13] 295.9 664.3 381.0 960.5
```

```r
## make matric by row
harry_potter_matrix <- matrix(box_office, nrow = 8, byrow = T)## organize it by rows



# Provide column names
region <- c("US", "non-US")
region
```

```
## [1] "US"     "non-US"
```

```r
# Provide row names
titles <- c("Philosophers_Stone", "Chamber_of_Secrets", "Prisoner_of_Azkaban", "Goblet_of_Fire", "Order_of_the_Phoenix", "Half_Blood_Prince", "Deathly_Hallows_1", "Deathly_Hallows_2")
titles
```

```
## [1] "Philosophers_Stone"   "Chamber_of_Secrets"   "Prisoner_of_Azkaban" 
## [4] "Goblet_of_Fire"       "Order_of_the_Phoenix" "Half_Blood_Prince"   
## [7] "Deathly_Hallows_1"    "Deathly_Hallows_2"
```

```r
# Add col names to the matrices
colnames(harry_potter_matrix) <- region

# Add row names to the matrices
rownames(harry_potter_matrix) <- titles



##### Row sums
global <- rowSums(harry_potter_matrix)
global
```

```
##   Philosophers_Stone   Chamber_of_Secrets  Prisoner_of_Azkaban 
##                974.6                878.8                796.6 
##       Goblet_of_Fire Order_of_the_Phoenix    Half_Blood_Prince 
##                896.8                939.8                934.3 
##    Deathly_Hallows_1    Deathly_Hallows_2 
##                960.2               1341.5
```

```r
### Add new col to the matrices by "cbind()" 
all_harry_potter_matrix <- cbind(harry_potter_matrix, global) ## show new title directly
all_harry_potter_matrix
```

```
##                         US non-US global
## Philosophers_Stone   317.5  657.1  974.6
## Chamber_of_Secrets   261.9  616.9  878.8
## Prisoner_of_Azkaban  249.5  547.1  796.6
## Goblet_of_Fire       290.0  606.8  896.8
## Order_of_the_Phoenix 292.0  647.8  939.8
## Half_Blood_Prince    301.9  632.4  934.3
## Deathly_Hallows_1    295.9  664.3  960.2
## Deathly_Hallows_2    381.0  960.5 1341.5
```

```r
# rbind() to add new row to a matrices

# colSums() calculates the col total

# matrice[a,b] # a is row, b is col

all_harry_potter_matrix[1,3] ## 1st row, 3rd col value
```

```
## [1] 974.6
```

```r
all_harry_potter_matrix[1:3] ## 1st row, 3 values in that row
```

```
## [1] 317.5 261.9 249.5
```

```r
colMeans(all_harry_potter_matrix) # all column mean
```

```
##       US   non-US   global 
## 298.7125 666.6125 965.3250
```

```r
mean(all_harry_potter_matrix[,3]) # single column mean
```

```
## [1] 965.325
```

```r
# rowMeans()
```



# Lab 3.1 Data Frames

```r
 library("tidyverse")
```

```
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.2     ✔ readr     2.1.4
## ✔ forcats   1.0.0     ✔ stringr   1.5.0
## ✔ ggplot2   3.4.2     ✔ tibble    3.2.1
## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
## ✔ purrr     1.0.1     
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

```r
## data.frame(A, B,C) # make a data frame for three vectors

Sex <- c("male", "female", "male")
Length <- c(3.2, 3.7, 3.4)
Weight <- c(2.9, 4.0, 3.1)

hbirds <- data.frame(Sex, Length, Weight)
hbirds
```

```
##      Sex Length Weight
## 1   male    3.2    2.9
## 2 female    3.7    4.0
## 3   male    3.4    3.1
```

```r
names(hbirds) # show variables names
```

```
## [1] "Sex"    "Length" "Weight"
```

```r
dim(hbirds) # show dimension of hbirds data
```

```
## [1] 3 3
```

```r
str(hbirds) # show data strucutre
```

```
## 'data.frame':	3 obs. of  3 variables:
##  $ Sex   : chr  "male" "female" "male"
##  $ Length: num  3.2 3.7 3.4
##  $ Weight: num  2.9 4 3.1
```

```r
# Let's use lowercase names when we create the data frame. 
# We just changed to lowercase here, but we could use any names we wish.  

hbirds <- data.frame(sex = Sex, length = Length, weight_g = Weight)
##  rename-- new.name = old.name

# rename (new = old)
# rename(mammals, genus = "Genus", afr = "AFR", maxlife = "max. life", littersyears = "litters/year")

# Adding a new row
new_bird <- c("female", 3.6, 3.9)
new_bird
```

```
## [1] "female" "3.6"    "3.9"
```

```r
hbirds<- rbind(hbirds, new_bird)
hbirds
```

```
##      sex length weight_g
## 1   male    3.2      2.9
## 2 female    3.7        4
## 3   male    3.4      3.1
## 4 female    3.6      3.9
```

```r
# Adding a new col by $
hbirds$neighborhood <- c("lakewood", "brentwood", "lakewood", "scenic Heights")
hbirds
```

```
##      sex length weight_g   neighborhood
## 1   male    3.2      2.9       lakewood
## 2 female    3.7        4      brentwood
## 3   male    3.4      3.1       lakewood
## 4 female    3.6      3.9 scenic Heights
```

```r
## Writing data to file-- save hbirds with name hbirds_data.csv

write.csv(hbirds, "hbirds_data.csv", row.names = FALSE) ##csv = common separate value

# We use `row.names = FALSE` to avoid row numbers from printing out. 
```


# Lab 3.2 Data Frames


```r
getwd()# check the working directory
```

```
## [1] "/Users/zhuoyawang/Desktop/GitHub/BIS15W2024_zywang/mid1 cheatsheet"
```

```r
#hot_springs <- read_csv("lab3/hsprings_data.csv") # Load the file
#class(hot_springs$scientist)
#hot_springs$scientist <- as.factor(hot_springs$scientist) # change the class of 'scientist' variable to factor

#levels(hot_springs$scientist) # show level of that


# glimpse() another way to show strucutre
# summary() summary our data frame
# head() first rows of data
# tail() last rows of data
# table(hot_springs$scientist)# produces counts of the number of observations in a variable
```



# Lab 4.1 select()  extract variables (col)

```r
# select(fish, "lakeid", "scalelength") # select(dataname, "var1", "var2") to pull out the iterest variables 

# select(fish, fish_id:length) ## select from the start_col to end_col

# select(fish, -"fish_id", -"annnumber", -"length", -"radii_length_mm") # minus operator is going to select everything expect the select variables.   

# select(fish, contains("length")) extract the variables whose name contains 'length'

# select(fish, starts_with("radii")) Select columns that start with a character string  
# select(fish, matches("a.+er"))  a column contains a letter (in this case "a") followed by a subsequent string (in this case "er") -- > "annnunumber 


# select_if(fish, is.numeric) extract numeric variables in fish dataset

# select_if(fish, ~!is.numeric(.)) # select if in the fish data look across all the data, do not select all numeric variables. ! is Not

# select_all(mammals, tolower) #use lowercase to keep
```

Options to select columns based on a specific criteria include:  
1. ends_with() = Select columns that end with a character string  
2. contains() = Select columns that contain a character string  
3. matches() = Select columns that match a regular expression  
4. one_of() = Select columns names that are from a group of names  



# Lab 4.2 filter() -- extract row from dataset

```r
# filter(fish, lakeid == "AL")# select the rows which contain AL## 2equal sign and ""

# !=  is not equal 

# filter(fish, length %in% c(167, 175)) # choose the observation with length = 167 and length = 175

# filter(fish, between(scalelength, 2.5, 2.55)) #filter the observation with scalelength in between (2.5 2.55)   between a range --> between(variable_name, range)

# filter(fish, near(radii_length_mm, 2, tol = 0.2))# tol = tolerance; extract observations "near" a certain value with tolerance range

# filter(fish, lakeid == "AL" & length > 350) From Al or length > 350 (more rows than use "and")


# filter(fish, length > 400, (scalelength > 11 | radii_length_mm > 8)). we filter out the fish with a length over 400 and a scale length over 11 or a radii length over 8.
```

+`filter()` allows all of the expected operators; i.e. >, >=, <, <=, != (not equal), and == (equal)

'|' is or; '&' is and

Rules:  
+ `filter(condition1, condition2)` will return rows where both conditions are met.  
+ `filter(condition1, !condition2)` will return all rows where condition one is true but condition 2 is not.  
+ `filter(condition1 | condition2)` will return rows where condition 1 or condition 2 is met.  
+ `filter(xor(condition1, condition2)` will return all rows where only one of the conditions is met, and not when both conditions are met.  


# Lab 5.1 --> filter 2.0

```r
library(janitor)
```

```
## 
## Attaching package: 'janitor'
```

```
## The following objects are masked from 'package:stats':
## 
##     chisq.test, fisher.test
```

```r
# clean_names() change variables' names to lower cases

# primate <- filter(new_mammals, genus %in% c("Lophocebus" , "Erythrocebus"  ,"Macaca")) ## within is %in% 选择有L，E，M的rows
```

# Lab 5.2 --> Pipes, arrange(), mutate(), and if_else()



