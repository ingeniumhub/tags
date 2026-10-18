# tags

Un robot necesita saber dónde están las cosas y dónde está él: la estación de carga, la pieza que va a tomar, la pared del pasillo. Una cámara es el sensor más barato para eso, pero entrega píxeles, no metros. Y lo que hay en una escena normal (esquinas de muebles, texturas, sombras) se parece demasiado entre sí y cambia con la luz: el robot ve algo, pero no sabe qué es ni a qué distancia está.

Los marcadores fiduciales existen para resolver exactamente eso. Son patrones diseñados para que una cámara los encuentre sin dudar, sepa cuál es cada uno y pueda medirlos. Un AprilTag o un ArUco es un cuadrado blanco y negro con una rejilla de bits adentro: el borde negro se detecta de lejos y en ángulo, los bits dicen el ID, y las cuatro esquinas, junto con el tamaño real del cuadrado y la calibración de la cámara, dan la posición y la orientación del marcador en 3D. AprilTag nació en 2011 en la Universidad de Michigan; ArUco, en 2014 en la Universidad de Córdoba. Los dos son abiertos y los dos están en OpenCV.

Para qué sirven en la práctica: acoplarse a una base de carga, saber en qué punto de una nave está el robot, calibrar la cámara respecto al brazo, medir dónde quedó una pieza para tomarla, dar referencia a un dron para aterrizar, alinear escaneos 3D. Es la forma más barata de darle a un robot una referencia absoluta: tinta sobre papel.

## Qué hay aquí

Una librería en Python y C++ sobre OpenCV que detecta uno o varios marcadores, estima su pose con su incertidumbre y la entrega en el marco que el robot necesita. Está escrita para reutilizarse tal cual en otro proyecto, no para leerse y reescribirse.

Alrededor de la librería, ejemplos completos de uso: acoplarse a una estación, localizarse en un cuarto, calibrar la cámara contra el brazo, tomar una pieza. Cada uno corre solo con la librería, dentro de ROS 2, y en simulación o en un robot real, y cada uno mide su error.

Es el código que acompaña al [generador de AprilTag y ArUco](https://ingeniumhub.org/es/herramientas/generador-de-tags) de Ingenium Hub: los marcadores salen de ahí, y la página explica la teoría, las estrategias de colocación y los casos reales en los que se basan los ejemplos.

## Estado

En construcción. Todavía no hay código publicado.

## Licencia

Código bajo MIT. Marcadores y textos, CC BY 4.0.
