# POO-y-algoritmos-en-Python

Programación orientada a objetos (POO) y algoritmos en Python

Este repositorio se crea como resumen del curso POO y algoritmos en Python dictado por David Aroesti en Platzi

# Indice
- Programación orientada a objetos
 - Objetivos
 - POO en Python
 - Tipos de datos abstractos y clases e instancias
 - Decomposición
 - Abstracción
 - Encapsulación, getters and setters
 - Herencia
 - Polimorfismo
 - Int. a la complejidad algoritmica
 - Conteo abstracto de la operación
 - Notación asintótica
 - Clases de complejidad algorítmica
 - Búsqueda lineal





## Notación Asintótica
Esta notación lo que permite es evaluar la eficiencia del algritmo cuando sus valores tienden al infinito.
 - En este método se eliminan o no importan las variaciones pequeñas de la función
 - Con este método se evalua el comportamiento en el mejor de los casos de la ejecución del algoritmo, el caso promedio y el peor de los casos
 - para la simplicafición este método solo evalua el comportamiento del termino de mayor tamaño
 
 ### Big o
 Es un lenguaje o metrica que utilizamos para describir la eficiencia de los algoritmos.
 algunos ejemplos conocidos de la notaciones big o son:
  - O (log N)
  - O (N log N)
  - O (N)
  - O (N^2)
  - O (2N)

#### Ley de la suma ej(1):

```python

def f(n):
  for i in range(n):
   print (i)
   
  for i in range(n):
   print (i)
   
# O(n) + O(n) = O(n+n) = O(2n) = O(n)
```
Esto quiere decir que el algoritmo de suma crece en O de n o en funcion de n. En la última igualdad se remplaza 2n por n, debido a que en terminos de Big O solo no interesa el termino que mas crece.

#### Ley de la suma ej(2):
```python

def f(n):
 for i in range(n):
  print(i)
 
 For i in range(n * n):
  print(i)
# O(n) + O(n * n) = O(n + n^2) = O(n^2)

```
Como al Big O le interesa el termino más grande el Big O de este ejemplo es n^2

#### Ley de la multiplicación
```python

def f(n):
 for i in range(n):
  for j in range(n):
   print(i,j)
   
# O(n) * O(n) = O(n*n) = O(n^2)

```

#### Recursividad múltiple
```python

def fibonacci(n):
 if n == 0 or n == 1:
  return 1
 return fibonacci(n -1) + fibonacci(n-2)
 
# O(2^n)

```

## Clases de complejidad algorítmica
 - O(1) , constante
 - O(n) , Lineal - crece de manera prporcional
 - O(log n) , logarítmica - la funcion crece al principio mucho y lkuego se estabiliza
 - O(n log n) , Log lineal - se crece de manera logarítmica más una constante
 - O(n^2), Polinomial - 
 - O(2^n), exponencial
 
En cuanto al tipo de algorítmos que son usables para la solución de problemas, se excluye el uso de los algoritmos que tiene  un crecimiento polinomial, exponencial y factoriales debido al tiempo y la cantidad de recursos que usarian para resolver los problemas y en algunos casos estas soluciones para base de datos tan amplias como las de Google tomaria demasiados años para utilizarlos debido a la cantidad de pasos que debe hacer el algoritmo.

## Búsqueda lineal (algorítmos de búsqueda y ordenación)
Este modulo busca que se apliquen los conceptos de complejidad algorítmica y que conozcan algunos algorítmos para poder resolver problemas

> una habilidad de los computer science es reducir los problemas a problemas más pequeños y para los cuales ya existe una solución.

### Búsqueda lineal
Este es un algorítmo sencillo el cual busca si un elemento se encuentra en una lista o array y determina si este se encuentra o no.

```python

import random

def busqueda_lineal(lista, objetivo):
    match = False

    for elemento in lista:
        if elemento == objetivo:
            match = True
            break

    return match


if __name__ == '__main__':
    tamaño_de_lista = int(input('De que tamaño sera la lista? '))
    objetivo = int(input('Que numero quieres encontrar? '))

    lista = [random.randint(0, 100) for i in range(tamaño_de_lista)]

    encontrado = busqueda_lineal(lista,objetivo)
    print(lista)
    print(f'El elemento {objetivo} {"esta" if encontrado else "no esta"} en la lista')

```
¿Cúal es la complejidad algorítmica del programa anterior?

En cuanto a la complejidad algorítmica del programa anterior, este es de tipo linea lcomo su nombre lo indica, ya que solo genera un for loop para el elemento en la lista y el tamaño depende de la longitud que el usuario le de a la lista, Es decir:
 
 Complejidad: O(n)


### Búsqueda Binaria

Es el ejercicio que se usará a continuación sera una busqueda recursiva es decir que con cada iteración el tamaño de la lista se reduce a la mitad como se nota con el primer print statement al ejecutar el codigo.

Para tener en cuenta: "este algorítmo asume que los datos estan ordenados" 

> se aplica el principio de divide y conquista, el problema se divide en 2 en cada iteración

