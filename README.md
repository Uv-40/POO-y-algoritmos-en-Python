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
Busca en todos los elementos de manera secuencial o de la manera en que esta ordenado

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


