# RETO-11
Este repo desarrolla cada uno de los ejercicios propuestos en la clase en la cual se explicó el tema de *matrices*

**1. Desarrolle un programa que permita realizar la suma/resta de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.**

```python
def crear_matriz(filas, columnas):
    # Crea una matriz solicitando los valores al usuario
    return [[int(input(f"Elemento [{i+1}, {j+1}]: ")) for j in range(columnas)] for i in range(filas)]

def imprimir_matriz(matriz):
    # Imprime la matriz fila por fila
    for fila in matriz:
        print(fila)

def validar_dimensiones(matriz1, matriz2):
    # Verifica si las dimensiones de las matrices son iguales
    return len(matriz1) == len(matriz2) and len(matriz1[0]) == len(matriz2[0])

def sumar_matrices(matriz1, matriz2):
    # Suma dos matrices de igual tamaño
    return [[matriz1[i][j] + matriz2[i][j] for j in range(len(matriz1[0]))] for i in range(len(matriz1))]

def restar_matrices(matriz1, matriz2):
    # Resta dos matrices de igual tamaño
    return [[matriz1[i][j] - matriz2[i][j] for j in range(len(matriz1[0]))] for i in range(len(matriz1))]

def main():
    # Solicitar el tamaño de ambas matrices
    filas1 = int(input("Filas de la primera matriz: "))
    columnas1 = int(input("Columnas de la primera matriz: "))
    matriz1 = crear_matriz(filas1, columnas1)

    filas2 = int(input("Filas de la segunda matriz: "))
    columnas2 = int(input("Columnas de la segunda matriz: "))
    matriz2 = crear_matriz(filas2, columnas2)

    # Verificar si se puede realizar la operación
    if validar_dimensiones(matriz1, matriz2):
        operacion = input("¿Suma o resta? ").lower()
        
        if operacion == "suma":
            resultado = sumar_matrices(matriz1, matriz2)
        elif operacion == "resta":
            resultado = restar_matrices(matriz1, matriz2)
        else:
            print("Operación no válida")
            return

        imprimir_matriz(resultado)
    else:
        print("Error: Las matrices no tienen las mismas dimensiones.")

if __name__ == "__main__":
    main()

```

**2. Desarrolle un programa que permita realizar el producto de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.**
   
```python
def crear_matriz(filas, columnas):
    # Crea una matriz solicitando los valores al usuario
    return [[int(input(f"Elemento [{i+1}, {j+1}]: ")) for j in range(columnas)] for i in range(filas)]

def imprimir_matriz(matriz):
    # Imprime la matriz fila por fila
    for fila in matriz:
        print(fila)

def producto_matrices(matriz1, matriz2):
    # Calcula el producto de dos matrices
    return [[sum(matriz1[i][k] * matriz2[k][j] for k in range(len(matriz2))) for j in range(len(matriz2[0]))] for i in range(len(matriz1))]

def main():
    # Solicitar el tamaño de la primera matriz
    filas1 = int(input("Filas de la primera matriz: "))
    columnas1 = int(input("Columnas de la primera matriz: "))
    matriz1 = crear_matriz(filas1, columnas1)

    # Solicitar el tamaño de la segunda matriz
    filas2 = int(input("Filas de la segunda matriz: "))
    columnas2 = int(input("Columnas de la segunda matriz: "))
    
    # Verificar si se pueden multiplicar (columnas de matriz1 == filas de matriz2)
    if columnas1 != filas2:
        print("Error: No se puede multiplicar. Las columnas de la primera matriz deben ser iguales a las filas de la segunda.")
        return
    
    matriz2 = crear_matriz(filas2, columnas2)

    # Calcular e imprimir el producto de las matrices
    resultado = producto_matrices(matriz1, matriz2)
    imprimir_matriz(resultado)

if __name__ == "__main__":
    main()
```
**3. Desarrolle un programa que permita obtener la matriz transpuesta de una matriz ingresada. El programa debe validar las condiciones necesarias para ejecutar la operación.**
   
