MINI FPS - ESTRUCTURA DEL PROYECTO
==================================

Archivos principales:
- index.html               Entrada automática; abre el menú principal.
- main.index.html          Menú principal, perfil y selector de mundos.
- worlds/town/index.html   Juego completo del mundo "Town".

Ejecución recomendada:
1. Abre una terminal dentro de la carpeta MiniFPS_Town.
2. Ejecuta: python -m http.server 8000
3. Abre en el navegador: http://localhost:8000

El perfil se guarda con localStorage en el navegador.
Three.js y PointerLockControls se cargan mediante CDN, por lo que el juego requiere conexión a Internet para esas librerías.


MUNDO 2 - BOSQUE INVERNAL
-------------------------
Archivo: mundo2.html
Acceso: desde main.index.html
Características: bosque nevado, pinos densos, nieve ambiental, enemigos tipo oso polar con mayor velocidad base.
Mantiene armas, munición, rondas, chaleco, torretas, jefe final y reinicio de campaña.


MEDIO OESTE - ACTUALIZACIÓN
- Forajidos armados con revólver: disparan cada 5 segundos con proyectil visible, fogonazo y retroceso.
- Nueva arma del jugador: Revólver, cilindro de 6 y 36 balas totales (6 + 30 de reserva). Tecla R para recargar.
- Rondas 1 a 9 normales; dificultad sube 25% por ronda hasta el límite de +125%.
- Ronda 10: jefe vaquero gigante montado a caballo con escopeta de doble cañón funcional.
- Ambientación extra: torre de agua, faroles, cercas, pacas de heno, más polvo y plantas rodadoras animadas.


NUEVAS MECANICAS
- SPRINT GLOBAL: Mantén Shift para correr a x1.7. La energía permite hasta 6 segundos continuos y se regenera completamente en 2.5 segundos al soltar Shift.
- BOSQUE INVERNAL: 6 rondas normales y jefe final en ronda 7. El jefe es un oso polar gigante que lanza rayos de hielo; al impactar reducen la velocidad del jugador 55% durante 3 segundos.
- AGACHARSE GLOBAL: Mantén Ctrl izquierdo o derecho para bajar la cámara a postura agachada. La velocidad se reduce al 45%, el sprint se cancela mientras estés agachado y al soltar Ctrl vuelves suavemente a la altura normal.


CONTROLES POR PLATAFORMA
------------------------
Al seleccionar cualquier mundo desde main.index.html se pregunta PC o Android.
PC: WASD + ratón + teclado con Pointer Lock.
Android: joystick izquierdo para movimiento, joystick derecho para simular la vista del ratón y botones táctiles para Disparar, Saltar, Cambiar arma, Recargar, Sprint, Agacharse, Zoom y Pausa.
La plataforma se transmite por ?platform=pc o ?platform=android.
