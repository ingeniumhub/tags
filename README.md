# tags

Un robot necesita saber dónde están las cosas y dónde está él: la estación de carga, la pieza que va a tomar, la pared del pasillo. Una cámara es el sensor más barato para eso, pero entrega píxeles, no metros, y lo que hay en una escena normal se parece demasiado entre sí y cambia con la luz.

Un marcador fiducial resuelve exactamente eso. Es un patrón diseñado para que la cámara lo encuentre sin dudar, sepa cuál es y pueda medirlo: un cuadrado blanco y negro con un borde que se ve de lejos, una rejilla de bits que dice su ID, y cuatro esquinas que, con el tamaño real y la calibración de la cámara, dan su posición y orientación en 3D. Pegado en la pared, en la estación o en la pieza, le da al robot una referencia con identidad y pose desde un solo cuadro de video, sin entrenar nada. AprilTag y ArUco son las dos familias que importan; las dos son abiertas y las dos están en OpenCV.

La explicación completa, con diagramas, las estrategias de colocación y los casos reales, está en la página que acompaña a este repo: [Fiduciales en robótica](https://ingeniumhub.org/es/herramientas/generador-de-tags). Al final de esa página hay un generador para imprimir los marcadores a tamaño real.

## Qué hay aquí

Nada que inventar: los detectores ya existen y son buenos. Lo que falta es saber cuál usar en cada caso, con qué parámetros, y cómo se conecta con el resto del robot. Eso es este repo: una guía de los detectores que vale la pena usar, probados con la misma cámara y el mismo marcador, y ejemplos completos armados con el mejor para cada caso.

**Los detectores**, documentados uno por uno (instalar, configurar, qué devuelve, dónde falla) y medidos con la misma prueba (cuadros por segundo, distancia máxima, error contra la regla, comportamiento en ángulo):

- **OpenCV** (`cv2.aruco`): ArUco y los diccionarios AprilTag, en Python y C++, sin instalar nada más. Para empezar, para scripts y para cualquier PC.
- **AprilTag 3** (la librería de Michigan, en C): la referencia en precisión y velocidad en CPU; en ROS 2 vive como `apriltag_ros`. Para el robot de producción sin GPU.
- **Isaac ROS AprilTag** (NVIDIA): la detección en GPU, para Jetson y robots con cámara a alta resolución o varias cámaras. Qué gana, qué cuesta y sus límites (hoy solo 36h11 en CUDA).
- Y los que resuelven algo que los anteriores no: **TagSLAM** (construir el mapa de marcadores en vez de medirlo) y los marcadores **fractales** de ArUco (ver de lejos y de cerca con el mismo marcador).

**Los ejemplos**, en el orden en que se aprende, cada uno con sus scripts, su paquete de ROS 2, un mundo de simulación con los marcadores ya puestos, y lo necesario para repetirlo en un robot real:

1. **Un marcador y su pose.** Detectar, estimar la pose y dibujarla. Ver qué pasa al alejarse, al girarlo y al declarar mal el tamaño.
2. **Calibrar la cámara.** Con un tablero ChArUco, y comprobar que la distancia medida coincide con la regla.
3. **Ir hacia un marcador.** Girar hasta tenerlo al centro, avanzar hasta la distancia deseada, acoplarse en una orientación concreta.
4. **Varios marcadores en un cuarto.** Que el robot sepa dónde está con cualquiera que vea, sin saltos al cambiar el marcador visible.
5. **La cámara en el brazo.** Calibración mano-ojo y tomar una pieza con un marcador en ella.
6. **Un reto.** Un recorrido de marcador en marcador sin tocar nada.

Cada ejemplo dice qué detector usa y por qué, qué mide y cuánto error da.

## Estado

En construcción. Todavía no hay código publicado; este README dice qué va a haber y en qué orden.

## Licencia

Código bajo MIT. Marcadores y textos, CC BY 4.0.
