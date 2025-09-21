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

         plt.figure(figsize=(10, 4))
         plt.stem(y)
         plt.title('Señal Resultante y[n]')
         plt.xlabel('Índice n')
         plt.ylabel('Amplitud')
         plt.grid(True)
         plt.show()
   <img width="850" height="393" alt="image" src="https://github.com/user-attachments/assets/5181128b-8ba7-4243-a017-2919f6c3f31b" />
   


**Silvia..**

**Alejandra Torres**

Teniendo el sistema h[n] = {5,6,0,7,4,8} y la señal x[n] = {1,0,1,1,3,2,1,5,9,7}:  
1. Encuentre la señal 𝑦[𝑛] resultante de la convolución usando sumatorias (a mano).
<img width="1488" height="1238" alt="image" src="https://github.com/user-attachments/assets/91ae1dff-e385-4e28-ba72-c7ce268aebe7" />
2. Encuentre la representación gráfica y secuencial (a mano).
<img width="1159" height="775" alt="image" src="https://github.com/user-attachments/assets/25e2b891-aa53-4556-af6d-a24d76f320ac" />
3. Encuentre la señal 𝑦[𝑛] resultante de la convolución usando Python.
   
        h = [5,6,0,0,7,4,8]
        x = [1,0,1,1,3,2,1,5,9,7]
        y = np.convolve(x, h)
       print("y[n] =", y)

### Parte B:

### Parte C:

### Referencias:
- Gila, L., Villanueva, A., & Cabeza, R. (2009). Fisiopatología y técnicas de registro de los movimientos oculares. Anales del Sistema Sanitario de Navarra, 32(Supl. 3), 9–26. https://scielo.isciii.es/pdf/asisna/v32s3/original2.pdf
- MathWorks. (s.f.). Convolución - MATLAB & Simulink. https://la.mathworks.com/discovery/convolution.html
- Oppenheim, A. V., Willsky, A. S., & Nawab, S. H. (1997). Signals and Systems (2nd ed.). Prentice Hall. https://archive.org/details/OppenheimSignalsAndSystems2ndEd
