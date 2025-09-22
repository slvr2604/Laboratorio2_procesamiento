# Laboratorio2_procesamiento
Lina María Cortés Almonacid  
María Alejandra Torres Cardenas  
Silvia Lorena Vargas Rueda  

## Convolución, correlación y transformada de Fourier  
En este laboratorio se tuvieron en cuenta tres operaciones matemáticas: la convolución, la correlación y las transformadas. La convolución permite determinar cómo un sistema responde a una señal de entrada. La correlación, por su parte, mide la similitud entre dos señales a lo largo del tiempo, siendo una herramienta valiosa en el procesamiento de señales, la detección de patrones y la reducción de ruido. Las transformadas por su parte, como la de Fourier, facilitan el análisis de señales en el dominio de la frecuencia. Estas herramientas permiten descomponer señales en sus componentes fundamentales, optimizando la compresión de datos.  

### Parte A:  
Se tomaron los datos de tres estudiantes, donde se estableció un sistema y una señal de entrada basados en sus datos personales. Para cada estudiante se definió el sistema h[n] como una secuencia discreta formada por los dígitos de su código de estudiante. Se definió la señal de entrada x[n] como la secuencia compuesta por los dígitos de su número de identidad. A partir de estas secuencias, se obtuvo la señal de salida y[n] mediante la operación de convolución discreta.  

**Lina Cortés**  

Teniendo el sistema h[n] = {5,6,0,8,3,4} y la señal x[n] = {1,0,7,6,7,3,6,2,2,9}:  
1. Encuentre la señal 𝑦[𝑛] resultante de la convolución usando sumatorias (a mano). 
<img width="1392" height="646" alt="image" src="https://github.com/user-attachments/assets/341fe452-4ea3-4a34-a475-8bda0c3212fb" />

2. Encuentre la representación gráfica y secuencial (a mano).
<img width="1442" height="1229" alt="image" src="https://github.com/user-attachments/assets/89073635-2828-4488-b3ed-03adf264a7d6" />

3. Encuentre la señal 𝑦[𝑛] resultante de la convolución usando Python.
 
         x = np.array([1,0,7,6,7,3,6,2,2,9])
         h = np.array([5,6,0,0,8,3,4])
         y = np.convolve(x, h)
         print("La señal resultante y[n] es:", y)
   
**La señal resultante y[n]** es: [  5   6  35  72  79  60 108 115 124 126 139  46  46  86  35  36]  


4. Encuentre la representación gráfica y secuencial usando Python.

         x = np.array([1,0,7,6,7,3,6,2,2,9])
         h = np.array([5,6,0,0,8,3,4])

         fig, axs = plt.subplots(3, 1, figsize=(10, 8), sharex=False)  

         Gráfica de x(n)
         plt.subplot(3, 1, 1)
         plt.stem(x_n, x)
         plt.title("x (n) = Lina Cortés")
         plt.ylabel("x [n]")
         plt.grid(True)

         Gráfica de h(n) 
         plt.subplot(3, 1, 2)
         plt.stem(h_n, h)
         plt.title("h (n) =  Lina Cortés")
         plt.ylabel("h [n]")
         plt.grid(True)

         Gráfica de y(n)
         plt.subplot(3, 1, 3)
         plt.stem(y_n, y)
         plt.title("y(n) = Lina Cortés")
         plt.xlabel("n")
         plt.ylabel("y [n]")
         plt.grid(True)

         plt.tight_layout()
         plt.show()


   <img width="989" height="790" alt="image" src="https://github.com/user-attachments/assets/c4d69630-c63e-42f2-80f1-e7f6a5071003" />

Se confirma que el procedimiento que fue a mano, junto con el programado es correcto y concuerda.  
   


**Silvia Vargas**  

Primero hacemos el cálculo de la convolución a mano de la señal `y(n) = x(n) + h(n)` a través del método enseñado, teniendo en cuenta que `x(n) = {1,0,5,4,2,8,4,0,8,8}` y que `h(n) = {5,6,0,0,8,5,6}`, la cual quedaría de la siguiente forma:
<img width="1280" height="748" alt="image" src="https://github.com/user-attachments/assets/2293c06b-8583-4c6d-99a1-9f0557905734" />

Y al ser graficada, nos dará una gráfica de la siguiente forma:
<img width="816" height="1019" alt="image" src="https://github.com/user-attachments/assets/506d05a0-1000-410b-a6ef-968d3ce829bb" />

Y una vez hecho el proceso a mano, procederemos a verificarlo a través del código de Python:

