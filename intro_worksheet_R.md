UNIVERSIDAD FRANCISCO MARROQUÍN - Facultad de Ciencias Económicas
Aplicaciones económicas de programación y bases de datos I – Sección A
Segundo Semestre 2017

## Worksheet – R Basics

**Impresión en consola y asignación de variables**

Para imprimir el resultado de alguna operación o un determinado valor solo es necesario escribir la operación. Además de valores numéricos se pueden agregara secuencias de letras o caracteres. Para que R interprete como una cadena se debe de empezar y terminar con comillas dobles "". R también maneja datos de tipo lógico, estos datos o valores pueden explicito
Ejemplo:
~~~~R
#mostrar resultados en consola
3+6
8^3
3+(8/7)*5
#imprimir cadena de caracteres
"hola!"
~~~~
Las variables nos sirven para almacenar valores para utilizarlos en el futuro. A las variables se les puede asignar valores o resultados de operación (  y datos complejos como veremos más adelante).
Los nombres de las variables siempre empiezan con alguna letra (mayúscula o minúscula), luego les puede seguir una sucesión de caracteres, números o guiones bajos. Se hace distinción entre mayúscula y minúscula.

La asignación se hace de la siguiente manera “Nombre_variable <- valor_o_resultado”

~~~~R
#asignación de variables
var<-8^2 #8 al cuadrado
var <- (var*8)^2
Var<- var*(12*3/4)
Var #imprimir el valor de Var
var_z <- "valor de cadena"
a_log <- 10 < 8 # asigna un valor lógico 
~~~~

**Generación de secuencias**

En ocasiones necesitaremos manejar una sucesión de números desde un valor inicial hasta un valor final, para ello R cuenta con un mecanismo para poder generar la sucesión. La sintaxis es de la siguiente manera: “número_inicial:número_final”
~~~~R
#generación ascendente
1:10
3*3:10
#generación descendente
10:7
7*10:4
~~~~
Resolver lo siguiente:
1. Explique cual es el patrón de la siguiente secuencia

	~~~~R
	200:7*10
	~~~~

2. Tomando las variables generadas en el ejemplo, calcular el valor de "Var" al cuadrado divido por "var"
3. Investigar todos los operadores lógicos permitidos en R.


**Estructuras de datos**

Existen escenarios donde debemos almacenar conjuntos de datos, para ello en programación existe el concepto de “Estructura de datos” que busca que las personas puedan manejar muchos datos en una variable.
Las estructuras de datos más comunes son las siguientes:
* Vectores
* Listas
* Arreglos
* Matrices
* Data frames

**Vectores**

Los vectores son las estructuras de datos más simples y comunes en R. Tiene la característica de que puede  almacenar valores lógicos, numéricos y cadenas. Los vectores sólo pueden almacenar valores de un tipo, no almacena mezclas.  Para construir un vector se utiliza la función “c()” que le indica a R que se hará una combinación.
~~~~R
#imprimiendo un vector
c(1,2,3)
c("uno","dos","tres")
v1 <-c(1:10)#asignando una secuencia
x <- c(1,2,3)
y <- c(10,20,30,40,50,60)
z<- c(x,y) #combinando vectores
~~~~
Realizar lo siguiente:
4. Tomando los datos del ejemplo anterior explique que realiza la siguiente operación    " x+y ".
5. Que sucede cuando mezclamos tipos de valores en el siguiente ejemplo “c(1,2,"hola")” .
6. Para que sirve la función "mode()" en R.

**Matrices**

Una matriz es un conjunto de datos de dos dimensiones, en el caso de R necesitamos especificar a priori el número de columnas y el número de filas para poder utilizar cada uno de los campos. 
~~~~R
#creación de una matriz
X<- matrix(1:6,nrow=2,ncol=3);
#el primer parametro es un secuencia de números
#nrow nos sirve para indicar las filas, ncol nos sirve para indicar las columnas.
X <- matrix(c(1,2,3,4,5,6), nrow=2,ncol=3) #los datos de la matriz son de un vector
#Ordenar los valores de la matriz por fila
X<-matrix(1:6,nrow=2,ncol = 3,byrow = TRUE)
#repetir valores
X<-matrix(1,nrow=10,ncol=10)
~~~~

Realizar lo siguiente:
7. escriba el código de la siguiente forma "X <- matrix(v,nrow=2,ncol=4)" donde "v" sea el vector más pequeño posible para que "X" sea de la siguiente forma

