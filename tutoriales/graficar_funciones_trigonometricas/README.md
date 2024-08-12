# Graficar funciones trigonométricas en Python

Para graficar estas funciones se utilizarán las librerías numpy y matplotlib, en caso de no tenerlas instaladas se pueden instalar mediante la consola de Spyder o también desde el CMD si se tiene Python instalado

```bash
pip install numpy
```
```bash
pip install matplotlib
```

Una vez instaladas las librerías entonces podemos comenzar importandolas en el código de Python.

`numpy` se importa para cálculos numéricos y `matplotlib` para la visualización de las gráficas.

```python
import numpy as np
import matplotlib.pyplot as plt
```

El rango de valores para el eje x se obtiene usando np.linspace, se crea un array que comienza desde -2π hasta 2π y este array tiene 1000 valores.

Se calculan las funciones seno, coseno y tangente para cada valor del array x usando numpy.

```python
x = np.linspace(-2 * np.pi, 2 * np.pi, 1000)

y_sin = np.sin(x)
y_cos = np.cos(x)
y_tan = np.tan(x)
```

Teniendo ya un array con los valores del eje x y 3 arrays cada uno con los valores correspondientes al eje y para las funciones seno, coseno y tangente se puede ya realizar la gráfica. El siguiente código nos muestra la función seno.

```python
plt.plot(x, y_sin)
```

<img src="https://github.com/Ingenieria-Electrica-UdeA/banco_imagenes/blob/main/presentaciones/funcion_seno.png" style="max-width: 100%;" alt="Función seno">

Podemos agregar datos a la gráfica para que sea más ilustrativa y fácil de leer para otra persona, agregamos el título de la gráfica, nombre del eje x, nombre del eje y y una cuadrícula.

```python
plt.plot(x, y_sin)
plt.title('Función Seno')
plt.xlabel('Ángulo (radianes)')
plt.ylabel('seno (x)')
plt.grid(True)
```

<img src="https://github.com/Ingenieria-Electrica-UdeA/banco_imagenes/blob/main/presentaciones/funcion_seno_detalles.png" style="max-width: 100%;" alt="Función seno">

Cuando se trabaja con varias funciones en un solo gráfico es muy útil utilizar una leyenda, esto nos permite diferenciar cada una de las funciones.

```python
plt.plot(x, y_sin)
plt.plot(x, y_cos)
plt.title('Funciones seno y coseno')
plt.xlabel('Ángulo (radianes)')
plt.ylabel('seno (x),coseno(x)')
plt.legend(["seno (x)","coseno (x)"])
plt.grid(True)
```

Para hacer ambas funciones en gráficas separadas se utiliza plt.show()

```python
plt.plot(x, y_sin)
plt.title('Función seno')
plt.xlabel('Ángulo (radianes)')
plt.ylabel('seno (x)')
plt.grid(True)
plt.show()

plt.plot(x, y_cos)
plt.title('Función coseno')
plt.xlabel('Ángulo (radianes)')
plt.ylabel('coseno (x)')
plt.grid(True)
plt.show()
```


<img src="https://github.com/Ingenieria-Electrica-UdeA/banco_imagenes/blob/main/presentaciones/funciones_seno_coseno.png" style="max-width: 100%;" alt="Funciones seno y coseno">

En este caso se grafican la función seno y coseno ya que su rango y dominio son iguales, si las graficamos junto a la función tangente habría que hacer ajustes adicionales ya que la función tangente tiene asíntotas y en su eje y tiene valores más altos que seno y coseno, en la gráfica no se observan bien estas funciones y es porque su valor más alto en y es igual a 1.

```python
plt.plot(x, y_sin)
plt.plot(x, y_cos)
plt.plot(x, y_tan)
plt.title('Funciones seno, coseno y tangente')
plt.xlabel('Ángulo (radianes)')
plt.ylabel('seno (x),coseno(x)')
plt.legend(["seno (x)","coseno (x)","tangente (x)"])
plt.grid(True)
```

<img src="https://github.com/Ingenieria-Electrica-UdeA/banco_imagenes/blob/main/presentaciones/funciones_seno_coseno_tangente.png" style="max-width: 100%;" alt="Funciones seno, coseno y tangente">

## Código completo

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(-2 * np.pi, 2 * np.pi, 1000)
y_sin = np.sin(x)
y_cos = np.cos(x)
y_tan = np.tan(x)

plt.plot(x, y_sin)
plt.plot(x, y_cos)
plt.plot(x, y_tan)
plt.title('Funciones seno, coseno y tangente')
plt.xlabel('Ángulo (radianes)')
plt.ylabel('seno (x),coseno(x)')
plt.legend(["seno (x)","coseno (x)","tangente (x)"])
plt.grid(True)
```