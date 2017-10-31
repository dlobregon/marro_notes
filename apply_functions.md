UNIVERSIDAD FRANCISCO MARROQUÍN - Facultad de Ciencias Económicas
Aplicaciones económicas de programación y bases de datos I – Sección A
Segundo Semestre 2017
## Funciones y el uso de Apply

**Funciones**

Una función es una porción de código diseñado y organizado para  obtener un resultado específico. Las partes fundamentales de una función son los “parámetros” (son los datos sobre los cuales operamos) y el “return” que nos devuelve el resultado de la operación. En R las funciones se declaran de la siguiente manera:

~~~~R
#función que divide  el primer número entre el cuadrado del segundo
custom_f<-function(a,b){
  resultado<-a/(b^2)
  return(resultado)
}
custom_f(20,2) #aplicando la función para
print(custom_f(20,2)) #imprimirá el valor 5 como resultado de aplicar la función
~~~~
La función anterior se puede aplicar incluso  columnas de un data frame o matriz, para ello enviamos como parámetros  las columnas que deseamos operar. El resultado de aplicar dicha función a las columnas es un vector con los resultados de aplicar la función entre las filas de las columnas enviadas como parámetros.

~~~~R
#dado un data frame con las columnas indicador y coeficiente
custom_f(df1$indicador,df1$coeficiente)
#asignado el resultado a una nueva fila del data frame
df1$nueva<-custom_f(df1$indicador,df1$coeficiente)
#la columna "nueva" tendrá los valores resultados de aplicar dichas funciones
~~~~
De lo anterior, nótese que se pueden enviar vectores siempre y cuando sean del mismo tamaño. Puede aplicarse desde un parámetro a más.



**Apply**

Para operar entre los valores de las columnas  y filas de un “data frame” o matriz podemos utilizar ciclos como el “for” o el “while”. R tiene entre una función que nos facilita aplicar funciones a los valores de las estructuras de datos llamada “apply”. La función “apply” devuelve un vector o matriz de valores obtenidos al aplicar una función a los márgenes de una matriz o “data frame” sin caer en la necesidad de usar ciclos.

La función “apply” está formada básicamente por los siguientes parámetros:
* X, que es la estructura de datos sobre la cual tenemos que aplicar la función.
* MARGIN, nos sirve para determinar si queremos aplicar la función a las filas (valor igual a 1) o las columnas (valor igual a 2). Si queremos que la función se aplique tanto a filas columnas definimos el valor como "c(1,2)".
* FUN, nos sirve para definir la función que deseamos aplicar sobre los datos.

Ejemplo:

~~~~R
# creamos una matriz de 10 filas x 2 columnas
m <- matrix(c(1:10, 11:20), nrow = 10, ncol = 2)
# usamos apply para obtener la media de las filas
apply(X= m, MARGIN=1,FUN= mean)
[1]  6  7  8  9 10 11 12 13 14 15
#  apply para obtener la media de las columnas
apply(X=m,MARGIN= 2,FUN= mean)
[1]  5.5 15.5
# divide una matríz de todos los valores dividos por 2
apply(X=m,MARGIN= 1:2,FUN= function(x) x/2)
# si existiese una función definida aparte que realice la misma operación 
apply(X=m, MARGIN=1:2, FUN=nombre_funcion)
~~~~
Si deseamos aplicar la función para una sola porción de la matriz o “data frame” se debe de definirlo de la siguiente manera:


~~~~R
#dado un dataframe "df" de tres columnas, y queremos aplicarlo a la columna número 2
#"nombre_función" es culaquier función definida con anterioridad
apply(X=df[,2],MARGIN=2,FUN = nombre_funcion )
#aplicando a una fila determinada
apply(X=df[3,],MARGIN=1,FUN = nombre_funcion ) #aplicando a la fila 3

# en algunos casos R toma las expresiones como objetos que no son vectores
# y nos devuelve errores como ""dim(X) must have a positive length"
# para ello debemos de utilizar el parámetro "drop=F"
apply(X=df[,2,drop=F],MARGIN=2,FUN = nombre_funcion )
#aplicando a una fila determinada
apply(X=df[3,,drop=F],MARGIN=1,FUN = nombre_funcion )
~~~~

