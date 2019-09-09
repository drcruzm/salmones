

## Descripción de los Datos

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
setwd("/cloud/project")
# dir()
library(ggplot2)
```

## Descripción de los Datos

```{r }
knitr::opts_chunk$set(echo = TRUE)
View(mpg) 
attach(mpg)
head(mpg)
str(mpg)
```

## Aplicando ggplot2

```{r}

d <- ggplot(data = mpg, aes(x=displ,y=hwy)) # elementos de base
d + geom_point()

d + geom_point(size=3,shape=23, color="red",fill="yellow")

ggsave("fig.pdf",dpi = 400)
```

## Aplicando aes

```{r}
d <- ggplot(data = mpg, aes(x=displ,y=hwy)) # GRAFICA DE BASE

d + geom_point(aes(color=class),size=3)

d + geom_point(aes(color=(displ <= 4) ), size=3)
    
```


```{r}
d <- ggplot(data = mpg, aes(x=cyl,y=hwy)) # GRAFICA DE BASE

d + geom_point(aes(color=trans), size=3)

dd <- ggplot(data = mpg, aes(x=displ,y=hwy,col=manufacturer))
dd + geom_point(size=3)
```


```{r}
d <- ggplot(data = mpg, aes(x=factor(manufacturer),y=hwy)) # GRAFICA DE BASE

d + geom_boxplot()

```


```{r}
d <- ggplot(data = mpg, aes(x=hwy,y=factor(model)))# GRAFICA DE BASE

d + geom_point(size=3,col="blue")

```