~~~~R
     [,1] [,2] [,3] [,4]
[1,]    1    1    1    1
[2,]    2    2    2    2
~~~~
R también permite fusionar vectores para crear matrices, con la condicion de que los vectores sean del mismo tamaño.
~~~~R
#fusionando vectores, donde cada vector es una columna
X1 <- cbind(1:5,11:15)
#fusionando vectores, donde cada vector es una fila
X2 <- rbind(1:5,11:15)
~~~~

Realizar lo siguiente:
8. 	Crear una matriz de dos columnas, donde la primera columna son los números de 1 a 25, la segunda columna es el valor de la primera columna al cuadrado.

**Accediendo a valores de vectores y matrices**

Para acceder a un valor especifico que se encuentra dentro de un vector o matríz debemos de indicar las "coordenas" o "posición", esa tal posición se le llama "índice".
~~~~R
#accediendo al valor de un vector
y<-5:10
y[2] #debe devolver como valor el número 6.

#accediendo a un valor de una matríz
z<-cbind(1:15,37:51)
z[1,] #devuelve los valores de la primera fila
z[,1] #devuelve los valores de la primera columna
z[9,2] #devuelve el valor de la fila nueve y columna dos
~~~~

Realizar lo siguiente:
9. Encontrar la posición del número 48 en la matriz "z"
10. Investigar en que se diferencia una lista y un vector en R.
11. Investigar en que se diferencia una Matriz y un Array en R.

**Data frames**

Son estructuras de datos que permiten almacenar valores mixtos, son de dos dimensiones y además permiten el uso de cabeceras para las columnas.
~~~~R
#creando un dataframe
data <- data.frame(1:5,(1:5)^2,c("uno","dos","tres","cuatro","cinco"))
#creando un dataframe con cabeceras
data <- data.frame(numeros=1:5,cuadruados=(1:5)^2,cadenas=c("uno","dos","tres","cuatro","cinco"))
# accediendo a la posición que ubica el número 25
data[5,2]
#agregando una nueva columna al data frame
data$nueva <- 71:75
#definiendo un valor especifico en una posicion del dataframe
data[4,4]<-7

~~~~
Realizar lo siguiente:
12. porque usando el ejemplo anterior, no se puede aplicar lo siguiente: "data[4,3]<-6"


**Sentencia de control IF**

Ejecuta un trozo de código si la condición evaluada es verdadera, la instrucción "else" ejecuta el trozo de código interno si la condición es falsa. Evalúa valores lógicos que provienen de valores lógicos o comparaciones de valores númericos o comparaciones de cadenas.


~~~~R
# evaluando si 3 es menor a 4
if (3 < 4 ){
	print("verdadero")
}
#evaluando si 7 es menor a 4
if (7 < 4 ){
	print("verdadero")
}else{
	print("falso")
}
#evaluacion simplificada
print(
  ifelse(7 < 4,"verdadero","falso")
  )
~~~~
Resolver lo siguiente:

13. encontrar los signos de comparación para valores númericos y lógicos
14. investigar cómo se niega un valor lógico, es decir que pase de verdadero a falso y viceversa

**Ciclos**

Los ciclos son sentencias que ejecutan porciones de código un determinado número de veces. Los ciclos en R son los siguientes:
* for
* while
* repeat

**Ciclo "for"**

Repite la porción de código por un número establecidoCompletar el código siguiente, a manera de que se detenga exactamente cuando encuentre el número 40:
 de veces.
~~~~R
for(i in 1:15){
  print(c("estoy en la posicion: ",i))
}
veces <- 1:10
for(vez in veces){
  print(c("estoy en la posicion: ",vez))
}

#deteniendo ciclos
x <- 1:5
for (val in x) {
  if (val == 3){
    break
  }
  print(val)
}

#recorriendo matriz por columna a la vez
for(i in 1:3){
  for(j in 1:15){
    print(matriz[j,i])
  }
}
~~~~

Resolver lo siguiente:

15. hacer las instrucciones para recorrer la matriz por fila a la vez
16. Completar el código siguiente, a manera de que se detenga exactamente cuando encuentre el número 40.
~~~~R
#deteniendo el ciclo cuando encuentra el 40 en la matriz
for(i in 1:3){
 for(j in 1:15){
  print(matriz[j,i])
   if(matriz[j,i] == 40){
    break
   }
 }
}
~~~~