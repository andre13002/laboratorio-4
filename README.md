Para la practica de laboratorio, lo primero que hicimos fue una investigación acerca de los siguientes términos: 

-El sistema nervioso autónomo (SNA) controla funciones involuntarias del cuerpo como la frecuencia cardíaca, la digestión y la respiración. Se divide en:
       Simpático: Activa la respuesta de "lucha o huida". Aumenta la frecuencia cardíaca, dilata las pupilas y redirige la sangre a los músculos, preparándonos para la acción. 
       Parasimpático: Promueve la "descanso y digestión". Disminuye la frecuencia cardíaca, contrae las pupilas y aumenta el flujo sanguíneo hacia los órganos digestivos, favoreciendo la recuperación y el descanso.

-La variabilidad de la frecuencia cardíaca (HRV) es una medida de las variaciones en el tiempo entre latidos cardíacos consecutivos (intervalos R-R en el ECG). Es un indicador de la capacidad del SNA para adaptarse a diferentes condiciones fisiológicas y emocionales.
Frecuencias de interés en HRV:
       Baja frecuencia (0.04 - 0.15 Hz): Refleja la actividad del sistema   simpático y parasimpático, asociada con la regulación de la presión arterial y otros procesos lentos.
       Alta frecuencia (0.15 - 0.4 Hz): Relacionada con la actividad parasimpática y la respiración, lo que impacta en la frecuencia cardíaca en ciclos de respiración rápida.

Una alta HRV suele ser signo de buena adaptabilidad del sistema autónomo, mientras que una baja HRV puede indicar estrés, fatiga o problemas cardiovasculares.
  -La transformada wavelet es una herramienta matemática que descompone una señal en diferentes escalas o frecuencias, permitiendo el análisis tanto en el dominio del tiempo como en el de la frecuencia. A diferencia de la transformada de Fourier, que analiza frecuencias globales, la transformada wavelet permite ver cómo las frecuencias cambian a lo largo del tiempo.
        Usos en señales biológicas: En ECG, EEG y HRV, ayuda a identificar variaciones en la actividad a diferentes frecuencias, permitiendo analizar cómo responde el cuerpo a diferentes estímulos o detectar anomalías.
        Tipos de wavelet en señales biológicas:
   Morlet: Amplia, útil para señales biológicas como ECG y EEG, ya que permite el análisis de frecuencia y tiempo simultáneamente.

Luego realizamos un diagrama de flujo para tener todas las acciones en cuenta de acuerdo a lo anterior y se envió vía correo.

