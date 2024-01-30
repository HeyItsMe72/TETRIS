# Tetris
![HTML5](https://img.shields.io/badge/HTML%20-orange?logo=HTML5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS%20-blue?logo=CSS3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript%20-yellow?logo=JavaScript&logoColor=white)

![VanillaJavaScript](https://img.shields.io/badge/JavaScript-yellow?style=for-the-badge&logo=javascript&logoColor=white)

![JSFuncionalidades](https://img.shields.io/badge/Device%20Detection%20-blue?style=for-the-badge&logo=javascript&logoColor=%23FFF000&label=Canvas&labelColor=%23FF008F&color=%23FF008F)
![StartGame](https://github.com/HeyItsMe72/TETRIS/assets/124311622/aaa39f41-a93e-4ce6-976c-860384bb9a18)
![Game](https://github.com/HeyItsMe72/TETRIS/assets/124311622/660e14fc-f71b-4453-a627-2ce666ffc3dc)

## Introducción
*Tetris* es un proyecto creado con fines de aprendizaje, realizado para experimentar con las funcionalidades de JavaScript. Es un proyecto bastante noble del cual se puede aprender mucho sobre el lenguaje, y aunque el proyecto no busca ser una réplica del juego *Tetris original*, es bastante entretenido al jugarse. Puede ser jugado en computadoras, smartphones y tablets. 

Para crearlo, se utilizaron tecnologías puras: HTML5, CSS3 y Vanilla JavaScript. 

**CSS *styles.css***

En este archivo se encuentran todos los estilos requeridos para el sitio. 

**JavaScript *device-detection.js***

En este archivo se encuentra la lógica que permite al sitio identificar el dispositivo por el cual es visitado, esto permite, en el caso de un usuario vía computadora, tener jugabilidad con su teclado. Por otra parte, para una visita por medio del smartphone, se crea un apartado con botones que permite la jugabilidad. 

Lo anterior es logrado utilizando la propiedad *userAgent*, propia del objeto *navigator* y verificando las coincidencias de esta propiedad con expresiones regex. 

**JavaScript *index.js***

En este archivo se encuentran las funcionalidades principales del sitio, el juego en sí.
Se comienza identificando el dispositivo por el que el sitios es visitado, ejecutando la función *userDeviceInfo()* en cuando el contenido del DOM es cargado (*DOMContentLoaded*). 

Se dibuja el canvas obteniéndolo desde el DOM y se le asigna la escala al contexto, lo que nos permite crear cuadrados de 20x20 pixeles. Para crear el tablero y todo el juego (piezas y solidificaciones) se utilizan Arrays, en términos sencillos, 1 es un cuadro lleno, mientras que 0 está vacío. En este caso, para crear el tablero se llena el contenido a 0. 

Al definir las piezas, se consideran los tetriminos que el juego original aporta, por medio de un objeto que incluya la forma y el color que se le determinó; cada forma es un array de arrays. 

**Funciones**

La función *draw* es una función auxiliar que permite dibujar el tablero y las piezas, definiendo el color de las piezas al quedar solificadas, es decir, que sólo los espacios que tenda 1 en su contenido del Array serán dibujadas de este color. 

La función *checkCollisios* permite identificar cuando una pieza tiene una colisión con otra, o bien, son las orillas, el fin del tablero o el tope (lo que indica un *Game Over*); esto se logra, principalmente, utilizando el operador de [Encadenamiento opcional](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining).

La función *solidifyPieces* permite identificar en el tablero los espacios en el que el hay números 1. Al solidificar las piezas, una nueva pieza debe ser obtenida (de forma aleatoria) y resetada su posición al inicio del tablero de juego. Cada vez que una nueva pieza cae, se debe revisar si existen o no colisiones con el tope del tablero, de ser así, una alerta de *Game Over* es enviada.

La función *removeRows* permite revisar el contenido del Board, si el contenido de una fila entera es igual a 1, la fila es removida y el total de estas filas removidas, son las nuevas filas en blanco son agregadas al incio del tablero. Por cada fila eliminada, el *score* aumenta 10 puntos. 

La función *update* es la función principal, que permite actualizar el contenido mostrado utilizando el método *requestAnimationFrame*. También permite que cada segundo pueda ser posible aumentar la posición en *y* de las piezas, para que se cree una simulación de caída. 

**Listeners**

Existen dos listeners asignados al *document*: "*click*" y "*keydown*". El primero, es lanzado únicamente cuando el dispositivo detectado es un smartphone o tablet. El segundo, por su parte, es lanzado cuando el dispositivo puede contener un teclado físico, permitiendo que la jugabilidad se dé mediante las teclas. 

## Mejoras
![Generales](https://img.shields.io/badge/Generales-red?style=for-the-badge&logoColor=%23FFF000&label=%C3%81reas%20de%20oportunidad&labelColor=FFB600&color=FF0000)

Este proyecto mantiene una simplicidad, pues no busca ser una réplica del juego original, simplemente experimentar con el lenguajes y sus bondades. Aún así, existen mejoras que pueden implementarse y mejorar la experiencia al jugarlo. 

Es cierto que, debido al uso del método *requestAnimationFrame* al abandonar la página del sitio, la pieza ya no sigue bajando, pues no hay un *refresh* del contenido del sitio; a pesar de este comportamiento, una mejora posible es agregar el **botón de pausa**. 

La lógica de este código se ha limitado a pintar la solificación de las piezas de un sólo color, una mejora que podría hacerlo interesante, es que, al solificar las piezas, el pintado sea del color que cada tetrimino declarado sea la correspondiente a su propiedad *color*.

Un buen aspecto de esta clase de juegos y que puede ayudar a mejorarlo, es el registro del *record* mostrando el *score* máximo que ha tenido el usurio dentro de ese navegador; para esto, podría hacerse uso del localStorage, como la forma más sencilla de hacerlo. 

Por ahora, el mensaje de *Game Over* es resumido a una alerta enviada al usuario. Sin embargo, esto puede mejorar haciéndolo mucho más personalizado. 

![SmartphoneTablets](https://img.shields.io/badge/Smartphone%2C%20Tablets%20-red?style=for-the-badge&logoColor=%23FFF000&label=%C3%81reas%20de%20oportunidad&labelColor=FFB600&color=FF0000)

Una buena mejora para la jugabilidad en estos dispositivos, involucra el manejo del click sostenido en los apartados de los botones; manejarlo permitiría que le movimiento de las piezas fuera más rápido. En el teclado físico esto funciona porque el evento utilizado es "*keydown*". 

Por el momento, este sitio sólo puede ser jugado de forma adecuada cuando el dispositivo es posicionado verticalmente; una mejora sería adaptar el contenido del juego al activar el *rotate* de los dispositivos. Este es un cambio un tanto complicado, ya que involucraría hacer cambios en el tamaño del tablero y las piezas, así como disminuir la escala, ya que este juego el principal contenido es más alto que ancho, lo que genera un recorte del área visible para el usuario, obligándolo a deslizar la pantalla continuamente. 


Nota: Proyecto guiado por el Desarrollador Web [Miguel Ángel Durán](https://www.instagram.com/midu.dev/).