```
#Definimos x(n) y h(n).
x = np.array([1,0,5,4,2,8,4,0,8,8])
h = np.array([5,6,0,0,8,5,6])

y = np.convolve(x,h)
print("y(n) = ", y)
```
**Y nos dará que `y (n) = {5, 6, 25, 50, 42, 57, 114, 81, 106, 186, 132, 68, 88, 104, 88, 48}`, la cual coincide con la señal convolucionada calculada anteriormente.**
Y procederemos con el rango de índices para las gráficas.
```
#Generamos el rango de índices.
x_n = np.arange(len(x))
h_n = np.arange(len(h))
y_n = np.arange(len(y))
```
Y una vez hecho, podremos generar las tres gráficas, de `x(n)`, `h,(n)` y de `y(n)`.
```
fig, axs = plt.subplots(3, 1, figsize=(10, 8), sharex=False)

# Gráfica de x(n)
plt.subplot(3, 1, 1)
plt.stem(x_n, x)
plt.title("x(n) = Código Silvia")
plt.ylabel("x[n]")
plt.grid(True)

# Gráfica de h(n)
plt.subplot(3, 1, 2)
plt.stem(h_n, h)
plt.title("h(n) = Código Silvia")
plt.ylabel("h[n]")
plt.grid(True)

# Gráfica de y(n)
plt.subplot(3, 1, 3)
plt.stem(y_n, y)
plt.title("y(n) = Código Silvia")
plt.xlabel("n")
plt.ylabel("y[n]")
plt.grid(True)

plt.tight_layout()
plt.show()
```
Donde `fig, axs = plt.subplots(3, 1, figsize=(10, 8), sharex=False)` será de utilidad para dar un tamaño general a las tres gráficas para que al graficarlas se observen así: 
<img width="989" height="790" alt="image" src="https://github.com/user-attachments/assets/955752fb-a2b0-46bc-9af9-661ccd58e516" />
y `plt.subplot(3, 1, 1)` es la forma clásica de dividir una sola figura en una cuadrícula de subgráficas, donde el primer 3 respresenta el número de filas, el primer 1 será el número de columnas, y el segundo 1 será el índice de la gráfica que será usada.
 Y finalmente observaremos la relación correcta entre la convolución realizada a mano con el método enseñado y la convolución realizada a través de Python.
 
**Alejandra Torres**

Teniendo el sistema h[n] = {5,6,0,7,4,8} y la señal x[n] = {1,0,1,1,3,2,1,5,9,7}:  

1. Encuentre la señal 𝑦[𝑛] resultante de la convolución usando sumatorias (a mano).
   
<img width="1488" height="1238" alt="image" src="https://github.com/user-attachments/assets/91ae1dff-e385-4e28-ba72-c7ce268aebe7" />

3. Encuentre la representación gráfica y secuencial (a mano).
   
<img width="1159" height="775" alt="image" src="https://github.com/user-attachments/assets/25e2b891-aa53-4556-af6d-a24d76f320ac" />

5. Encuentre la señal 𝑦[𝑛] resultante de la convolución usando Python.
   
       h = [5,6,0,0,7,4,8]
       x = [1,0,1,1,3,2,1,5,9,7]
       y = np.convolve(x, h)
       print("y[n] =", y)

**La señal resultante y[n]** es: [  5 6 5 11 28 32 32 42 108 123 86 55 91 125 100 56 ]  

4. Encuentre la representación gráfica y secuencial usando Python.

       import numpy as np
       import matplotlib.pyplot as plt

       h = [5, 6, 0, 0, 7, 4, 8]
       x = [1, 0, 1, 1, 3, 2, 1, 5, 9, 7]

       x_n = np.arange(len(x))
       h_n = np.arange(len(h))

       y = np.convolve(x, h)
       y_n = np.arange(len(y))

       fig, axs = plt.subplots(3, 1, figsize=(10, 8), sharex=False)

       # Grafica x(n)
       axs[0].stem(x_n, x)
       axs[0].set_title("x(n) = Alejandra Torres")
       axs[0].set_ylabel("x[n]")
       axs[0].grid(True)

       # Grafica h(n)
       axs[1].stem(h_n, h)
       axs[1].set_title("h(n) = Alejandra Torres")
       axs[1].set_ylabel("h[n]")
       axs[1].grid(True)

       # Grafica y(n)
       axs[2].stem(y_n, y)
       axs[2].set_title("y(n) = Alejandra Torres")
       axs[2].set_xlabel("n")
       axs[2].set_ylabel("y[n]")
       axs[2].grid(True)

       plt.tight_layout()
       plt.show()

       print("La señal resultante y[n] es:", y)

