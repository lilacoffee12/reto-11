# reto-11
# punto 1 
## suma y resta de matrices 
```
#Suma de matrices

import random                                                  # Importar paquete para generar números aleatorios y rellenar la matriz

def generar_matriz(filas_1, filas_2, columnas_1, columnas_2):  #Define la función para crear la matriz teniendo en cuenta filas y columnas
    matriz_1 = []                                              #Genera matriz vacía
    matriz_2 = []

    for i in range(filas_1):                                   #Recorre las filas de la primera matriz
        fila_1 = []              
        for n in range(columnas_1):                            #Recorre las columnas de la primera matriz
            fila_1.append(random.randint(1, 100))              #Agrega números aleatorios a la lista "fila_1" donde irán columnas y filas
        matriz_1.append(fila_1)                                #Agrega la anterior lista a la lista de la matriz


    for o in range(filas_2):                                   #Recorre las filas de la segunda matriz
        fila_2 = []                                   
        for p in range(columnas_2):                            #Recorre las columnas de la segunda matriz
            fila_2.append(random.randint(1, 100))              #Agrega números aleatorios a la lista "fila_2"
        matriz_2.append(fila_2)                                #Agrega la anterior lista a la lista de la matriz

    return matriz_1, matriz_2                                  #Retorna ambas listas


if __name__ == "__main__":
    filas_1 = int(input("Ingrese el número de filas para la matriz 1: "))         
    columnas_1 = int(input("Ingrese el número de columnas para la matriz 1: "))
    filas_2 = int(input("Ingrese el número de filas para la matriz 2: "))
    columnas_2 = int(input("Ingrese el número de columnas para la matriz 2: "))
    matriz_1, matriz_2 = generar_matriz(filas_1, filas_2, columnas_1, columnas_2)  #Genera dos matrices teniendo en cuenta número de filas y columnas ingresadas


    print()

    print("La matriz 1 es: ")
    for fila_1 in matriz_1:                                   #Genera los datos en forma de matriz
      print(fila_1)                                           #Imprime la matriz 1

    print()

    print("La matriz 2 es: ")
    for fila_2 in matriz_2:                                   #Genera los datos en forma de matriz
      print(fila_2)                                           #Imprime matriz 2


def suma_matrices(matriz_1, matriz_2):                                           #Define la función para sumar dos matrices
  if len(matriz_1) == len(matriz_2) and len(matriz_1[0]) == len(matriz_2[0]):    #Se tiene en cuenta que las filas y columnas de ambas matrices deben ser equivalentes
    matriz_3 = []
    for h in range(len(matriz_1)):                                               #Recorre las filas
      fila_3 = []
      for s in range(len(matriz_1[0])):                                          #Recorre las columnas
        fila_3.append(matriz_1[h][s] + matriz_2[h][s])                           #Suma los elementos correspondientes de las dos matrices y los agrega a la fila_3
      matriz_3.append(fila_3)                                                    #Agrega la fila 3 a la matriz 3 
  else:
    print()
    print("No es posible sumar las matrices, deben ser del mismo tamaño")        #Si no se cumple con la condición devuelve un mensaje

  return matriz_3                                                                #Retorna la matriz 3

if __name__ == "__main__":
   matriz_3 = suma_matrices(matriz_1, matriz_2)  

   print()
   print("La suma de las matrices es: ")
```
# punto 2
## Programa que realice el producto de matrices 
```
#funcion para validar que ambas matrices tienen el mismo tamañaño
def validar(m1, m2):
  num_columnas_m1 = len(m1[0])
  num_filas_m2 = len(m2)

  return num_columnas_m1 == num_filas_m2

 
#función para multiplicar matrices
def producto(m1, m2):
  if validar(m1, m2):
    resultado = []

    for i in range(len(m1)):
      fila = []
      #recorremos las columnas de la segunda matriz.
      for j in range(len(m2[0])):
        punto = 0
        #ahora las columnas 
        for k in range(len(m2)):
          #operamos y añadimos a la fila el resultado para luego añadirlo a la respuesta
          punto += m1[i][k] * m2[k][j]
        fila.append(punto)
      resultado.append(fila)
    return resultado
  else:
    return None
    
#EJEMPLO    
m1 = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
m2 = [[9, 8, 7], [6, 5, 4], [3, 2, 1]]

resultado_producto = producto(m1, m2)
```
# punto 3 
## obtener matriz transpuesta de matriz ingresada 
```
#función para imprimir una matriz
def matriz(matriz):
  for fila in matriz:
    for elemento in fila:
      print(elemento, end="\t")
        #genera el salto entre filas   
    print()  

#funcion para obtener la matriza transpuesta
def transpuesta(matriz):
  #verifica si la matriz esta vacia
  if not matriz:
    return []
  #obtener el numero de filas y columnas
  filas = len(matriz)
  columnas = len(matriz[0])
  #inicia una matriz vacia para ivertir las dimenciones
  transpuesta = [[0] * filas for _ in range(columnas)]
  #transpone a la matriz ingresada
  for i in range(filas):
    for j in range(columnas):
            #intercambia las posisciones
            transpuesta[j][i] = matriz[i][j]

  return transpuesta
#pide la cantidad de filas, nosotros definimos las columnas
filas = int(input("Ingrese el número de filas de la matriz: "))

#una matriz vacía
m = []


print("Ingrese los elementos de la matriz fila por fila: ")
for i in range(filas):
  fila = input(f"Ingrese los elementos de la fila {i + 1} separados por espacios: ").split()
  fila = [int(elemento) for elemento in fila]
  m.append(fila)
#imprime la matriz transpuesta
resultante = transpuesta(m)
for fila in resultante:
  print(fila)
```
# punto 4 
## Programa que sume los elemntos de una columna dada de una matriz 
```
import random

def generar_matriz(filas, columnas):  
    matriz = []

    for i in range(filas):
        fila = []
        for n in range(columnas):
            fila.append(random.randint(1, 100))
        matriz.append(fila)

    return matriz


if __name__ == "__main__":
    filas = int(input("Ingrese el número de filas para la matriz : "))
    columnas = int(input("Ingrese el número de columnas para la matriz : "))
    matriz = generar_matriz(filas, columnas)


    print()

    print("La matriz es: ")                  
    for fila in matriz:
      print(fila)
    print()


def suma_columna(matriz, num_columna):
  suma = 0
  for fila in matriz:
    suma += fila[num_columna]
  return suma


if __name__ == "__main__":
   num_columna = int(input("Ingrese el número de la columna que desea sumar, recordando que la primera columna es cero: "))
   suma_columna = suma_columna(matriz, num_columna)

   print()
   print("La suma de los elementos de la columna " + str(num_columna) + " es: ")
   print(suma_columna)

if resultado_producto:
    print("producto de matrices:")
    for fila in resultado_producto:
        print(fila)



   for fila_3 in matriz_3:                                                       #Genera los datos en forma de matriz
    print(fila_3)                                                                #Imprime la matriz 3
