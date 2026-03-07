# PARCIAL

# 1. Responda las siguientes preguntas:

 ## ¿Qué son los microcontroladores y los microprocesadores?
  ### Microcontroladores:
  Son dispositivos electrónicos programables que integran en un solo circuito la CPU, memoria y puertos de entrada y salida. Se utilizan para controlar funciones específicas dentro de un sistema electrónico.

  ### Microprocesadores:
  Son circuitos integrados encargados de procesar datos y ejecutar instrucciones. Funcionan como la CPU de un sistema y normalmente necesitan memoria y otros componentes externos para trabajar.

 ## Defina la arquitectura Von Neumann y la Arquitectura de Harvard además: 
 
  ### a. mencionar sus caracteristica
  
  ### b. mencionar  sus ventajas
  
  ### c. mencionar sus diferencias
  
 
  ### Von Neumann
  Es una arquitectura donde la memoria de datos y la memoria de programa están en el mismo espacio de memoria y usan el mismo bus para comunicarse con la CPU.

  #### Caracteristicas
   * Usa una sola memoria para datos e instrucciones.
   * Utiliza un mismo bus para acceder a la memoria.
   * La CPU procesa las instrucciones de forma secuencial.

  #### Ventajas
   * Diseño más simple.
   * Menor costo de implementación.
  
  
  ### Harvard
  Es una arquitectura donde la memoria de datos y la memoria de programa están separadas, cada una con su propio bus, lo que permite acceder a ambas al mismo tiempo.

  #### Carcateristicas
   * Tiene memoria separada para datos y para instrucciones.
   * Usa buses independientes para cada memoria.
   * Permite acceder a datos e instrucciones al mismo tiempo.

  #### Ventajas 
   * Mayor velocidad de procesamiento.
   * Mejor rendimiento del sistema.

  #### Diferencias
   * En Von Neumann los datos y las instrucciones comparten la misma memoria; en Harvard están separadas.
   * Von Neumann usa un solo bus; Harvard usa buses independientes.
   * Harvard suele ser más rápida porque puede acceder a datos e instrucciones al mismo tiempo.

 ## ¿Qué son los procesadores tipos RISC y tipo CISC?
  Son procesadores que utilizan un conjunto pequeño de instrucciones simples. Están diseñados para ejecutar las instrucciones de forma rápida y eficiente.

 ## ¿Qué es ARM (Advanced RISC Machine)?
 
  ### a. Exponer sus características
  
  ### b. Exponer sus ventajas
  
  ### c. Exponer si es muy usado en la actualidad.

  ARM es una arquitectura de procesadores basada en el modelo RISC, diseñada para ofrecer buen rendimiento con bajo consumo de energía.

  #### Caractareristicas
   * Arquitectura RISC.
   * Bajo consumo de energía.
   * Alta eficiencia en procesamiento.

  #### Ventajas
   * Menor consumo de batería.
   * Buen rendimiento.
   * Diseño eficiente para dispositivos pequeños.

 ## ¿Cuál es la arquitecura de Arduino ? Y ¿qué características tiene?
  Las placas Arduino utilizan arquitectura Harvard.

   #### Características:
   * Microcontroladores basados en arquitectura Harvard.
   * Separación entre memoria de datos y memoria de programa.
   * Fácil programación mediante el entorno Arduino IDE.
   * Amplio uso en proyectos educativos y prototipos electrónicos.

 ## ¿Cuál es la arquitectura de PIC16F887 y sus principales características?
  El PIC16F887 utiliza arquitectura Harvard

   #### Características:
   * Microcontrolador de 8 bits.
   * Memoria de programa tipo Flash.
   * Varios puertos de entrada y salida digitales.
   * Convertidor analógico-digital (ADC).
   * Temporizadores internos.
   * Bajo consumo de energía.



# 2. Plantee una solución paso a paso de las situaciones descritas con lo aprendido en clase
El propósito de los estudiantes de ingeniería de telecomunicaciones de compensar es el planteamiento de una plataforma que permita el reconocimiento de las herramientas que existen en un laboratorio y también a las personas que están en el mismo donde se observe si se movilizan a una velocidad prudente o si están generando movimientos muy rápidos por medio de sistemas embebidos
Formule de manera robusta lo siguiente:

## a. ¿Cómo plantearía el desarrollo de una base de datos con imágenes de los diferentes elementos de un laboratorio de telecomunicaciones?

Primero se deben tomar muchas fotos de los elementos que hay en el laboratorio, por ejemplo routers, multímetros, cables, protoboards o antenas. Las fotos se pueden tomar desde diferentes ángulos y con distintas posiciones para que el sistema pueda reconocer mejor los objetos.
Después las imágenes se organizan en carpetas según el objeto. Por ejemplo, una carpeta para routers, otra para cables y otra para multímetros. De esta forma el programa puede aprender a diferenciar cada elemento.
Esta base de datos de imágenes será la que se utilice para entrenar el sistema de reconocimiento.