```python
def crear_matriz(filas, columnas):
    # Crea una matriz solicitando los valores al usuario
    return [[int(input(f"Elemento [{i+1}, {j+1}]: ")) for j in range(columnas)] for i in range(filas)]

def imprimir_matriz(matriz):
    # Imprime la matriz fila por fila
    for fila in matriz:
        print(fila)

def transponer_matriz(matriz):
    # Calcula la transpuesta de la matriz
    return [[matriz[j][i] for j in range(len(matriz))] for i in range(len(matriz[0]))]

def main():
    # Solicitar el tamaño de la matriz
    filas = int(input("Ingrese el número de filas de la matriz: "))
    columnas = int(input("Ingrese el número de columnas de la matriz: "))
    
    # Crear la matriz
    matriz = crear_matriz(filas, columnas)
    
    # Imprimir la matriz original
    print("\nMatriz ingresada:")
    imprimir_matriz(matriz)
    
    # Calcular la transpuesta e imprimirla
    transpuesta = transponer_matriz(matriz)
    print("\nMatriz transpuesta:")
    imprimir_matriz(transpuesta)

if __name__ == "__main__":
    main()
```
**4. Desarrollar un programa que sume los elementos de una columna dada de una matriz.**

```python
def crear_matriz(filas, columnas):
    # Crea una matriz solicitando los valores al usuario
    return [[int(input(f"Elemento [{i+1}, {j+1}]: ")) for j in range(columnas)] for i in range(filas)]

def imprimir_matriz(matriz):
    # Imprime la matriz fila por fila
    for fila in matriz:
        print(fila)

def sumar_columna(matriz, columna):
    # Suma los elementos de una columna específica
    return sum(fila[columna] for fila in matriz)

def main():
    # Solicitar el tamaño de la matriz
    filas = int(input("Ingrese el número de filas de la matriz: "))
    columnas = int(input("Ingrese el número de columnas de la matriz: "))
    
    # Crear la matriz
    matriz = crear_matriz(filas, columnas)
    
    # Imprimir la matriz
    print("\nMatriz ingresada:")
    imprimir_matriz(matriz)
    
    # Solicitar la columna que se quiere sumar
    columna = int(input(f"Ingrese el número de la columna a sumar (0 a {columnas-1}): "))
    
    # Verificar si la columna ingresada es válida
    if 0 <= columna < columnas:
        # Sumar e imprimir el resultado de la columna
        suma = sumar_columna(matriz, columna)
        print(f"\nLa suma de los elementos de la columna {columna} es: {suma}")
    else:
        print("Error: Columna fuera de rango.")

if __name__ == "__main__":
    main()
```
**5. Desarrollar un programa que sume los elementos de una fila dada de una matriz**
   
```python
def crear_matriz(filas, columnas):
    # Crea una matriz solicitando los valores al usuario
    return [[int(input(f"Elemento [{i+1}, {j+1}]: ")) for j in range(columnas)] for i in range(filas)]

def imprimir_matriz(matriz):
    # Imprime la matriz fila por fila
    for fila in matriz:
        print(fila)

def sumar_fila(matriz, fila):
    # Suma los elementos de una fila específica
    return sum(matriz[fila])

def main():
    # Solicitar el tamaño de la matriz
    filas = int(input("Ingrese el número de filas de la matriz: "))
    columnas = int(input("Ingrese el número de columnas de la matriz: "))
    
    # Crear la matriz
    matriz = crear_matriz(filas, columnas)
    
    # Imprimir la matriz
    print("\nMatriz ingresada:")
    imprimir_matriz(matriz)
    
    # Solicitar la fila que se quiere sumar
    fila = int(input(f"Ingrese el número de la fila a sumar (0 a {filas-1}): "))
    
    # Verificar si la fila ingresada es válida
    if 0 <= fila < filas:
        # Sumar e imprimir el resultado de la fila
        suma = sumar_fila(matriz, fila)
        print(f"\nLa suma de los elementos de la fila {fila} es: {suma}")
    else:
        print("Error: Fila fuera de rango.")

if __name__ == "__main__":
    main()

```