![IMG_1109](https://github.com/user-attachments/assets/e499f07f-ceec-4c20-b274-edb1002c926a)
![IMG_1110](https://github.com/user-attachments/assets/e95cbc6d-253d-4587-aeab-2ef4624a2ef1)



se realizo la toma de un ECG de un usuario por medio de la tarjeta de adquisición de arduino con electrodos en el pecho y con el amplificador AD8232, con sus respectivos electrodos como se muestra en la imagen.

![3-2Belectrodos](https://github.com/user-attachments/assets/58fdc173-7944-418a-a282-e8979c4dfe3f)

Se tomo la señal con una frecuencia de muestreo de 250 Hz al ser de ese valor se demora un poco tomándo los los datos, por ende en nuestra señal un segundo son al rededor de 40 segundos. Entonces en el eje x se perciben pocos segundos pero en realidad la señal se capturo durante 5 minutos.
Al tener esto lo que hicimos fue tomarle una captura, que guardamos en el escritorio y luego llamamos a python, donde por medio de una función convertimos en matriz para luego allí gráficar la matriz.


![python](https://github.com/user-attachments/assets/1200b45e-67ab-4968-b171-68db9d3e7a8b)  <img width="471" alt="matriz" src="https://github.com/user-attachments/assets/85f70625-6044-4dc4-b16c-c627a58bd7cc">

<img width="450" alt="ecg sin nada " src="https://github.com/user-attachments/assets/b2724b3d-7ad7-45ed-9534-4a62d9e84f7c">

Cuando estaba finalmente la señal en python, lo que se hizo fue agregar filtros pasa altos y pasa bajos para asi eliminar ruidos por interferencias, ambientes y por campos electromagnéticosticos.

<img width="439" alt="ecg con filtros" src="https://github.com/user-attachments/assets/54f3e3d1-53fd-45d9-99fe-ac4e41010ae8">


Con la señal filtrada calculamos los parámetros básicos de la HRV en el dominio del tiempo, esto es: La variabilidad de la frecuencia cardíaca (HRV, por sus siglas en inglés) es una medida de las variaciones en el tiempo entre latidos consecutivos del corazón, El HRV es una herramienta importante para evaluar la salud del sistema nervioso autónomo y la capacidad del cuerpo para adaptarse a factores de estrés, recuperación y actividad física:
      -Alta HRV: Suele indicar buena adaptabilidad y un equilibrio saludable entre los sistemas nerviosos simpático y parasimpático. Se asocia con una mejor salud cardiovascular y menor riesgo de enfermedades.
      -Baja HRV: Puede ser indicativo de estrés, fatiga, falta de sueño o enfermedades. En contextos médicos, una baja HRV puede asociarse con un mayor riesgo de enfermedades cardiovasculares.
Por esto calculamos:
Los intervalos R-R que son el  tiempo entre dos picos R consecutivos en una señal de electrocardiograma (ECG). Los picos R representan el punto más alto de cada latido en el complejo QRS, que es la parte de la señal ECG correspondiente a la despolarización de los ventrículos cardíacos, y son los puntos más fáciles de identificar en el ECG, se mide en segundos o milisegundos. Este intervalo es crucial en el análisis de la variabilidad de la frecuencia cardíaca (HRV), ya que refleja cómo varía la frecuencia cardíaca con el tiempo y puede ofrecer información sobre el funcionamiento del sistema nervioso autónomo.
Por esto lo calculamos en segundos este intervalo y dio lo siguiente:

<img width="445" alt="R-R" src="https://github.com/user-attachments/assets/25dc6c3b-e5e6-4282-ac98-24b61e4862fc">

<img width="491" alt="INTERVALO R-R" src="https://github.com/user-attachments/assets/7c362546-11e4-4c57-bb19-db26ace8967c">

En los datos de los intervalos R-R calculados, se observa una variabilidad moderada entre los tiempos de cada latido consecutivo, con valores que van de 0.064 a 0.112 segundos. Esta variabilidad es un signo positivo de la capacidad de adaptación del sistema nervioso autónomo, reflejando que tanto el sistema simpático como el parasimpático están ajustando la frecuencia cardíaca en respuesta a las necesidades del cuerpo. Aunque la mayoría de los intervalos se concentran entre 0.07 y 0.08 segundos (lo que sugiere una frecuencia cardíaca promedio entre 75 y 85 latidos por minuto), el intervalo de 0.112 segundos es una posible variación normal o un artefacto en la señal. Este dato nos mostró una frecuencia cardíaca en un rango saludable y una HRV adecuada para un adulto en reposo.

También calculamos la media de estos intervalos y la desviación estándar y dio:

<img width="399" alt="esta" src="https://github.com/user-attachments/assets/ac67f683-4f94-4eb0-8736-9f613fcf27ba">

Esta variabilidad refleja una actividad equilibrada del sistema simpático y parasimpático, indicando que el organismo es capaz de adaptarse a demandas cambiantes, como el estrés o la relajación.

Al analizar esto hicimos  un espectrograma de la HRV usando la transformada wavelet continua, la selecciónnada fue la morlet, segun nuestra primera investigación y obtuvimos una grafica de frecuencia vs tiempo:

<img width="717" alt="espectograma" src="https://github.com/user-attachments/assets/4bdc121b-3408-40d5-9155-8f0aa31806de">

Posterior a eso quisimos ver exactamente en que puntos la morlet coincidió con la señal de ECG y obtuvimos esto:

<img width="444" alt="donde coincide" src="https://github.com/user-attachments/assets/73ecb9f5-940a-40b4-8adf-6e924cb04b8a">

Luego para saber exactamente este dato con mas precisiones calculamos la bondad  y obtuvimos esto: 

<img width="169" alt="bondad" src="https://github.com/user-attachments/assets/e7f99923-8497-468d-8988-ad407fee0010">

En donde: R-squared=Coeficiente de determinación: muestra que la wavelet Morlet puede explicar el 65% de la variabilidad total de la señal ECG original. En otras palabras, el modelo wavelet captura una parte significativa de las características de la señal, pero un 35% de la variabilidad no está representada en la reconstrucción. Idealmente, un R-squared cercano a 1 indicaría una representación más precisa.
MSE= error cuadratico medio: mide el error promedio al cuadrado entre los valores originales y los valores reconstruidos de la señal ECG. 750 muestra que existe una desviación acumulada relativamente alta entre ambas señales, lo que sugiere que la reconstrucción no es perfecta y aún muestra diferencias significativas por los puntos en los que en el eje x la mrolet no se ajusto.
RMSE=Raiz del error cuadratico medio: Al ser la raíz cuadrada del MSE, el RMSE da una interpretación del error en las mismas unidades de la señal (en este caso, milivoltios si la señal ECG está en esta unidad). Un RMSE de 27.5 indica el error promedio de reconstrucción.


Por ultimo realizamos una comparación entre Amplitud promedio en baja frecuencia y la Amplitud promedio en alta frecuencia y obtuvimos esto:

<img width="410" alt="compA" src="https://github.com/user-attachments/assets/71cb94b6-f46d-4815-b11b-eb070786484e">

Podemos ver que la amplitud promedio en la banda de baja frecuencia (0.04 - 0.15 Hz) es de 0.0361, mientras que en la banda de alta frecuencia (0.15 - 0.4 Hz) es de 0.0134. significa que las variaciones más lentas (como las asociadas al control autónomo simpático y parasimpático del ritmo cardíaco) predominan en la señal, ya que la amplitud en baja frecuencia es mayor que en alta frecuencia.

- ¿Qué diferencias se observan entre los análisis en el dominio del tiempo y el dominio tiempo-frecuencia?
El análisis en el dominio del tiempo, como el cálculo de los intervalos R-R y sus estadísticas (media y desviación estándar), se enfoca en variaciones de la HRV sin ofrecer información sobre cómo cambian las frecuencias a lo largo del tiempo. Por otro lado, el análisis tiempo-frecuencia, mediante la transformada wavelet, permite observar la evolución de las frecuencias específicas (como baja y alta frecuencia) a lo largo del tiempo, revelando cambios en la potencia espectral y cómo podrían estar relacionados con las actividades simpática y parasimpática en el sistema nervioso autónomo.

- ¿Qué efecto tiene el uso de diferentes funciones wavelet en los resultados del análisis?
Cada tipo de wavelet tiene una resolución particular en tiempo y frecuencia, lo que afecta la precisión con la que se pueden observar variaciones en las señales. En señales biológicas como el ECG, el tipo de wavelet seleccionado (como Morlet o Daubechies) puede influir en la claridad de la separación de frecuencias de interés, mejorando o limitando la interpretación de los patrones de HRV. Cambiar de wavelet puede resaltar ciertos aspectos de la señal o reducir el ruido en frecuencias específicas.

- ¿Qué aplicaciones reales tiene esta práctica?
Este análisis es fundamental en aplicaciones de monitoreo de salud, como el seguimiento de la respuesta autonómica del corazón en pacientes cardíacos o en estudios de estrés y regulación emocional. En el ámbito biomédico, esta práctica se usa para evaluar la salud del sistema nervioso autónomo, detectar anomalías cardíacas y estudiar la respuesta del corazón ante distintas condiciones fisiológicas. Además, técnicas similares se aplican en dispositivos de monitoreo remoto para pacientes y en estudios de la respuesta cardíaca a intervenciones terapéuticas.
