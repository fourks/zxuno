# JOY2PS2

* Versión alternativa propuesta por Antonio Villena.

Código C para microcontroladores Atmega168/328 que permite mapear a scancodes de teclado PS/2 desde varios tipos de joysticks.

Por defecto, se encuentra configurado para poder utilizar el conector DB15, o bien el conector principal DB9. Esta configuración se puede cambiar en caliente mediante una combinación especial, de manera que se habilitaría el conector auxiliar DB9 y deshabilitaria el conector DB15. Esto es útil cuando se necesita jugar a dos jugadores con el mismo addon.

El conector DB15 admite por ahora los siguientes gamepads:

-> Neogeo Oldstyle

Los conectores db9 admiten por ahora los siguientes gamepads:

-> Atari DB9 1 o 2 botones
-> Megadrive de 3 o 6 botones, con botones Start y Select (Mode)
-> NES clonico, version de Antonio adaptado a Atari DB9

CONTROLES
---------

Desde el gamepad principal se puede controlar el ZXUno, así como todo tipo de menús. Al comienzo, éste siempre se encuentra mapeados en modo cursores, primer boton Enter y segundo Escape (modo menú tradicional).

En cualquier momento podremos pasar a un estado especial, al que llamaremos SHIFT. Para acceder a este estado, se puede hacer de cualquiera de las siguientes formas:

1. Pulsando Start + Boton 1
2. Pulsado Select + Start.
3. Pulsando y soltando la tecla Keymapper.

Una vez en el modo SHIFT, parecerá que no funciona ningún boton, pero no es asi. A partir de ahora se puede tomar la siguiente acción, que se llevará a cabo al pulsar el boton 1 del gamepad como evento final (para cancelar, volver a pulsar la combinacion de SHIFT, o bien pulsar el boton 2 del gamepad):

Nota: Las combinaciones abajo expuestas son pulsando y soltando (no mantener botones pulsados), cualquier cambio de direccion resetea el contador de las otras:

Sólo boton 1: Cambio de cursores a OPQA y viceversa en el joystick 1 (el principal)
Sólo boton 2: Cancelar modo SHIFT (también se puede cancelar volviendo a pulsar la combinación de SHIFT)

Opciones ABAJO
--------------

* 1 vez abajo y luego boton 1: NMI
* 2 veces abajo y luego boton 1: Reset (Se cambia automaticamente a cursores)
* 3 veces abajo y luego boton 1: MasterReset (Se cambia automaticamente a cursores)
* 4 veces abajo y luego boton 1: MasterReset y entrada a ROMs (Se cambia automaticamente a cursores)
* 5 veces abajo y luego boton 1: MasterReset y entrada a cores (Se cambia automaticamente a cursores)
* 6 veces abajo y luego boton 1: MasterReset y entrada a BIOS (Se cambia automaticamente a cursores)
* 7 veces y siguientes... se mantiene en la opcion de las 6 veces.

Opciones ARRIBA
---------------

* 1 vez arriba y luego boton 1: tecla '1'
* 2 veces arriba y luego boton 1: tecla '2'
* ...
* 9 veces arriba y luego boton 1: tecla '9'
* 10 veces arriba y luego boton 1: tecla '0'
* ... siguientes, se mantiene en la última opción '0'

Opciones DERECHA
----------------

* 1 vez y sucesivas: teclas 'J ""' (load modo 48k)

Opciones IZQUIERDA
------------------

* 1 vez izquierda y luego boton 1: Modo teclado completo (ver abajo)
* 2 veces izquierda y luego boton 1: Escape (necesario si se usa joystick de un solo boton, junto como el boton de keymapper a modo de shift)
* 3 veces izquierda y luego boton 1 de jugador 1 o 2: Cambio de mapa del jugador correspondiente. (ver abajo mapas disponibles)
* 4 veces izquierda y luego boton 1: Tecla Extend
* 5 veces izquierda y luego boton 1: Tecla Caps (LCTRL)
* 6 veces izquierda y luego boton 1: Tecla Symbol (RCTRL)
* 7 veces izquierda y luego boton 1: Tecla Graph (RALT)
* 8 veces izquierda y luego boton 1: Tecla TrueVid (F3)
* 9 veces izquierda y luego boton 1: Tecla InvVid (F4)
* 10 veces y siguientes... se mantiene en la opcion 9.

CAMBIO ENTRE DB15/DB9 Y DB9x2
-----------------------------

* Estando en modo SHIFT pulsar el boton 1, y manteniendolo pulsado, pulsar boton 2.

