EXAMEN\_PARCIAL
================
ANTONI ESQUIVEL
03/01/2022

# PREGUNTA 01

***CALCULAR LOS VALORES APROXIMADOS DE***

``` r
m <- (0.3*0.15)/(0.3*0.15+0.2*0.8+0.5*0.12)
cat("El valor aproximado es de",m)
```

    ## El valor aproximado es de 0.1698113

``` r
m <- (5**6/factorial(6))*(exp(1))**(-5)
cat("El valor aproximado es de",m)
```

    ## El valor aproximado es de 0.1462228

# PREGUNTA 02

***REALIZAR LAS SIGUIENTE SUMAS***

**1+2+3+4+5…….+1000**

``` r
df<-c(1:1000)
sum(df)
```

    ## [1] 500500

**1+2+4+8+16……+1024**

``` r
i <- NULL; r <- NULL; aux <- NULL
for (i in 0:10) {
  aux <- 2**i; r <- c(r,aux)
}
suma_02 <- sum(r)
cat("La suma de los 10 primeras potencias de dos es", suma_02)
```

    ## La suma de los 10 primeras potencias de dos es 2047

# PREGUNTA 03

**PRIMERO LEEMOS EL ARCHIVO rmd**

``` r
load("ei1012-1516-la-s1-datos.RData")
```

***El vector grupo representa el grupo al que pertenece una serie de
alumnos***

**¿Cuántos alumnos tiene**

``` r
cat("El salón tiene", length(grupo), "alumnos")
```

    ## El salón tiene 192 alumnos

**¿En que posición del vector esta la letra “A”?**

``` r
cat("Estan en la", which(grupo == "A"), "alumnos")
```

    ## Estan en la 2 8 17 21 28 84 101 108 111 115 123 136 190 192 alumnos

# PREGUNTA 04

***El vector nota representa la nota de un examen de los alumnos que***
***están en los grupos del vector grupo.***

**¿Cuánto suman todas las notas?**

``` r
cat("las notas suman", sum(nota))
```

    ## las notas suman 962

**¿Cuál es la media aritmetica de las notas?**

``` r
cat("Su promedio es igua a", mean(nota))
```

    ## Su promedio es igua a 5.010417

**¿En que posición están las notas mayores a 7?**

``` r
cat("Estan en la posición", which(nota > 7))
```

    ## Estan en la posición 81 103 120 151

**Visualiza las notas en orden de mayor a menor**

``` r
orden <- sort(nota, decreasing = TRUE)
cat("El orden decreciente de las notas es", head(orden))
```

    ## El orden decreciente de las notas es 7.7 7.5 7.4 7.2 7 6.9

``` r
cat("El orden decreciente de las notas es", head(sort(nota, decreasing = TRUE)))
```

    ## El orden decreciente de las notas es 7.7 7.5 7.4 7.2 7 6.9

**En que posición está la máxima nota**

``` r
cat("Esta en la posición", which.max(nota))
```

    ## Esta en la posición 120

# PREGUNTA 05

***A partir de los vectores grupo y nota definidos***

**Suma las notas de los 10 primeros alumnos del vector**

``` r
cat("La Suma es", sum(nota[1:10]))
```

    ## La Suma es 51.8

**¿Cuántos alumnos hay del grupo C**

``` r
cat("Hay", length(grupo[grupo == "C"]))
```

    ## Hay 39

**¿Cuántos alumnos aprobaron?**

``` r
cat("Hay", length(nota[nota > 5.5]), "alumnos aprobados")
```

    ## Hay 60 alumnos aprobados

**¿Cuántos alumnos del grupo B aprobaron?**

``` r
library(tidyverse)
library(dplyr)
library(pacman)
```

``` r
dfclase <- data.frame(grupo, nota) %>% as_tibble() 
```

``` r
GrupoB <- dfclase %>% 
  dplyr::filter(nota > 5.5 & grupo == "B") 
cat("El numero de alumnos aprobados en el grupo B es:", length(GrupoB$grupo))
```

    ## El numero de alumnos aprobados en el grupo B es: 8

**¿Qué Porcentaje de alumnos del grupo C aprobaron?**

``` r
GrupoC <- dfclase %>% 
  dplyr::filter(nota > 5.5 & grupo == "C") 

cat("El porcentaje de alumnos aprobado del aula C son:",
      ((length(GrupoC$grupo)/length(dfclase$grupo))*100),"%")
```

    ## El porcentaje de alumnos aprobado del aula C son: 9.375 %

**¿De que grupo son la máxima y minima nota de las muestras?**

``` r
Notmax <- dfclase %>% 
   dplyr::arrange(desc(nota))

Notmin <- dfclase %>% 
   dplyr::arrange(nota)

cat("La nota máxima le pertenece al grupo", Notmax$grupo[1], 
    "Y la nota mínima le pertenece al grupo", Notmin$grupo[1])
```

    ## La nota máxima le pertenece al grupo E Y la nota mínima le pertenece al grupo B