<img width="989" height="790" alt="image" src="https://github.com/user-attachments/assets/8dde492d-a75b-4531-a2af-6367a66e4ff2" />

Los resultados fueron exactamente iguales en ambos casos, tanto en los valores de y[n] como en la gráfica obtenida, confirmando que el procedimiento manual y el programado son correctos.




### Parte B:
Para la parte B será necesario calcular la correlación cruzada de dos señales que serán las siguientes:
`x1[nTs] = cos(2π100nTs) para 0 ≤ n < 9`  y `x2[nTs] = sin(2π100nTs) para 0 ≤ n <9` y para `Ts = 1.25ms`
Comenzaremos haciendo el cálculo de la correlación cruzada a mano que nos dará lo siguiente: 

Y luego haremos la gráfica.


Y procederemos con el código en Python para verificar que lo hecho a mano es correcto: 
En primer lugar se declaran las variables y las señales que serán correlacionadas.
```
Ts = 1.25e-3
f0 = 100
n = np.arange(9)

x1 = np.cos(2*np.pi*f0*n*Ts)
x2 = np.sin(2*np.pi*f0*n*Ts)
```
Y a través de funciones de Python calculamos la correlación cruzada.
```
N = len(x1)
r = []
lags = range(-N+1, N)
```
Donde `N` es el número de muestras de la señal, que en este caso serán 9, `r` será un vector que almacenará los valores de correlación para cada retardo y `lags` es el rango de retardos (k) que va desde -(N-1) hasta +(N-1).
Y seguiremos con el cálculo de los retardos: 

```
for k in lags:
    suma = 0
    for i in range(N):
        j = i + k
        if 0 <= j < N:
            suma += x1[i] * x2[j]
    r.append(suma)
print("Valores de la correlación cruzada:")
for k, val in zip(lags, r):
    print(f"k={k:2d}  ->  {val:.4f}")
```

En esta parte se hace un ciclo que recorre cada retardo `k (for k, val in zip(lags, r):)` y un ciclo que recorrerá cada muestra `i` y hará la suma de las muestras con los retardos a través de ` j = i + k`.
También será necesario usar un if para asegurar que `j`  está dentro del rango de la señal, si es así hará la suma de los productos y almacenará el resultado en la lista `r`. 
Básicamente cumple la fórmula que fue usada cuando se calculó la correlación cruzada a mano.
Y se imprimen los retardos:
`k=-8  =  0.0000, k=-7  =  0.7071, k=-6  =  1.5000, k=-5  =  1.4142, k=-4  =  0.0000, k=-3  =  -2.1213, k=-2  =  -3.5000, k=-1  =  -2.8284, k= 0  =  -0.0000, k= 1  =  2.8284, k= 2  =  3.5000, k= 3  =  2.1213, k= 4  =  -0.0000, k= 5  =  -1.4142
, k= 6  =  -1.5000, k= 7  =  -0.7071, k= 8  =  -0.0000`

Finalmente graficamos y obtenemos lo siguiente: 
```
# Graficamos
plt.stem(lags, r)
plt.title("Correlación cruzada")
plt.xlabel("Retardo k")
plt.ylabel("r (x1x2)")
plt.grid(True)
plt.show()
```

<img width="565" height="455" alt="image" src="https://github.com/user-attachments/assets/94efe047-9294-4200-8f44-7cedea577551" />

Y podremos observar que tiene una secuencia discreta y simétrica, ya que tiene valores positivos a la derecha de `k = 0` y hacia la izquierda estos son negativos. Esta señal a su vez alterna valores positivos y negativos, lo que nos muestra una especie de onda.
Observamos que su máximo principal alrededor de k ≈ +2, con un valor cercano a 3.4, y su mínimo principal alrededor de k ≈ –2, con un valor cercano a –3.3. Lo que nos puede indicar que la mayor similitud entre ambas ondas se da cuando la señal x2 se desplaza aproximadamente 2 muestras hacia la derecha con respecto a x1. Es decir que la gráfica confirma que x1 y x2 son la misma frecuencia pero con un desfase de 90°, y la correlación cruzada capta ese desfase como el pico positivo en k=+2 y con el negativo en k=–2.

