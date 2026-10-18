# tags

Un robot necesita saber dónde están las cosas y dónde está él: la estación de carga, la pieza que va a tomar, la pared del pasillo. Una cámara es el sensor más barato para eso, pero entrega píxeles, no metros, y lo que hay en una escena normal se parece demasiado entre sí y cambia con la luz.

Un marcador fiducial resuelve exactamente eso. Es un patrón diseñado para que la cámara lo encuentre sin dudar, sepa cuál es y pueda medirlo: un cuadrado blanco y negro con un borde que se ve de lejos, una rejilla de bits que dice su ID, y cuatro esquinas que, con el tamaño real y la calibración de la cámara, dan su posición y orientación en 3D. Pegado en la pared, en la estación o en la pieza, le da al robot una referencia con identidad y pose desde un solo cuadro de video, sin entrenar nada. AprilTag y ArUco son las dos familias que importan; las dos son abiertas y las dos están en OpenCV.

La explicación completa, con diagramas, las estrategias de colocación y los casos reales, está en la página que acompaña a este repo: [Fiduciales en robótica](https://ingeniumhub.org/es/herramientas/generador-de-tags). Al final de esa página hay un generador para imprimir los marcadores a tamaño real.

## Qué hay aquí

Una librería en Python y C++ sobre OpenCV que detecta uno o varios marcadores, estima su pose con su incertidumbre y la entrega en el marco que el robot necesita. Escrita para reutilizarse tal cual en otro proyecto.

Y ejemplos que siguen el mismo orden en que se aprende, cada uno apoyado en el anterior:

1. **Un marcador y su pose.** Detectar, estimar la pose y dibujarla sobre la imagen. Ver qué pasa al alejarse, al girarlo y al declarar mal el tamaño.
2. **Calibrar la cámara.** Con un tablero ChArUco, y comprobar que la distancia medida coincide con la regla.
3. **Ir hacia un marcador.** Girar hasta tenerlo al centro, avanzar hasta la distancia deseada, acoplarse en una orientación concreta.
4. **Varios marcadores en un cuarto.** Que el robot sepa dónde está con cualquiera que vea, y que la pose no salte cuando cambia el marcador visible.
5. **La cámara en el brazo.** Calibración mano-ojo y tomar una pieza con un marcador en ella.
6. **Un reto.** Un recorrido de marcador en marcador sin tocar nada.

Cada ejemplo se puede correr solo con la librería, dentro de ROS 2, y en simulación o en un robot real. Y cada uno mide su error, no solo "funciona".

## Estado

En construcción. Todavía no hay código publicado; este README dice qué va a haber y en qué orden.

## Licencia

Código bajo MIT. Marcadores y textos, CC BY 4.0.
