DEFUSUAL - ESTRUCTURA DEL PROYECTO
==================================

Archivos principales:
- index.html               Entrada automática; abre el menú principal.
- main.index.html          Menú principal, perfil y selector de mundos.
- worlds/town/index.html   Juego completo del mundo "Town".

Ejecución recomendada:
1. Abre una terminal dentro de la carpeta Defusual.
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
- AGACHARSE GLOBAL: Mantén C para bajar la cámara a postura agachada. La velocidad se reduce al 45%, el sprint se cancela mientras estés agachado y al soltar C vuelves suavemente a la altura normal.


CONTROLES POR PLATAFORMA
------------------------
Al seleccionar cualquier mundo desde main.index.html se muestran PC, Android, Xbox, PlayStation y Nintendo.
PC: WASD + ratón + teclado con Pointer Lock.
Android: joystick izquierdo para movimiento, arrastre sobre la pantalla para mirar y botón de disparo con arrastre para apuntar mientras disparas.
Xbox: ya está habilitado en los tres mundos mediante Gamepad API.
  - Stick izquierdo: mover
  - Stick derecho: mirar
  - RT: disparar / mantener para metralleta
  - LT: apuntar / zoom del francotirador
  - A: saltar e iniciar/reanudar
  - B: agacharse mientras se mantiene
  - L3: sprint mientras se mantiene
  - LB / RB: arma anterior / siguiente
  - X: recargar
  - D-Pad arriba: inspeccionar arma
  - Menu: pausa / reanudar
PlayStation y Nintendo aparecen en el selector pero se configurarán después.
La plataforma se transmite por ?platform=pc, ?platform=android o ?platform=xbox.

ACTUALIZACION - CONFIGURACION Y CHALECO
---------------------------------------
- Bosque Invernal y Medio Oeste: chaleco antibalas activo desde ronda 3.
- Chaleco Nv.1: 3 impactos.
- Chaleco Nv.2: 5 impactos.
- Chaleco Nv.3: 7 impactos (máximo).
- Si el chaleco se conserva al avanzar de ronda y aún no es Nv.3, aparece un objeto de mejora.
- Si se destruye, puede reaparecer un chaleco base en una ronda posterior.
- Botón ⚙ Configuración disponible dentro de Town, Bosque Invernal y Medio Oeste.
- Sensibilidad: 10% a 100%. La sensibilidad original equivale a 25% y es el valor predeterminado.
- Dificultad manual: 100% a 200% en pasos de 25%. Se multiplica sobre la dificultad propia de la ronda.
- La configuración se guarda en localStorage y se comparte entre los tres mundos.


ACTUALIZACIÓN XBOX Y VIDA
------------------------
Xbox: L3 = sprint, LB/RB = arma anterior/siguiente, X = recargar, RT = disparar, LT = apuntar, A = saltar, B = agacharse.
Jugador: 100 puntos de vida con barra HUD. El chaleco absorbe proyectiles antes de descontar vida.
Enemigos normales: 3 HP con barra de vida sobre el personaje. Francotirador causa 3 de daño, espada y revólver 2, pistola/metralleta 1.
Jefes: conservan su vida especial y muestran una barra grande en el HUD.

BALANCE ACTUALIZADO:
- Teclado PC: C mantiene la postura agachada; Shift conserva el sprint.
- Enemigos normales: 2 HP y menor daño de contacto.
- Cantidad aproximada de enemigos reducida 50%: 2 iniciales, máximo base 7 y 3 derrotas para completar una ronda.
- Desde ronda 4 aparece una segunda variante élite por mapa, con más vida y velocidad.
- Jefes: mayor velocidad, ataques más frecuentes y mayor daño.
- Medio Oeste: el jefe a caballo ahora puede lanzar un lazo, enganchar al jugador y arrastrarlo hacia el caballo.


INSPECCION Y BOOST DE JEFE
---------------------------
- PC: tecla F inspecciona el arma equipada.
- Android: botón "Inspeccionar" dentro de los controles táctiles.
- Xbox: D-Pad arriba inspecciona el arma. El mismo botón queda preparado para los futuros esquemas PlayStation/Nintendo.
- Todas las armas tienen una animación de inspección propia por tipo (arma corta, rifle/metralleta o espada).
- Mientras se inspecciona no se puede disparar, recargar ni cambiar de arma, evitando conflictos de animación.
- En la ronda del jefe de cada mundo aparece un boost luminoso de doble salto.
- El doble salto solo se activa si recoges el boost y dura hasta terminar esa pelea contra el jefe.