Finalmente podremos interpretar que la correlación cruzada es útil en el procesamiento digital de señales para la detección de una señal conocida dentro de ruido, para estimar retrasos entre dos señales cuando son medidas con dos sensores distintos, para analizar la similitud entre canales (confirmando si dos señales fueron capturadas con la misma fuente o si son filtradas una de la otra) y para analizar sistemas lineales (estudiando la respuesta de un sistema probando con señales y correlacionando la salida con la entrada).

### Parte C: parte a 
 
Un electroculograma (EOG) es una prueba médica utilizada para medir la actividad eléctrica generada por los movimientos oculares, registra la diferencia de potencial eléctrico entre la córnea (positiva) y la retina (negativa), formando un dipolo eléctrico. Se colocan pequeños electrodos cerca de los ojos para captar los cambios de voltaje que ocurren cuando los ojos se mueven. Es especialmente útil en oftalmología y neurología para evaluar el funcionamiento de ciertas estructuras del ojo y detectar posibles alteraciones, la prueba dura unos 45 minutos e incluye fases de adaptación a la luz y oscuridad.  

En cuanto a su frecuencia, el EOG se considera una señal de baja frecuencia, con un rango típico entre 0.1 Hz y 30 Hz, según el tipo de movimiento ocular. Los movimientos lentos como la fijación o el seguimiento generan señales entre 0.1 Hz y 10 Hz, mientras que los movimientos rápidos como los sacádicos pueden alcanzar hasta 30 Hz. Este rango permite registrar adecuadamente la actividad ocular sin interferencias de señales de mayor frecuencia como las del EEG o EMG, también a veces el ojo experimenta temblores que pueden alcanzar oscilaciones de alta frecuencia (30-150 Hz) y muy baja amplitud. 

Se descargó un EOG en .txt del generador para graficarlo en colab y a su vez obtener algunos datos. Para esto se tuvo en cuenta la frecuencia de Nyquist que es la mitad de la frecuencia de muestreo necesaria para capturar adecuadamente todas las componentes de frecuencia de una señal sin que ocurra aliasing. Es decir, si la señal tiene una componente de frecuencia máxima, la frecuencia de muestreo debe ser al menos el doble de la frecuencia maxima. Entonces se tomó la frecuencia máxima de 150 Hz y se multiplico por 2, lo que dio 300 Hz y según la guia este valor se multiplica por 4, dando 1200 Hz, que fue el valor de frecuencia de muestreo usado para digitalizar la señal.  

       ruta = "/content/drive/MyDrive/Colab Notebooks/senal.txt"
       senal = np.loadtxt(ruta) * 1000  
       fs = 1200
       tiempo = np.arange(len(senal)) / fs
       
       plt.figure(figsize=(12,4))
       plt.plot(tiempo, senal)
       plt.title("Señal EOG")
       plt.xlabel("Tiempo [s]")
       plt.ylabel("Voltaje [mV]")
       plt.grid()
       plt.show()
<img width="1026" height="393" alt="image" src="https://github.com/user-attachments/assets/f9d9162d-4f61-427b-bdba-871281fda9a6" />

Se obtuvieron los datos estadísticos de la señal:

       print("=== DATOS ESTADÍSTICOS DE LA SEÑAL ===")
       print("Media:", round(np.mean(senal), 4), "mV")
       print("Mediana:", round(np.median(senal), 4), "mV")
       print("Desviación estándar:", round(np.std(senal), 4), "mV")
       print("Valor mínimo:", round(np.min(senal), 4), "mV")
       print("Valor máximo:", round(np.max(senal), 4), "mV")
       
**=== DATOS ESTADÍSTICOS DE LA SEÑAL ===**  
Media: 159.1661 mV  
Mediana: 92.154 mV  
Desviación estándar: 379.9427 mV  
Valor mínimo: -1379.9736 mV  
Valor máximo: 1484.7332 mV  

**Convolución**  
Para la convolución fue necesario poner filtro, ya que inicialmente se veía así:
<img width="1021" height="393" alt="image" src="https://github.com/user-attachments/assets/ea83ab83-717d-4440-8322-5eb2fe416bf4" />

Se aplicó un filtro de media móvil con una ventana de 50 muestras. Dado que la frecuencia de muestreo es de 1200 Hz, cada muestra corresponde a aproximadamente 0,83 ms. Por lo tanto, una ventana de 50 muestras equivale a un intervalo temporal de alrededor de 42 ms. Este filtro actúa como un suavizador, reduciendo las variaciones rápidas o de alta frecuencia de la señal y resaltando las tendencias más lentas y relevantes para el análisis. Se sabe que equivale a 42 ms al dividir el tamaño de la ventana (50) entre la frecuencia de muestrreo (1200 Hz).

