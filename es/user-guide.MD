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

### 2.1 Abriendo terminales y moviéndose
Una operación muy básica es abrir una nueva terminal. Por defecto, la combinación de teclas para esto es `$mod+Enter`, es decir, Alt+Enter (`Mod1+Enter`) en la configuración predeterminada. Al presionar `$mod+Enter`, se abrirá una nueva terminal. Esta llenará todo el espacio disponible en tu pantalla.

![alt text](../images/single_terminal.png)