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

Se calculan las funciones seno, coseno y tangente para cada valor del array x.

```python
x = np.linspace(-2 * np.pi, 2 * np.pi, 1000)

y_sin = np.sin(x)
y_cos = np.cos(x)
y_tan = np.tan(x)
```