<img width="1017" height="393" alt="image" src="https://github.com/user-attachments/assets/33beeb2e-808b-4867-a8e8-70b3f7415faf" />

**Correlación**  
Para esta parte se hizo una autocorrelación, ya que solo teniamos una señal y no se podia hacer una correlación cruzada, inicalmente la gráfica se veía así:

      auto_corr = np.correlate(senal, senal, mode='full')
      
      plt.plot(auto_corr)
      plt.title("Autocorrelación (sin normalizar ni centrar)")
      plt.xlabel("Desfase [muestras]")
      plt.ylabel("Correlación")
      plt.show()

<img width="578" height="455" alt="image" src="https://github.com/user-attachments/assets/c887f41a-79f8-4c71-8dfc-cee9e5e66ea1" />

Acá ya se se quitó la media de la señal para que quede centrada en cero, se normaliza para que el valor máximo sea 1 y sea más fácil de comparar, y se pasa el eje de desfases a segundos dividiendo entre la frecuencia de muestreo en lugar de dejarlo en número de muestras.  

      auto_corr = np.correlate(senal - np.mean(senal), senal - np.mean(senal), mode='full')
      auto_corr = auto_corr / np.max(auto_corr)
      lags = np.arange(-len(senal)+1, len(senal)) / fs

      plt.figure(figsize=(12,4))
      plt.plot(lags, auto_corr, color="purple")
      plt.title("Autocorrelación de la señal")
      plt.xlabel("Desfase [s]")
      plt.ylabel("Correlación normalizada")
      plt.grid()
      plt.show()
<img width="1017" height="393" alt="image" src="https://github.com/user-attachments/assets/a513c844-02a0-42cd-a7ff-cb3122bedd83" />

**Clasificación de la señal**  
El EOG puede clasificarse como **aleatorio**, ya que se trata de una señal fisiológica influenciada por múltiples factores biológicos y por la presencia inevitable de ruido. Esto hace que no sea posible predecirla de manera exacta en cada instante de tiempo.  

En cuanto a su periodicidad, la señal es **aperiódica**, dado que no presenta un patrón repetitivo fijo a lo largo del tiempo. Los movimientos oculares son variables y dependen de estímulos externos o del comportamiento espontáneo de la persona, por lo cual no siguen un ciclo estable.  

Finalmente, la señal es **analógica**, ya que se origina como una variación continua de potencial eléctrico en la superficie de la piel alrededor de los ojos. Sin embargo, en este trabajo se utiliza su versión digitalizada, la cual permite procesarla y analizarla mediante herramientas computacionales.

## Parte b 

Para hallar la transformada de fourier de la señal, la densidad espectral de potencia, y los datos estadisticos se utilizo el siguiete codigo:

    fft_resultado = np.fft.fft(senal_mV - np.mean(senal_mV))
    frecuencias_fft = np.fft.fftfreq(len(fft_resultado), 1/frecuencia_muestreo)
    magnitud_fft = np.abs(fft_resultado)

Se aplicó la Transformada de Fourier a la señal, lo que permitió transformarla del dominio del tiempo al dominio de la frecuencia. De esta forma se identificaron las frecuencias presentes en la señal. Para un análisis más claro, se graficaron solo las frecuencias entre 0 y 100 Hz, que es donde se concentra la información de interés.

<img width="1001" height="393" alt="image" src="https://github.com/user-attachments/assets/996bb492-b8d8-48e6-bd99-d48105f1dcf2" />

En esta gráfica se observan los picos de frecuencia de la señal. La energía está muy concentrada entre 0 y 15 Hz, con un pico principal cerca de 5 Hz, lo que indica que la señal tiene componentes de baja frecuencia dominantes.
A partir de 20 Hz, la magnitud disminuye drásticamente y se mantiene muy baja hasta los 100 Hz, lo que confirma que casi no hay contenido en altas frecuencias.
Las pequeñas variaciones en la parte alta del espectro son principalmente ruido del sistema de adquisición o interferencias externas.


    frecuencias_psd, potencia_psd = welch(senal_mV, frecuencia_muestreo, nperseg=1024)

Luego se calculó la Densidad Espectral de Potencia (PSD) empleando el método de Welch, con el fin de visualizar cómo se distribuye la energía de la señal a lo largo del espectro de frecuencias de manera más estable y menos sensible al ruido que la FFT.

