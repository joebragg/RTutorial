# Data Science & R Programming
Joe Bragg  
Sunday, September 14, 2014  

## What is Data Science?

Data science is the study of the generalizable **extraction of knowledge** from data. The key word is **science**.

It incorporates varying elements and builds on techniques and theories from many fields, including signal processing, mathematics, probability models, machine learning, statistical learning, computer programming, data engineering, pattern recognition and learning, visualization, uncertainty modeling, data warehousing, and high performance computing with the goal of **extracting meaning** from data and creating data products.

http://en.wikipedia.org/wiki/Data_science

## Steps Data Scientists Use

* Define the question/objective
* Define the ideal data set
* Determine what data can be accessed
* Obtain the data
* Clean the data
* Explore and summarize the data
* Construct statistical models and predictions
* Interpret results
* Challenge results
* Write up results
* Create reproducible code
* Distribute results to other people (Peer Review)

## Data Scientist Tools

* Programming language(s)
    + R, Python, T-SQL, C/C++, etc.
    
* Programming modules, packages, add-ons and Application Programming Interfaces (APIs)

* Documentation Tools
    + Markdown, R Markdown, Python Markdown, HTML, PDF, etc.
    
* Version Control System (VCS)
    + Git, Subversion, CVS, etc.
    
* Distribution/publishing system
    + GitHub, SourceForge, Google Code, etc.
    
# R Programming

## R "Atomic" Classes (Data Types)
    
+---------------+---------------+-------------------------------------+
| Data Type     | Example       | Comments                            |
+===============+===============+=====================================+
|Character      | "A", "f", "4",|                                     |
|               | "$", "Hello"  |                                     |
+---------------+---------------+-------------------------------------+
|Numeric        | 2.10, 4, -2,  | - Inf = 1/0                         |
|(real numbers) | Inf, NaN      | - NaN = 0/0                         |
+---------------+---------------+-------------------------------------+
|Integer        |12**L**, 0:8   | - L makes the number an integer     |
|               |               | - 0:8 = 0 1 2 3 4 5 6 7 8           |
+---------------+---------------+-------------------------------------+
|Complex        |1+2i, 4i       | - Re() function gives real part     |
|               |               | - Im() function gives imaginary part|
+---------------+---------------+-------------------------------------+
|Logical        |TRUE or FALSE, |                                     |
|               |T or F         |                                     |
+---------------+---------------+-------------------------------------+
    
## Vectors

Vectors can only contain objects of the same class.
    

```r
vn<-c(4,2.1,5,6.4,7)  ## numeric vector
print(vn)
```

```
## [1] 4.0 2.1 5.0 6.4 7.0
```


```r
vc<-c("d","S","12","Hello")  ## character vector
vc  ## Short for print(vc)
```

```
## [1] "d"     "S"     "12"    "Hello"
```


```r
qa<-c(T,F,T,T,F,F,T,F,T,T)
names(qa)<-c("Q1","Q2","Q3","Q4","Q5","Q6","Q7","Q8","Q9","Q10") # Adding Names
qa
```

```
##    Q1    Q2    Q3    Q4    Q5    Q6    Q7    Q8    Q9   Q10 
##  TRUE FALSE  TRUE  TRUE FALSE FALSE  TRUE FALSE  TRUE  TRUE
```


## Matrices

Like a vector, a matrix can only contain objects of the same class.
    

```r
m <- matrix(1:12, nrow = 3, ncol = 4)  ##interger matrix
dimnames(m) <- list(c("x", "y","z"), c("a", "b","c","d")) #Adding row & column names
m
```

```
##   a b c  d
## x 1 4 7 10
## y 2 5 8 11
## z 3 6 9 12
```


```r
class(m[1,1])
```

```
## [1] "integer"
```


```r
m["y","b"]
```

```
## [1] 5
```

## Lists

Lists can contain objects of different classes
    

```r
l<-list(A1=4,A2="Median",A3=TRUE,A4=1+2i)
l
```

```
## $A1
## [1] 4
## 
## $A2
## [1] "Median"
## 
## $A3
## [1] TRUE
## 
## $A4
## [1] 1+2i
```
## Factors

Factors are used to represent qualitative data (Male/Female, Country, State, Color, Texture, etc.) and they can be ordered or unordered.


```r
states<-factor(c("Texas","Arkansas","Oklahoma","New Mexico","Louisiana"))
states
```

```
## [1] Texas      Arkansas   Oklahoma   New Mexico Louisiana 
## Levels: Arkansas Louisiana New Mexico Oklahoma Texas
```

```r
tf<-factor(c(T,F,T,T,F,F,T))  ##unordered
tf
```

```
## [1] TRUE  FALSE TRUE  TRUE  FALSE FALSE TRUE 
## Levels: FALSE TRUE
```

```r
tf<-factor(c(T,F,T,T,F,F,T),levels=c(T,F))  ##ordered
tf
```

```
## [1] TRUE  FALSE TRUE  TRUE  FALSE FALSE TRUE 
## Levels: TRUE FALSE
```

## Data Frames

Data Frames are used to store tabular data.

```r
team<-data.frame(Name=c("John","Amy","Bob","Mike","Sue"),Number=c(3,2,6,17,8),
                 Active=c(T,T,F,T,F))
team
```

```
##   Name Number Active
## 1 John      3   TRUE
## 2  Amy      2   TRUE
## 3  Bob      6  FALSE
## 4 Mike     17   TRUE
## 5  Sue      8  FALSE
```


```r
ncol(team)
```

```
## [1] 3
```


```r
nrow(team)
```

```
## [1] 5
```

## Data Frames Continued


```r
names(team)
```

```
## [1] "Name"   "Number" "Active"
```


```r
team[1,]
```

```
##   Name Number Active
## 1 John      3   TRUE
```


```r
team[2,2]
```

```
## [1] 2
```

## Data Frames Continued


```r
team["Name"]
```

```
##   Name
## 1 John
## 2  Amy
## 3  Bob
## 4 Mike
## 5  Sue
```


```r
team$Name[2:4]
```

```
## [1] Amy  Bob  Mike
## Levels: Amy Bob John Mike Sue
```


```r
class(team$Name)
```

```
## [1] "factor"
```

## Subsetting


```r
vc
```

```
## [1] "d"     "S"     "12"    "Hello"
```


```r
vc[2:4] # Subsetting a vector
```

```
## [1] "S"     "12"    "Hello"
```


```r
m
```

```
##   a b c  d
## x 1 4 7 10
## y 2 5 8 11
## z 3 6 9 12
```


```r
m["y",3:4] # Subsetting a matrix
```

```
##  c  d 
##  8 11
```

## Subsetting Continued


```r
team
```

```
##   Name Number Active
## 1 John      3   TRUE
## 2  Amy      2   TRUE
## 3  Bob      6  FALSE
## 4 Mike     17   TRUE
## 5  Sue      8  FALSE
```


```r
team[team$Active==FALSE, ] # Subsetting the "team" data frame on inactive players
```

```
##   Name Number Active
## 3  Bob      6  FALSE
## 5  Sue      8  FALSE
```

## Slide with R Code and Output


```r
summary(cars)
```

```
##      speed           dist    
##  Min.   : 4.0   Min.   :  2  
##  1st Qu.:12.0   1st Qu.: 26  
##  Median :15.0   Median : 36  
##  Mean   :15.4   Mean   : 43  
##  3rd Qu.:19.0   3rd Qu.: 56  
##  Max.   :25.0   Max.   :120
```

## Slide with Plot

![plot of chunk unnamed-chunk-27](./RTutorial_files/figure-html/unnamed-chunk-27.png) 

