# tags

Marcadores fiduciales (AprilTag y ArUco) en robots: guía comparada de detectores y ejemplos completos con OpenCV, ROS 2, simulación y robot real.

Un marcador fiducial es un cuadrado blanco y negro que una cámara reconoce con certeza: su borde se detecta de lejos, su rejilla de bits codifica un ID y sus cuatro esquinas, con el tamaño real y la calibración de la cámara, dan su posición y orientación en 3D. Los robots los usan para acoplarse a una estación, localizarse en un edificio, calibrar la cámara respecto al brazo y tomar piezas. La explicación completa, con diagramas, estrategias de colocación y casos reales, está en [Fiduciales en robótica](https://ingeniumhub.org/es/herramientas/generador-de-tags), que también incluye un generador para imprimir marcadores a tamaño real.

## Contenido

### Detectores

Cada detector con su instalación, configuración, formato de salida y límites, y los resultados de una misma prueba: cuadros por segundo, distancia máxima de detección, error de posición contra la regla y comportamiento en ángulo, con la misma cámara y el mismo marcador.

| Detector | Qué es | Cuándo usarlo |
|---|---|---|
| OpenCV `cv2.aruco` | ArUco y diccionarios AprilTag en Python y C++, incluido en OpenCV | Scripts, prototipos, cualquier PC |
| AprilTag 3 y `apriltag_ros` | La librería de la Universidad de Michigan, en C, y su nodo de ROS 2 | Robots en producción con CPU |
| Isaac ROS AprilTag | Detección en GPU de NVIDIA para ROS 2 | Jetson, alta resolución, varias cámaras (solo 36h11 en CUDA) |
| TagSLAM | Mapa de marcadores estimado por optimización | Varios marcadores sin medir su posición a mano |
| ArUco fractal | Marcador anidado a varias escalas | Ver el mismo marcador de lejos y de cerca |

### Ejemplos

En orden, cada uno sobre el anterior. Cada ejemplo trae scripts en Python, un paquete de ROS 2 con sus launch, un mundo de simulación con los marcadores colocados a su tamaño real, y las instrucciones para repetirlo en un robot: qué imprimir, dónde ponerlo, cómo calibrar y qué medir.

1. **Un marcador y su pose.** Detección, estimación de pose y visualización. Efecto de la distancia, del ángulo y de un tamaño mal declarado.
2. **Calibración de la cámara.** Intrínsecos con un tablero ChArUco y comprobación de la distancia medida contra la regla.
3. **Navegación hacia un marcador.** Girar hasta centrarlo, avanzar hasta la distancia deseada, acoplarse en una orientación concreta.
4. **Varios marcadores en un cuarto.** Localización con cualquier marcador visible, sin saltos al cambiar de marcador.
5. **Cámara en el brazo.** Calibración mano-ojo y toma de una pieza con marcador.
6. **Reto.** Recorrido de marcador en marcador sin contacto.

Cada ejemplo indica el detector que usa, qué mide y el error obtenido.

## Requisitos

- Python 3.10 o superior y OpenCV con el módulo `aruco` (`opencv-contrib-python`).
- ROS 2 Jazzy para los paquetes y los launch.
- Gazebo para los mundos de simulación.
- Isaac ROS solo para el ejemplo correspondiente, en hardware NVIDIA.

## Estado

En construcción. Todavía no hay código publicado.

## Licencia

Código bajo MIT. Marcadores y textos bajo CC BY 4.0.
