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

### Ley de la suma ej:

```

def f(n):
  for i in range(n):
   print (i)
 
```
