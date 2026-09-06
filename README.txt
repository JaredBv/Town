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
