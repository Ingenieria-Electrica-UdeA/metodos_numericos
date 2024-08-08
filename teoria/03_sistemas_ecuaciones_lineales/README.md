# Sistemas de Ecuaciones Lineales

Un sistema de ecuaciones lineales es un conjunto de dos o más ecuaciones lineales que comparten un conjunto de variables. El objetivo es encontrar los valores de las variables que satisfacen todas las ecuaciones simultáneamente.

## Sistema de Ecuaciones 2x2

Para un sistema de dos ecuaciones con dos incógnitas, se puede escribir de la forma general:

a1x + b1y = c1

a2x + b2y = c2

Donde `a1`, `b1`, `c1`, `a2`, `b2` y `c2` son constantes. La solución es un par `(x, y)` que satisface ambas ecuaciones.

## Métodos para Resolver Sistemas de Ecuaciones Lineales en Python

### 1. Método de Álgebra Lineal Usando `numpy`

El método de álgebra lineal utiliza la matriz de coeficientes y el vector de constantes para resolver un sistema de ecuaciones. En Python, la biblioteca `numpy` proporciona una manera sencilla de resolver sistemas lineales utilizando la función `numpy.linalg.solve()`.

Dado un sistema de ecuaciones lineales que se puede escribir en la forma matricial `A*x = b`, donde:

- `A` es la matriz de coeficientes.
- `x` es el vector de incógnitas.
- `b` es el vector de constantes.

La solución del sistema se encuentra utilizando: x = np.linalg.solve(A, b)

#### Ejemplo
Considere el siguiente sistema de ecuaciones:

2x + 3y = 13

4x - y = 5

```python
import numpy as np

A = np.array([[2, 3], [4, -1]])
b = np.array([13, 5])

x = np.linalg.solve(A, b)

print("La solución es:", x)
```

### 2. Método de Cramer

El método de Cramer utiliza determinantes para resolver sistemas de ecuaciones lineales. Es especialmente útil para sistemas de dos ecuaciones con dos incógnitas.

Para un sistema de ecuaciones A*x = b, el método de Cramer usa los determinantes para encontrar las soluciones de las incógnitas x e y:

- Se calcula el determinante de la matriz de coeficientes det(A).
- Se sustituyen las columnas de la matriz A por el vector de constantes b para obtener las matrices A_x y A_y.
- Se calculan los determinantes de A_x y A_y.
- Las soluciones se encuentran como:

x = det(A_x) / det(A)

y = det(A_y) / det(A)

#### Ejemplo
Considere el siguiente sistema de ecuaciones:

2x + 3y = 13

4x - y = 5

```python
import numpy as np

A = np.array([[2, 3], [4, -1]])
b = np.array([13, 5])

det_A = np.linalg.det(A)
A_x = A.copy()
A_x[:, 0] = b
det_A_x = np.linalg.det(A_x)
A_y = A.copy()
A_y[:, 1] = b
det_A_y = np.linalg.det(A_y)


x = det_A_x / det_A
y = det_A_y / det_A

print("La solución es: x =", x, ", y =", y)
```

### 3. Método de Eliminación de Gauss

El método de eliminación de Gauss transforma el sistema de ecuaciones en una forma escalonada o triangular para facilitar la resolución. En Python, se puede utilizar la factorización LU para realizar esta eliminación.

Para resolver el sistema de ecuaciones se pueden seguir tres pasos.

- Escribir la matriz aumentada del sistema de ecuaciones lineales: La matriz aumentada combina la matriz de coeficientes con el vector de constantes. Para un sistema de ecuaciones lineales, la matriz aumentada tiene la forma:


|| | | |  ||
|---------------|---------------|-----|---------------|---------------|---------------|
| a<sub>11</sub> | a<sub>12</sub> | ... | a<sub>1n</sub> ||  b<sub>1</sub> |
| a<sub>21</sub> | a<sub>22</sub> | ... | a<sub>2n</sub> ||  b<sub>2</sub> |
| ...           | ...           | ... | ...           | | ...           |
| a<sub>m1</sub> | a<sub>m2</sub> | ... | a<sub>mn</sub> | | b<sub>m</sub> |
|| | | |  |

- Usar operaciones para llevar la matriz aumentada a una forma escalonada. Se pueden usar las operaciones elementales:

  - Intercambiar filas: Para poner un coeficiente no nulo en la posición principal.
  - Multiplicar filas: Por una constante no cero para normalizar el coeficiente principal.
  - Sumar o restar múltiplos de una fila a otras filas para obtener ceros debajo del coeficiente principal.
- Mediante sustitución regresiva, resuelva el sistema equivalente correspondiente a la matriz aumentada escalonada. Se comienza desde la última ecuación y resuelve para la última variable. Luego sustituye esta variable en las ecuaciones anteriores para resolver las siguientes variables.

#### Ejemplo
Considere el siguiente sistema de ecuaciones:

2x + 3y = 13

4x - y = 5

##### Matriz aumentada

|  |  | | |
|---------------|---------------|---|---------------|
| 2 | 3 |  | 13 |
| 4 | -1 |  | 5 |
|  |  | | |

##### Transformación a Forma Escalonada
Se resta 2 veces la primera fila a la segunda fila para obtener un cero en la posición [2,1]

|  |  | | |
|---------------|---------------|---|---------------|
| 2 | 3 |  | 13 |
| 4-(2*2) | -1-(3*2) |  | 5-(2*13) |
|  |  | | |

|  |  | | |
|---------------|---------------|---|---------------|
| 2 | 3 |  | 13 |
| 0 | -7 |  | -21 |
|  |  | | |

##### Transformación a Forma Escalonada
Se resuelve -7y = -21, se obtiene y = 3.

Sustituir y = 3 en 2x + 3y = 13, obteniendo 2x + 9= 13, así x = 2.

La solución es x = 2 y y = 3.

```python
from scipy.linalg import lu
import numpy as np

A = np.array([[2, 3], [4, -1]])
b = np.array([13, 5])

P, L, U = lu(A)

y = np.linalg.solve(L, np.dot(P.T, b))

x = np.linalg.solve(U, y)

print("La solución es:", x)

```