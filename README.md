# tags

Un robot necesita saber dónde están las cosas y dónde está él: la estación de carga, la pieza que va a tomar, la pared del pasillo. Una cámara es el sensor más barato para eso, pero entrega píxeles, no metros, y lo que hay en una escena normal se parece demasiado entre sí y cambia con la luz.

Un marcador fiducial resuelve exactamente eso. Es un patrón diseñado para que la cámara lo encuentre sin dudar, sepa cuál es y pueda medirlo: un cuadrado blanco y negro con un borde que se ve de lejos, una rejilla de bits que dice su ID, y cuatro esquinas que, con el tamaño real y la calibración de la cámara, dan su posición y orientación en 3D. Pegado en la pared, en la estación o en la pieza, le da al robot una referencia con identidad y pose desde un solo cuadro de video, sin entrenar nada. AprilTag y ArUco son las dos familias que importan; las dos son abiertas y las dos están en OpenCV.

La explicación completa, con diagramas, las estrategias de colocación y los casos reales, está en la página que acompaña a este repo: [Fiduciales en robótica](https://ingeniumhub.org/es/herramientas/generador-de-tags). Al final de esa página hay un generador para imprimir los marcadores a tamaño real.

## Qué hay aquí

Nada que inventar: la detección ya la hacen OpenCV y la librería AprilTag, y en ROS 2 ya existen `apriltag_ros`, tf2, Nav2 y MoveIt. Lo que no existe es el ejemplo completo y armado, que se pueda correr tal cual y repetir en un robot de verdad. Eso es este repo:

- **Scripts con OpenCV**, en Python, para ver y medir sin ROS: detectar, estimar la pose, dibujarla, comparar con la regla.
- **Un paquete de ROS 2** con los launch que conectan cámara, detector, tf2 y lo que consume la pose (el docking de Nav2, el planificador del brazo).
- **Mundos de simulación** con los marcadores ya puestos, a su tamaño, para probar sin hardware.
- **Lo necesario para repetirlo en un robot real**: qué imprimir, dónde pegarlo, cómo calibrar y qué medir para saber que funciona.

Los ejemplos siguen el orden en que se aprende, cada uno apoyado en el anterior:

1. **Un marcador y su pose.** Detectar, estimar la pose y dibujarla sobre la imagen. Ver qué pasa al alejarse, al girarlo y al declarar mal el tamaño.
2. **Calibrar la cámara.** Con un tablero ChArUco, y comprobar que la distancia medida coincide con la regla.
3. **Ir hacia un marcador.** Girar hasta tenerlo al centro, avanzar hasta la distancia deseada, acoplarse en una orientación concreta.
4. **Varios marcadores en un cuarto.** Que el robot sepa dónde está con cualquiera que vea, y que la pose no salte cuando cambia el marcador visible.
5. **La cámara en el brazo.** Calibración mano-ojo y tomar una pieza con un marcador en ella.
6. **Un reto.** Un recorrido de marcador en marcador sin tocar nada.

Cada ejemplo dice qué mide y cuánto error da, no solo que "funciona".

## Estado

En construcción. Todavía no hay código publicado; este README dice qué va a haber y en qué orden.

## Licencia

Código bajo MIT. Marcadores y textos, CC BY 4.0.
