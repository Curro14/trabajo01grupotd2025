---
title: "Trabajo01"
author: "Marta Martín Fernández"
date: "2025-10-15"
output: 
  pdf_document: default
  html_document: default
#install.packages('tinytex')
#tinytex::install_tinytex(bundle = 'TinyTeX-2') # ocupa aprox. 1.8Gb  
---



# PROBLEMA 1


#### Nos ha tocado un cupón de 10.000 euros y queremos encontrar la mejor opción para utilizarlo. 


#### ALTERNATIVAS:
    
    
$$
\begin{array}{c}
A_1: \text{Ahorrar todo el dinero para una inversión en el futuro.}\\
A_2: \text{Gastar la mayoría del dinero en un viaje en familia.}\\
A_3: \text{Gastar la mitad del dinero en comprar un coche de segunda mano.}
\end{array}
$$

    
#### Como no sé cómo será mi economía en el futuro, observamos tres posibles ESTADOS:


$$
\begin{array}{c}
E_1:\ \text{Mi situación económica mejora.}\\
E_2:\ \text{Mi economía se mantiene estable.}\\
E_3:\ \text{Mi economía empeora.}
\end{array}
$$


#### TABLA DE DECISIÓN 



$$
\begin{array}{lccc}
\textbf{Alternativa / Estado} & E_1: \text{Mejora} & E_2: \text{Estable} & E_3: \text{Empeora} \\[4pt]
A_1: \text{Ahorro} & 15000 & 11000 & 8000 \\[4pt]
A_2: \text{Viaje familiar} & 13000 & 9000 & 5000 \\[4pt]
A_3: \text{Coche} & 12000 & 10000 & 6000
\end{array}
$$



Vamos a resolver los distintos métodos de decisión bajo incertidumbre para ver cual es la mejor opción.



``` r
tablaX = crea.tablaX(c(15000,11000,8000,13000,9000,5000,12000,10000,6000), numalternativas = 3, numestados = 3, nb_alternativas = c("Ahorro","Viaje","Coche"), nb_estados = c("Mejora", "Estable","Empeora"))

tablaX
```

```
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
```


### CRITERIO DE WALD



```
## $criterio
## [1] "Wald"
## 
## $metodo
## [1] "favorable"
## 
## $tablaX
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
## 
## $ValorAlternativas
## Ahorro  Viaje  Coche 
##   8000   5000   6000 
## 
## $ValorOptimo
## [1] 8000
## 
## $AlternativaOptima
## Ahorro 
##      1
```

```
## $criterio
## [1] "Wald"
## 
## $metodo
## [1] "desfavorable"
## 
## $tablaX
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
## 
## $ValorAlternativas
## Ahorro  Viaje  Coche 
##  15000  13000  12000 
## 
## $ValorOptimo
## [1] 12000
## 
## $AlternativaOptima
## Coche 
##     3
```


### CRITERIO OPTIMISTA



```
## $criterio
## [1] "Optimista"
## 
## $metodo
## [1] "favorable"
## 
## $tablaX
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
## 
## $ValorAlternativas
## Ahorro  Viaje  Coche 
##  15000  13000  12000 
## 
## $ValorOptimo
## [1] 15000
## 
## $AlternativaOptima
## Ahorro 
##      1
```


### CRITERIO DE HURWICZ



```
## $criterio
## [1] "Hurwicz"
## 
## $alfa
## [1] 0.7
## 
## $metodo
## [1] "favorable"
## 
## $tablaX
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
## 
## $ValorAlternativas
## Ahorro  Viaje  Coche 
##  12900  10600  10200 
## 
## $ValorOptimo
## [1] 12900
## 
## $AlternativaOptima
## Ahorro 
##      1
```


### CRITERIO SAVAGE



```
## $criterio
## [1] "Savage"
## 
## $metodo
## [1] "favorable"
## 
## $tablaX
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
## 
## $Mejores
##  Mejora Estable Empeora 
##   15000   11000    8000 
## 
## $Pesos
##        Mejora Estable Empeora
## Ahorro      0       0       0
## Viaje    2000    2000    3000
## Coche    3000    1000    2000
## 
## $ValorAlternativas
## Ahorro  Viaje  Coche 
##      0   3000   3000 
## 
## $ValorOptimo
## [1] 0
## 
## $AlternativaOptima
## Ahorro 
##      1
```