## b. ¿Cómo crearía un sistema clasificador de elementos con la librería media pipe?

Para crear el clasificador se puede usar MediaPipe junto con Python y la cámara del computador. El programa captura imágenes en tiempo real y analiza lo que aparece en la cámara.
Luego el sistema compara la imagen con las que están en la base de datos y trata de identificar qué objeto es. Cuando reconoce el objeto, el programa puede mostrar en pantalla el nombre del elemento que detectó.
De esta forma se podría reconocer automáticamente las herramientas del laboratorio.

## c. ¿Cómo reconocería el sistema la velocidad de las personas en el laboratorio?

Para esto se puede usar MediaPipe Pose, que permite identificar las partes del cuerpo de una persona usando la cámara.
El sistema analiza cómo cambia la posición de la persona entre un momento y otro. Si el cambio de posición es muy rápido, el sistema puede identificar que la persona se está moviendo rápido o corriendo.
También se puede usar un sensor de movimiento conectado al PIC16F887 para detectar cuando una persona pasa por una zona específica. Con la información del sensor y de la cámara se puede tener una mejor idea de la velocidad de movimiento.

## d. ¿Cómo haría un despliegue en una plataforma web o móvil?

Para mostrar la información se puede crear una página web o una aplicación sencilla donde se vean los resultados del sistema.
El programa que procesa la cámara enviaría la información a la plataforma, por ejemplo mostrando qué objeto fue detectado o si una persona se está moviendo muy rápido.
De esta forma se podría monitorear lo que pasa en el laboratorio desde un computador o un celular.




 


# 3. Crear un algoritmo sencillo que solo me muestre puntos en el pulgar
<img width="2409" height="957" alt="image" src="https://github.com/user-attachments/assets/97f72df2-7a22-4e78-ad9f-bd16d463669f" />

## algoritmo base de COOLAB

```# 1. Instalaciones y Descargas
!pip install -q mediapipe
!wget -q -O hand_landmarker.task https://storage.googleapis.com/mediapipe-models/hand_landmarker/hand_landmarker/float16/1/hand_landmarker.task
!wget -q -O image.jpg https://storage.googleapis.com/mediapipe-tasks/hand_landmarker/woman_hands.jpg

# 2. Importaciones
import cv2
import numpy as np
import mediapipe as mp
from mediapipe.tasks import python
from mediapipe.tasks.python import vision
from google.colab.patches import cv2_imshow

# 3. Función de dibujo manual (Sin usar mp.solutions)
def draw_landmarks_manual(rgb_image, detection_result):
    annotated_image = np.copy(rgb_image)
    h, w, _ = annotated_image.shape

    # Definir conexiones de la mano (basado en la documentación oficial)
    # Cada tupla es (inicio, fin) de un hueso
    CONNECTIONS = [
        (0, 1), (1, 2), (2, 3), (3, 4),           # Pulgar
        (0, 5), (5, 6), (6, 7), (7, 8),           # Índice
        (9, 10), (10, 11), (11, 12),              # Medio
        (13, 14), (14, 15), (15, 16),             # Anular
        (0, 17), (17, 18), (18, 19), (19, 20),    # Meñique
        (5, 9), (9, 13), (13, 17)                 # Palma
    ]

    for hand_landmarks in detection_result.hand_landmarks:
        # 1. Dibujar las líneas (conexiones)
        for connection in CONNECTIONS:
            start_idx = connection[0]
            end_idx = connection[1]
            
            start_point = (int(hand_landmarks[start_idx].x * w), int(hand_landmarks[start_idx].y * h))
            end_point = (int(hand_landmarks[end_idx].x * w), int(hand_landmarks[end_idx].y * h))
            
            cv2.line(annotated_image, start_point, end_point, (255, 255, 255), 2)

        # 2. Dibujar los puntos (landmarks)
        for landmark in hand_landmarks:
            cx, cy = int(landmark.x * w), int(landmark.y * h)
            cv2.circle(annotated_image, (cx, cy), 5, (0, 0, 255), -1)

    return annotated_image

# 4. Ejecución Principal
# Configurar el detector
base_options = python.BaseOptions(model_asset_path='hand_landmarker.task')
options = vision.HandLandmarkerOptions(base_options=base_options, num_hands=2)
detector = vision.HandLandmarker.create_from_options(options)

# Cargar imagen
image = mp.Image.create_from_file("image.jpg")

# Detectar
detection_result = detector.detect(image)

# Dibujar y mostrar
if detection_result.hand_landmarks:
    annotated_image = draw_landmarks_manual(image.numpy_view(), detection_result)
    # Convertir de RGB (MediaPipe) a BGR (OpenCV) para mostrar correctamente
    cv2_imshow(cv2.cvtColor(annotated_image, cv2.COLOR_RGB2BGR))
else:
    print("No se detectaron manos en la imagen.")```



