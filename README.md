# Laboratorio2_procesamiento
Lina María Cortés Almonacid  
María Alejandra Torres Cardenas  
Silvia Lorena Vargas Rueda  

## Convolución, correlación y transformada de Fourier
### Parte A:
Teniendo el sistema h[n] = {5,6,0,8,3,4} y la señal x[n] = {1,0,7,6,7,3,6,2,2,9}:  
1. Encuentre la señal 𝑦[𝑛] resultante de la convolución usando sumatorias (a mano). 
<img width="1474" height="646" alt="image" src="https://github.com/user-attachments/assets/78fa8425-e75a-4f4e-b030-6d6e624f6bc0" />

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
   