### CRITERIO DE LAPLACE



```
## $criterio
## [1] "Laplace"
## 
## $metodo
## [1] "favorable"
## 
## $tablaX
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
## 
## $ValorAlternativas
##    Ahorro     Viaje     Coche 
## 11333.333  9000.000  9333.333 
## 
## $ValorOptimo
## [1] 11333.33
## 
## $AlternativaOptima
## Ahorro 
##      1
```


### CRITERIO DEL PUNTO IDEAL 



```
## $criterio
## [1] "Punto Ideal"
## 
## $metodo
## [1] "favorable"
## 
## $tablaX
##        Mejora Estable Empeora
## Ahorro  15000   11000    8000
## Viaje   13000    9000    5000
## Coche   12000   10000    6000
## 
## $Mejores
##  Mejora Estable Empeora 
##   15000   11000    8000 
## 
## $ValorAlternativas
##   Ahorro    Viaje    Coche 
##    0.000 4123.106 3741.657 
## 
## $ValorOptimo
## [1] 0
## 
## $AlternativaOptima
## Ahorro 
##      1
```


# PROBLEMA 2


#### Queremos organizar un troneo de voleibol para la pretemporada en el pabellón de nuestra ciudad. Tenemos que decidir qué equipos nos interesa que vengan para ver la repercusión que puede tener en la ciudad. 


#### ALTERNATIVAS:

    
$$
\begin{array}{c}
A_1: \text{Organizar el torneo solo para los equipos locales.}\\
A_2: \text{Invitar al torneo a equipos nacionales amigos.}\\
A_3: \text{Hacer el torneo a puerta abierta, que cualquier equipo pueda participar.}
\end{array}
$$
  
    
#### La repercusión de estas invitaciones repercute en la asistencia y lo que se ganará durante esos días, distinguiendose 3 ESTADOS:


$$
\begin{array}{c}
E_1:\ \text{Alta asistendia de público .}\\
E_2:\ \text{Asistencia media pero notable.}\\
E_3:\ \text{Poca asistencia.}
\end{array}
$$


#### TABLA DE DECISIÓN 


$$

\begin{array}{lccc}
\textbf{Alternativa / Estado} & E_1: \text{A.alta} & E_2: \text{A.media} & E_3: \text{A.poca} \\[4pt]
A_1: \text{E.locales} & 15000 & 11000 & 8000 \\[4pt]
A_2: \text{E.nacionales} & 13000 & 9000 & 5000 \\[4pt]
A_3: \text{Puerta abierta} & 12000 & 10000 & 6000
\end{array}

$$


Vamos a resolver los distintos métodos de decisión bajo incertidumbre para ver cual es la mejor opción, esta vez utilizando una función donde se realizan todos los criterios a la vez.



``` r
tablaY = crea.tablaX(c(15,12,8,25,15,5,40,10,-5), numalternativas = 3, numestados = 3, nb_alternativas = c("Equipos locales","Equipos nacionales","Puerta abierta"), nb_estados = c("Alta asistencia", "Media asistencia","Poca asistencia"))

tablaY
```

```
##                    Alta asistencia Media asistencia Poca asistencia
## Equipos locales                 15               12               8
## Equipos nacionales              25               15               5
## Puerta abierta                  40               10              -5
```


#### TODOS LOS CRITERIOS JUNTOS EN UNA TABLA.



```
##                    Alta asistencia Media asistencia Poca asistencia
## Equipos locales                 15               12               8
## Equipos nacionales              25               15               5
## Puerta abierta                  40               10              -5
## iAlt.Opt (fav.)                 --               --              --
##                               Wald      Optimista        Hurwicz         Savage
## Equipos locales                  8             15           12.9             25
## Equipos nacionales               5             25           19.0             15
## Puerta abierta                  -5             40           26.5             13
## iAlt.Opt (fav.)    Equipos locales Puerta abierta Puerta abierta Puerta abierta
##                                              Laplace    Punto Ideal
## Equipos locales                                11.67          25.18
## Equipos nacionales                             15.00          15.30
## Puerta abierta                                 15.00          13.93
## iAlt.Opt (fav.)    Equipos nacionales,Puerta abierta Puerta abierta
##                      Veces Optima
## Equipos locales                 1
## Equipos nacionales              1
## Puerta abierta                  5
## iAlt.Opt (fav.)    Puerta abierta
```
