# tags

Detección y pose de marcadores AprilTag y ArUco, lista para usarse en un robot: una librería en Python y C++ sobre OpenCV que detecta uno o varios marcadores, estima su pose con su incertidumbre y la entrega en el marco que el robot necesita. Código pensado para reutilizarse tal cual en otro proyecto, no para leerse y reescribirse.

Alrededor de la librería, ejemplos completos de uso: acoplarse a una estación, localizarse en un cuarto, calibrar la cámara contra el brazo, tomar una pieza. Cada uno corre solo con la librería, dentro de ROS 2, y en simulación o en un robot real, y cada uno mide su error.

Es el código que acompaña al [generador de AprilTag y ArUco](https://ingeniumhub.org/es/herramientas/generador-de-tags) de Ingenium Hub: los marcadores salen de ahí, y la página explica la teoría, las estrategias de colocación y los casos reales en los que se basan los ejemplos.

*AprilTag and ArUco detection and pose estimation, ready for robots: a Python and C++ library on OpenCV that detects one or several markers, estimates their pose with its uncertainty and delivers it in the frame the robot needs, written to be reused as is. Around it, complete examples (docking, localization, hand-eye calibration, picking) that run standalone, inside ROS 2, and in simulation or on a real robot, each with its own error measurement. Companion repo to the Ingenium Hub tag generator. Docs in Spanish; code and comments in English.*

## Estado

En construcción. Todavía no hay código publicado.

## Licencia

Código bajo MIT. Marcadores y textos, CC BY 4.0.
