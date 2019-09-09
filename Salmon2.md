    ---
    title: "analisis data Salmones"
    author: "Dr. Víctor Cruz"
    date: "9/9/2019"
    output: ioslides_presentation
    runtime: shiny
    ---

## Instalando librerias

    ```{r setup, include=True}
    knitr::opts_chunk$set(echo = T)
    library(car) # Librerias a utilizar
    # library() # Librerias a utilizar

    ```

## Lectura de Datos

```{r}
salmon1 <- read.csv("https://www.dropbox.com/s/8wl1wlmm2ourj7c/salmones.csv?dl=1",header = T, sep = ",",dec = ".")
head(salmon1)
```

## Arreglando la base

```{r}
salmon1$G = factor(salmon1$G)

str(salmon1)

salmon1$G = factor(salmon1$G,labels=c("King","Coho","Keta"))

names(salmon1)<-c("Weight","Species") ##Nombres para las variables

head(salmon1)
attach(salmon1)

```

## clasificando las especies por categorias

```{r}
summary(salmon1) 
```

## Graficando categorias y valores extremos

    ```{r, echo = TRUE }
    Boxplot(Weight,Species) #Reporta registros fuera de rango
    ```

## Analisis de Outliners 

    ```{r}
    salmon1[1386,] # numero de registo ?

    ext <- Boxplot(Weight,Species)
    salmon1[ext,]
    ```

## Guardamos los datos antes de cambiarlos

    ```{r}
    dump("salmon1", "/cloud/project/DataSalmon.R")

    ```

## to reload el dataset, se ejecuta

    ```{r}
    source("/cloud/project/DataSalmon.R")
    View(salmon1)
    ```

## Eliminando valores negativos

```{r}
# subset command in r - conditional indexing
salmonesC <- salmon1[Weight > 0,]

summary(salmonesC)
attach(salmonesC)
```

# Analizando y graficando los valores corregidos

```{r}
ggplot(salmonesC,aes(Species,Weight))+geom_boxplot()

with(salmonesC,tapply(Weight,Species,summary))

ggsave("clean.png",dpi=400)

```
**BACK TO HOME :**  [Código](/Salmon2.md) 