BARRIDA, RETROCESO Y VIEWMODELS
-------------------------------
- Teclado PC: mientras corres hacia delante con W + Shift, pulsa C para barrerte durante 1 segundo.
- La barrida baja la cámara, impulsa al jugador hacia delante y tiene animación propia del viewmodel.
- Android/Xbox reutilizan la misma lógica: sprint + agacharse mientras avanzas puede iniciar la barrida.
- Las armas tienen retroceso visual distinto según su potencia: metralleta bajo por disparo, pistola medio, revólver alto y francotirador muy alto.
- Los modelos de arma se simplificaron a un diseño intermedio: más claros que los originales, pero sin exceso de detalles.

AUDIO ACTUALIZADO
-----------------
- Los disparos principales usan grabaciones CC0 de armas de fuego reales mediante URLs de la biblioteca FPS Asset Kit / Free Firearm Sound Library.
- Pistola: 1911.
- Francotirador: Savage 10 .300 Blackout.
- Metralleta: PPSh.
- Revólver: Smith & Wesson 642.
- Escopeta: Mossberg.
- Si el navegador no puede cargar una grabación remota, Defusual conserva WAV locales de respaldo para no quedarse sin sonido.
- Equipar arma usa un efecto mecánico propio (no copia audio de TF2).
- Daño usa un efecto húmedo/sangre propio más orgánico.
- Recargas, inserción de cartuchos y pump-action usan WAV locales de mayor fidelidad.
- La música de menú, pausa y jefe y parte del ambiente siguen generándose con Web Audio API.
- El retroceso de cámara/viewmodel está desactivado para mantener una vista estable.


MUNDO 4 — ZOMBILAND
- Ciudad infectada con ambiente apocalíptico.
- Arsenal exclusivo: Escopeta, Metralleta, Francotirador, RPG y Cuchillo.
- R1 infectados comunes: sus mordidas aplican sangrado temporal.
- R2: 4 Spitters con proyectiles y charcos de ácido.
- R3: 4 Hunters con saltos altos y derribo.
- R4: 4 Smokers con lengua que arrastra al jugador.
- R5: 6 parásitos que se adhieren temporalmente y drenan vida.
- R6: 5 Chargers con brazo gigante y embestida.
- R7: oleada mixta con todos los infectados anteriores al mismo tiempo.
- R8: Tank, jefe de mucha vida; es rápido, golpea por 17 HP y lanza al jugador varios metros.
- El Tank arranca escombros del suelo y los arroja como proyectiles, además de llamar infectados comunes.
- En la ronda del Tank aparece el boost de doble salto.

ZOMBILAND - MUNDO 4
-------------------
- Ronda 1: infectados comunes con sangrado temporal.
- Ronda 2: 4 Spitters con ácido.
- Ronda 3: 4 Hunters con saltos y derribo.
- Ronda 4: 4 Smokers con lengua que arrastra al jugador.
- Ronda 5: 6 parásitos que se adhieren y drenan vida.
- Ronda 6: 5 Chargers con embestida.
- Ronda 7: oleada mixta con todos los infectados anteriores.
- Ronda 8: jefe final Tank, infectado gigante con 80 HP, velocidad alta, puñetazos de 17 HP, empuje de varios metros, lanzamiento de escombros y capacidad de invocar infectados comunes.
- Arsenal exclusivo de Zombiland: Escopeta pump-action, Metralleta, Francotirador, RPG y Cuchillo.
- RPG: proyectil físico, explosión de área, 1 cohete cargado y reserva limitada.
- Todas las armas usan las animaciones estables de equipar, desequipar, caminar, sprint, agacharse, barrerse, saltar, inspeccionar, disparar/atacar y recargar cuando aplica.

ZOMBILAND - actualización de hordas y movilidad
- Rondas 1-7 aumentadas aproximadamente x2.7: 8, 11, 11, 11, 16, 14 y 27 infectados totales.
- Las hordas grandes aparecen por oleadas internas para mantener rendimiento; máximo aproximado de 12 infectados normales simultáneos.
- Mapa cerrado con muro físico perimetral.
- Infectados más rápidos, con menor tiempo de reacción y desvío lateral básico cuando encuentran obstáculos.
- Tank R8 más rápido que la velocidad normal del jugador, mantiene puñetazo de 17 HP, escombros e invocación de infectados.
- Cuchillo: clic derecho ejecuta backstab instantáneo sobre infectados normales/especiales a corta distancia (no mata al Tank instantáneamente).
- RPG: explosión visual ampliada con onda expansiva y partículas.
- Rocket jump: en el aire, mantén C y dispara el RPG al suelo cerca de ti; la explosión causa 10 HP de daño propio e impulsa al jugador vertical y horizontalmente.
- En la pelea del Tank, el boost de salto ahora también activa gravedad reducida y salto más alto, conservando doble salto.