<img width="1004" height="393" alt="image" src="https://github.com/user-attachments/assets/2d7d4c58-7fa2-4f01-8e74-f7443a2ef301" />

La PSD muestra la distribución de energía de forma suavizada y más fácil de interpretar.
La mayor densidad de potencia se encuentra por debajo de 10 Hz, lo que significa que casi toda la información relevante de la señal está en ese rango.
Después de los 20 Hz, la potencia cae de forma significativa, lo que reafirma que las frecuencias altas tienen muy poca contribución útil.


    frecuencia_media = np.sum(frecuencias_filtradas * magnitud_filtrada) / np.sum(magnitud_filtrada)
    magnitud_acumulada = np.cumsum(magnitud_filtrada)
    frecuencia_mediana = frecuencias_filtradas[np.where(magnitud_acumulada >= magnitud_acumulada[-1]/2)[0][0]]
    desviacion_frecuencia = np.sqrt(np.sum(((frecuencias_filtradas - frecuencia_media)**2) * magnitud_filtrada) / np.sum(magnitud_filtrada))
    
Se calcularon los principales estadísticos en el dominio de la frecuencia: la frecuencia media, que indica el punto central de la energía en el espectro; la frecuencia mediana, que divide la energía en dos partes iguales; y la desviación estándar, que mide la dispersión de la energía alrededor de la media.

=== Estadísticos en Frecuencia (0-100 Hz) ===

Frecuencia media: 25.14 Hz

Frecuencia mediana: 14.40 Hz

Desviación estándar: 25.09 Hz

    plt.figure(figsize=(12,4))
    plt.hist(frecuencias_filtradas, bins=50, weights=magnitud_filtrada)
    plt.xlim(0, 80)
    plt.title("Histograma de Frecuencias (0-80 Hz)")
    plt.xlabel("Frecuencia [Hz]")
    plt.ylabel("Energía relativa")
    plt.grid()
    plt.show()

Finalmente, se elaboró un histograma de frecuencias ponderado por la magnitud, que permitió visualizar de forma sencilla en qué rangos se concentra la energía de la señal. Este resultado confirmó que la mayor parte de la energía está en las frecuencias bajas, como es esperado para señales biológicas como la EOG.

<img width="1010" height="393" alt="image" src="https://github.com/user-attachments/assets/afa189f6-9c61-4819-8eef-477517c86398" />

El histograma confirma de manera visual que la mayoría de la energía está en frecuencias bajas.
La mayor cantidad de barras se encuentra acumulada entre 0 y 20 Hz, y casi no aparecen barras en frecuencias más altas, lo que coincide con la FFT y la PSD.
Esto muestra claramente que la señal es predominantemente de baja frecuencia, como es característico de una señal EOG.


### Referencias:
- Gila, L., Villanueva, A., & Cabeza, R. (2009). Fisiopatología y técnicas de registro de los movimientos oculares. Anales del Sistema Sanitario de Navarra, 32(Supl. 3), 9–26. https://scielo.isciii.es/pdf/asisna/v32s3/original2.pdf
- MathWorks. (s.f.). Convolución - MATLAB & Simulink. https://la.mathworks.com/discovery/convolution.html
- Oppenheim, A. V., Willsky, A. S., & Nawab, S. H. (1997). Signals and Systems (2nd ed.). Prentice Hall. https://archive.org/details/OppenheimSignalsAndSystems2ndEd
- Tech Lib. (s.f.). Frecuencia de Nyquist - Definición y explicación. Recuperado el 21 de septiembre de 2025, de https://techlib.net/techedu/frecuencia-de-nyquist/
- Thai, J. (2025, 20 de mayo). Explicación de la tasa de Nyquist y el filtro antialiasing. ErdosMiller. https://info.erdosmiller.com/es/blog/explicaci%C3%B3n-de-la-tasa-de-nyquist-y-el-filtro-antialiasing
- Bounchaleun, A. (2019). An Elementary Introduction to Fast Fourier Transform Algorithms. University of Chicago, Mathematics Department.
- Recuperado de https://math.uchicago.edu/~may/REU2019/REUPapers/Bounchaleun.pdf

- Solomon Jr, O. M. (1984). PSD computations using Welch’s method. Sandia National Laboratories.
Recuperado de https://www.osti.gov/servlets/purl/5688766

- Same, M. H., Bouallegue, A., & Hentati, A. (2021). Simplified Welch Algorithm for Spectrum Monitoring. Applied Sciences, 11(1), 86.
https://doi.org/10.3390/app11010086