(La configuración seleccionada permanece durante reseteos en caliente de ZXUno)

MODO TECLADO (KEYSTROKES)
-------------------------

* arriba: cambio de tecla hacia adelante e impresion en pantalla.
* abajo: cambio de tecla hacia atras e impresion en pantalla.
* izquierda: borrar tecla.
* derecha: aceptar tecla o espacio.
* boton 1: cambio de tecla a correspodiente con tecla derecha del shift (para imprimir mayusculas o caracteres especiales)
* boton 2: Enter

* Para salir: Entrar al modo SHIFT y elegir otra opción, o salir del modo SHIFT una vez dentro.

MAPAS DE TECLADO
----------------

El cambio de mapa es cíclico, después del último mapa vuelve el mapa 0.

Mapa 0 
------

(Por defecto al iniciar y resetear el ZXUno)

Jugador 1

	KEY_Q,       	// UP
	KEY_A,       	// DOWN
	KEY_O,       	// LEFT
	KEY_P,       	// RIGHT
	KEY_5,	      	// SELECT
	KEY_1,		// START
	KEY_SPACE, 	// BUTTON 1
	KEY_E,       	// BUTTON 2
	KEY_R,       	// BUTTON 3
	KEY_D,       	// BUTTON 4
	KEY_F,       	// BUTTON 5
	KEY_C        	// BUTTON 6

Jugador 2

	KEY_I,       	// UP
	KEY_K,       	// DOWN
	KEY_J,       	// LEFT
	KEY_L,       	// RIGHT
	KEY_6,	    	// SELECT
	KEY_2,		// START
	KEY_H,		// BUTTON 1
	KEY_G,       	// BUTTON 2
	KEY_N,       	// BUTTON 3
	KEY_B,       	// BUTTON 4
	KEY_Y,       	// BUTTON 5
	KEY_T        	// BUTTON 6

Mapa 1
------

Jugador 1

	KEY_W,       	// UP
	KEY_S,       	// DOWN
	KEY_A,       	// LEFT
	KEY_D,       	// RIGHT
	KEY_5,	     	// SELECT
	KEY_1,		// START
	KEY_F,		// BUTTON 1
	KEY_E,       	// BUTTON 2
	KEY_R,       	// BUTTON 3
	KEY_D,       	// BUTTON 4
	KEY_F,       	// BUTTON 5
	KEY_C        	// BUTTON 6

Jugador 2

	KEY_I,       	// UP
	KEY_K,       	// DOWN
	KEY_J,       	// LEFT
	KEY_L,       	// RIGHT
	KEY_6,	    	// SELECT
	KEY_2,		// START
	KEY_H,		// BUTTON 1
	KEY_G,       	// BUTTON 2
	KEY_N,       	// BUTTON 3
	KEY_B,       	// BUTTON 4
	KEY_Y,       	// BUTTON 5
	KEY_T        	// BUTTON 6

Mapa 2
------

(Teclas por defecto de M.A.M.E)

Jugador 1

	KEY_UP,       	// UP
	KEY_DOWN,      	// DOWN
	KEY_LEFT,      	// LEFT
	KEY_RIGHT,     	// RIGHT
	KEY_5,	      	// SELECT
	KEY_1,		// START
	KEY_LCTRL,    	// BUTTON 1
	KEY_LALT,       // BUTTON 2
	KEY_SPACE,      // BUTTON 3
	KEY_LSHIFT,     // BUTTON 4
	KEY_Z,        	// BUTTON 5
	KEY_X         	// BUTTON 6

Jugador 2

	KEY_R,       	// UP
	KEY_F,       	// DOWN
	KEY_D,       	// LEFT
	KEY_G,       	// RIGHT
	KEY_6,	    	// SELECT
	KEY_2,		// START
	KEY_A,		// BUTTON 1
	KEY_S,       	// BUTTON 2
	KEY_Q,       	// BUTTON 3
	KEY_W,       	// BUTTON 4
	KEY_E,       	// BUTTON 5 // Not set by default on MAME
	KEY_T        	// BUTTON 6 // Not set by default on MAME

TO DO LIST
----------

* Soporte de gamepads de tipo Famicom DB9
* Revisar compatibilidad con ordenadores PC con entrada de teclado PS/2. (Ahora no funciona bien)
* Posibilidad de inicialización de teclado. (Puede que sea necesario para PCs)
* Implementación y acceso al set 1 de scancodes. (Necesario para el core de PC/XT del ZXUno)
