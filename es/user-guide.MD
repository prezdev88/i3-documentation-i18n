# Guía del Usuario de i3
Michael Stapelberg  
michael@i3wm.org

Este documento contiene toda la información que necesitas para configurar y usar el gestor de ventanas i3. Si no es así, puedes [contactarnos](https://i3wm.org/contact/) en [GitHub Discussions](https://github.com/i3/i3/discussions), IRC o la lista de correo.

## 1. Combinaciones de teclas predeterminadas
Para aquellos que prefieren una versión breve, aquí hay una visión general de las combinaciones de teclas predeterminadas (haz clic para ver la imagen en tamaño completo):

### Teclas para usar con $mod (Alt):
![Keys to use with $mod (Alt)](../images/keyboard-layer1.png)

### Teclas para usar con Shift+$mod:
![alt text](../images/keyboard-layer2.png)

Las teclas rojas son los modificadores que necesitas presionar (por defecto), las teclas azules son tu fila de inicio.

Ten en cuenta que, al iniciar i3 sin un archivo de configuración, i3-config-wizard te ofrecerá crear un archivo de configuración en el que las posiciones de las teclas (!) coinciden con lo que ves en la imagen anterior, independientemente del diseño del teclado que estés utilizando. Si prefieres usar un archivo de configuración donde las letras de las teclas coincidan con lo que ves arriba, simplemente rechaza la oferta de i3-config-wizard y basa tu configuración en `/etc/i3/config`.

## 2. Usando i3
A lo largo de esta guía, la palabra clave `$mod` se usará para referirse al modificador configurado. Esta es la tecla Alt (`Mod1`) por defecto, con la tecla Windows (`Mod4`) siendo una alternativa popular que previene en gran medida los conflictos con los atajos definidos por las aplicaciones.

### 2.1. Abriendo terminales y moviéndose
Una operación muy básica es abrir una nueva terminal. Por defecto, la combinación de teclas para esto es `$mod+Enter`, es decir, Alt+Enter (`Mod1+Enter`) en la configuración predeterminada. Al presionar `$mod+Enter`, se abrirá una nueva terminal. Esta llenará todo el espacio disponible en tu pantalla.

![alt text](../images/single_terminal.png)

Si ahora abres otra terminal, i3 la colocará junto a la actual, dividiendo el tamaño de la pantalla a la mitad. Dependiendo de tu monitor, i3 pondrá la ventana creada al lado de la ventana existente (en pantallas anchas) o debajo de la ventana existente (pantallas rotadas).

![alt text](../images/two_terminals.png)

Para mover el foco entre las dos terminales, puedes usar las teclas de flecha. Para mayor comodidad, las flechas también están disponibles directamente en la fila de inicio del teclado debajo de tu mano derecha:

|  |  | 
|--------------|--------------|
| `$mod+j` | izquierda |
| `$mod+k` | abajo |
| `$mod+l` | arriba |
| `$mod+;` | derecha |

Ten en cuenta que esto difiere en una tecla del popular editor de texto `vi`, que fue [desarrollado en un terminal ADM-3A y por lo tanto usa hjkl en lugar de jkl;](https://twitter.com/hillelogram/status/1326600125569961991) — el valor predeterminado de i3 está diseñado para requerir un movimiento mínimo de los dedos, pero algunos usuarios de `vi` cambian su configuración de i3 por consistencia.

En este momento, tu espacio de trabajo está dividido (contiene dos terminales) en una dirección específica (horizontal por defecto). Cada ventana puede dividirse horizontal o verticalmente nuevamente, al igual que el espacio de trabajo. La terminología es "ventana" para un contenedor que contiene una ventana X11 (como un terminal o navegador) y "contenedor dividido" para los contenedores que consisten en una o más ventanas.

Para dividir una ventana verticalmente, presiona `$mod+v` antes de crear la nueva ventana. Para dividirla horizontalmente, presiona `$mod+h`.

### 2.2. Cambiando el diseño del contenedor
Un contenedor dividido puede tener uno de los siguientes diseños:

`splith/splitv`  
Las ventanas se dimensionan de manera que cada ventana obtenga una cantidad igual de espacio en el contenedor. `splith` distribuye las ventanas horizontalmente (las ventanas están una al lado de la otra), `splitv` las distribuye verticalmente (las ventanas están una encima de la otra).

`stacking`  
Solo se muestra la ventana enfocada en el contenedor. Obtienes una lista de ventanas en la parte superior del contenedor.

`tabbed`  
El mismo principio que `stacking`, pero la lista de ventanas en la parte superior es solo una línea que está dividida verticalmente.

Para cambiar de modo, presiona `$mod+e` para splith/splitv (alternará entre ambos), `$mod+s` para stacking y `$mod+w` para tabbed.

![modes](../images/modes.png)

### 2.3. Alternar el modo de pantalla completa para una ventana

Para mostrar una ventana en modo de pantalla completa o salir del modo de pantalla completa, presiona `$mod+f`.

También hay un modo de pantalla completa global en i3 en el cual el cliente abarcará todas las salidas disponibles (el comando es `fullscreen toggle global`).

### 2.4. Abrir otras aplicaciones

Además de abrir aplicaciones desde una terminal, también puedes usar el práctico `dmenu`, que se abre presionando `$mod+d` por defecto. Solo escribe el nombre (o una parte de él) de la aplicación que deseas abrir. La aplicación correspondiente debe estar en tu `$PATH` para que esto funcione.

TODO: configuración es un link  
Además, si tienes aplicaciones que abres muy frecuentemente, puedes crear una combinación de teclas para iniciar la aplicación directamente. Consulta la sección [configuración] para más detalles.

### 2.5. Cerrar ventanas

Si una aplicación no proporciona un mecanismo para cerrar (la mayoría de las aplicaciones proporcionan un menú, la tecla Escape o un atajo como `Control+w` para cerrar), puedes presionar `$mod+Shift+q` para matar una ventana. Para las aplicaciones que soportan el protocolo WM_DELETE, esto cerrará correctamente la aplicación (guardando cualquier modificación o realizando otra limpieza). Si la aplicación no soporta el protocolo WM_DELETE, tu servidor X matará la ventana y el comportamiento dependerá de la aplicación.

### 2.6. Uso de espacios de trabajo

Los espacios de trabajo son una forma fácil de agrupar un conjunto de ventanas. Por defecto, estás en el primer espacio de trabajo, como indica la barra en la parte inferior izquierda. Para cambiar a otro espacio de trabajo, presiona `$mod+num`, donde `num` es el número del espacio de trabajo que deseas usar. Si el espacio de trabajo no existe todavía, se creará.

Un paradigma común es poner el navegador web en un espacio de trabajo, las aplicaciones de comunicación (`mutt`, `irssi`, ...) en otro, y las que usas para trabajar, en un tercero. Por supuesto, no hay necesidad de seguir este enfoque.

Si tienes múltiples pantallas, se creará un espacio de trabajo en cada pantalla al iniciar. Si abres un nuevo espacio de trabajo, estará vinculado a la pantalla en la que lo creaste. Cuando cambies a un espacio de trabajo en otra pantalla, i3 enfocará esa pantalla.

### 2.7. Mover ventanas a espacios de trabajo

Para mover una ventana a otro espacio de trabajo, simplemente presiona `$mod+Shift+num`, donde `num` es (al igual que al cambiar de espacios de trabajo) el número del espacio de trabajo de destino. De manera similar a cambiar de espacios de trabajo, el espacio de trabajo de destino se creará si aún no existe.

### 2.8. Redimensionar

La forma más fácil de redimensionar un contenedor es usando el mouse: agarra el borde y muévelo al tamaño deseado.

TODO: binding_modes, configuración predeterminada=default_config

También puedes usar [binding_modes] para definir un modo de redimensionamiento a través del teclado. Para ver un ejemplo de esto, consulta la configuración predeterminada proporcionada por i3.

### 2.9. Reiniciar i3 en el lugar

Para reiniciar i3 en el lugar (y así entrar en un estado limpio si hay un error, o para actualizar a una versión más reciente de i3), puedes usar `$mod+Shift+r`.

### 2.10. Reiniciar i3 en el lugar

Para salir de i3 de manera limpia sin matar tu servidor X, puedes usar `$mod+Shift+e`. Por defecto, aparecerá un diálogo preguntándote si realmente deseas salir.

### 2.11. Flotante

El modo flotante es el opuesto al modo en mosaico. La posición y el tamaño de una ventana no son gestionados automáticamente por i3, sino manualmente por ti. Usar este modo viola el paradigma de mosaico, pero puede ser útil para algunos casos excepcionales como las ventanas de diálogo "Guardar como" o ventanas de herramientas (GIMP o similar). Esas ventanas usualmente establecen la pista apropiada y se abren en modo flotante por defecto.


TODO: floating_modifier, configuración predeterminada

Puedes alternar el modo flotante para una ventana presionando `$mod+Shift+Space`. Arrastrando la barra de título de la ventana con tu mouse puedes mover la ventana. Agarrando los bordes y moviéndolos puedes redimensionar la ventana. También puedes hacerlo usando el [floating_modifier]. Otra forma de redimensionar ventanas flotantes usando el mouse es hacer clic derecho en la barra de título y arrastrar.

Para redimensionar ventanas flotantes con tu teclado, consulta el modo de combinación de teclas de redimensionamiento proporcionado por la configuración predeterminada de i3.

Las ventanas flotantes siempre están sobre las ventanas en mosaico.
 
TODO:

### 2.12. Mover contenedores en mosaico con el mouse

Desde i3 4.21, es posible arrastrar contenedores en mosaico usando el mouse. El arrastre puede iniciarse arrastrando la barra de título de la ventana o presionando el [floating_modifier] y arrastrando el contenedor mientras mantienes presionado el botón izquierdo del mouse. Consulta la opción [config_tiling_drag] para configurar qué acción desencadena el arrastre en mosaico.

Una vez que se inicia el arrastre y el cursor ha dejado el contenedor original, se crean indicadores de caída según la posición del cursor en relación con el contenedor objetivo. Estos indicadores te ayudan a entender cómo será el diseño del [árbol] resultante después de soltar el botón del mouse.

Las posiciones posibles de caída son:

#### Caída sobre el contenedor
Esto ocurre cuando el mouse está relativamente cerca del centro de un contenedor. Si se suelta el mouse, el resultado es exactamente como si hubieras ejecutado el comando `move container to mark`. Consulta [move_to_mark].

#### Caída como hermano
Esto ocurre cuando el mouse está relativamente cerca del borde de un contenedor. Si se suelta el mouse, el contenedor arrastrado se convertirá en un hermano del contenedor objetivo, colocado a la izquierda/derecha/arriba/abajo según la posición del indicador. Esto puede o no crear una nueva división vertical (v-split) o horizontal (h-split) según el diseño previo del contenedor objetivo. Por ejemplo, si el contenedor objetivo está en una división horizontal (h-split) y sueltas el contenedor arrastrado debajo de él, el nuevo diseño tendrá que ser una división vertical (v-split).

#### Caída al contenedor padre
Esto ocurre cuando el mouse está relativamente cerca del borde de un contenedor (pero aún más cerca del borde en comparación con el caso de hermano) y si ese borde también es el borde del contenedor padre. Por ejemplo, si tres contenedores están en un diseño horizontal, los bordes donde esto puede ocurrir son el borde izquierdo del contenedor izquierdo, el borde derecho del contenedor derecho y todos los bordes inferiores y superiores de los tres contenedores. Si se suelta el mouse, el contenedor primero se deja caer como un hermano del contenedor objetivo, como en el caso anterior, y luego se mueve direccionalmente como con el comando `move left|right|down|up`. Consulta [move_direction].

El color del indicador coincide con la configuración de client.focused. Consulta [client_colors].