```python

import random

def busqueda_binaria(lista, comienzo, final, objetivo):
    print(f'buscando {objetivo} entre {lista[comienzo]} y {lista[final-1]}')
    if comienzo > final:
        return False
    
    medio = (comienzo + final) // 2

    if lista[medio] == objetivo:
        return True
    elif lista[medio] < objetivo:
        return busqueda_binaria(lista, medio + 1, final, objetivo)
    else:
        return busqueda_binaria(lista,comienzo, medio - 1, objetivo)


if __name__ == '__main__':
    tamaño_de_lista = int(input('De que tamaño es la lista? '))
    objetivo = int(input('Que numero quieres encontrar? '))

    lista = sorted([random.randint(0,100) for i in range(tamaño_de_lista)])

    encontrado = busqueda_binaria(lista, 0, len(lista), objetivo)

    print(lista)
    print(f'El elemento {objetivo} {"esta" if encontrado else "no esta"} en la lista')

```

Resultado de una ejecución:

```python

PS C:\Users\Usuario\Desktop\Programacion\Python\POO y algoritmos con Python> python Busqueda_binaria.py
De que tamaño es la lista? 50
Que numero quieres encontrar? 60
buscando 60 entre 3 y 100
buscando 60 entre 60 y 100
buscando 60 entre 60 y 84
buscando 60 entre 60 y 62
buscando 60 entre 60 y 60
[3, 4, 4, 5, 8, 9, 15, 19, 21, 21, 21, 22, 23, 27, 33, 35, 38, 40, 42, 45, 48, 50, 53, 54, 57, 58, 60, 60, 62, 62, 62, 64, 65, 65, 78, 81, 84, 85, 87, 88, 88, 90, 91, 92, 92, 94, 95, 97, 98, 100]
El elemento 60 esta en la lista

```

## Ordenamiento de burbuja (bubble sort)
> "Es un algorítmo que recorre repetidamente una lista que necesita ordenarse. compara los elementos adyacentes y los intercambia si estan en el orden incorrecto. Este procedimiento se repite hasta que no se requieran más intercambios, lo que indica que la lista esta ordenada."

Este algoritmo mediante codigo se vería de la siguiente forma:

```python

import random

def ordenamiento_de_burbuja(lista):
    n = len(lista)

    for i in range(n):
        for j in range(0, n - i - 1):

            if lista[j] > lista[j + 1]:
                lista[j], lista[j + 1] = lista[j + 1], lista[j]
    return lista

if __name__ == '__main__':
    tamaño_de_lista = int(input('De que tamaño será la lista? '))

    lista = [random.randint(0,100) for i in range(tamaño_de_lista)]
    print(lista)

    Lista_ordenada = ordenamiento_de_burbuja(lista)
    print(Lista_ordenada)

```

Y la complejidad algorítmica de este código sería:
> Polinominial es decir Big O ( n ^ 2), debido a que se realiza un for loop para j que esta dento de un un for loop para i.

La ejecución de código queda como sigue:

```python
PS C:\Users\Usuario\Desktop\Programacion\Python\POO y algoritmos con Python> python ordenamiento_burbuja.py
De que tamaño será la lista? 10
[59, 30, 69, 43, 49, 27, 29, 7, 52, 48]
[7, 27, 29, 30, 43, 48, 49, 52, 59, 69]
```

## Ordenamiento por inserción
> "Es un algoritmo de facil implementación pero muy ineficiente para listas de gran tamaño"
> " la ejecución es la siguiente: 

    Una lista es dividida entre una sublista ordenada y otra sublista desordenada.
    Al principio, la sublista ordenada contiene un solo elemento, por lo que por
    definición se encuentra ordenada.

    A continuación se evalua el primer elemento dentro la sublista desordenada para
    que podamos insertarlo en el lugar correcto dentro de la lista ordenada.

    La inserción se realiza al mover todos los elementos mayores al elemento que
    se está evauluando un lugar a la derecha.

    Continua el proceso hasta que la sublista desordenada quede vacia y, por lo
    tanto, la lista se encontrará ordenada.

La implementación del código queda como sigue:

```python
import random

def ord_insercion(lista):

    for indice in range(1, len(lista)):
        valor_actual = lista[indice]
        posicion_actual = indice

        while posicion_actual > 0 and lista[posicion_actual - 1] > valor_actual:
            lista[posicion_actual] = lista[posicion_actual - 1]
            posicion_actual -= 1
        
        lista[posicion_actual] = valor_actual
        print(lista) # revisar los cambios

    return lista

if __name__ == "__main__":
    tamaño_de_lista = int(input('De que tamaño será la lista? '))

    lista = [random.randint(0, 100) for i in range(tamaño_de_lista)]

    lista_ordenada = ord_insercion(lista)
    print(lista_ordenada)
```

## Ordenamiento por mezcla (merge sort)

El ordenamiento por mezcla es un algoritmo de divide y conquistaras. primero divide una lista en partes iguales o hasta que quedan sublistas de 1 o 0 elementos. luego las recombina en forma ordenada.

La aplicación del código queda como sigue:

``` python
import random

def ord_insercion(lista):

    for indice in range(1, len(lista)):
        valor_actual = lista[indice]
        posicion_actual = indice

        while posicion_actual > 0 and lista[posicion_actual - 1] > valor_actual:
            lista[posicion_actual] = lista[posicion_actual - 1]
            posicion_actual -= 1
        
        lista[posicion_actual] = valor_actual
        print(lista) # revisar los cambios

    return lista

if __name__ == "__main__":
    tamaño_de_lista = int(input('De que tamaño será la lista? '))

    lista = [random.randint(0, 100) for i in range(tamaño_de_lista)]

    lista_ordenada = ord_insercion(lista)
    print(lista_ordenada)
 
 ```
 













