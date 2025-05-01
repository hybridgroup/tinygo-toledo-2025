# Tutorial sensores y Arduino

## Qué necesitas

    - Arduino Nano RP2040 Connect IoT
    - Kit Grove Starter
    - Ordenador con Go 1.24+ and TinyGo instalados, un puerto USB

### Controladores TinyGo

Todas las dependencias de código que necesitarás ya están en el archivo de módulos Go en este directorio, por lo que se descargarán e instalarán automáticamente. No necesitas hacer nada, cuando sigas las siguientes instrucciones serán descargados por TinyGo.

Sólo para tu información, los drivers de TinyGo que te permiten conectarte a sensores, pantallas y otros dispositivos periféricos externos se encuentran en el repositorio separado en https://github.com/tinygo-org/drivers.


## Conectando el Arduino Nano RP2040 Conéctalo a tu ordenador

<img src="./assets/nano-rp2040-connect-pins.png" alt="Arduino Nano RP2040 Connect" width="500"/>

Conecta el Arduino Nano RP2040 Connect a tu ordenador mediante un cable USB. (Puede que haya un en el kit proporcionado)

## Ejecutar el código

Los programas TinyGo se ejecutarán directamente en el microcontrolador Arduino. El procedimiento es básicamente

- Edita tu programa TinyGo.
- Compílalo y flashéalo en tu Arduino.
- El programa se ejecuta desde el Arduino.


¡Empecemos!

## Código

### hola - LED incorporado

![Arduino Nano RP2040 Connect](./assets/step0.jpg)

Esto prueba que puedes compilar y flashear tu Arduino con código TinyGo, haciendo parpadear el LED incorporado.

Ejecuta el siguiente comando para compilar tu código, y flashearlo en el Arduino:

```
tinygo flash -target nano-rp2040 ./step0/
```

Una vez que el Arduino está flasheado correctamente, el LED ámbar incorporado a la derecha de la toma USB debería empezar a encenderse y apagarse una vez por segundo. Ahora todo está configurado correctamente y ya está listo para continuar.


### step1.go - LED verda

![Arduino Nano RP2040 Connect](./assets/step1.jpg)


Ahora vamos a hacer lo mismo, pero en lugar de utilizar el LED incorporado vamos a utilizar un LED independiente que vamos a conectar desde el kit de piezas.

- Conecta uno de los pines «Ground» del Arduino a la toma de tierra (-) de la protoboard usando un cable puente negro o marrón.

- Conecta el pin «3.3V» del Arduino a la barra de alimentación de la protoboard (+) utilizando un cable puente rojo.

- Enchufa el LED verde Grove en el cable suministrado con el conector Grove en un extremo y los puentes macho en el otro. Asegúrate de que el LED está conectado a la placa Grove.

- Conecta el extremo negro macho del cable Grove a la toma de tierra (-) de la protoboard.

- Conecta el extremo macho rojo del cable Grove al carril de alimentación de la protoboard (+).

- Conecta el extremo macho amarillo del cable Grove al pin D12 del Arduino.


Ejecuta el código con:

```
tinygo flash -target nano-rp2040 ./step1/
```


Deberías ver parpadear el LED verde.


### step2.go - LED Verde, botón

![Arduino](./assets/step2.jpg)

A continuación, vamos a adjuntar un botón pulsador. El botón controlará el LED que añadimos en el paso anterior. Cuando pulses el botón, el LED se encenderá. Cuando sueltes el botón, se apagará.

- Enchufa el pulsador Grove a un cable suministrado con el conector Grove en un extremo y los puentes macho en el otro.

- Conecta el extremo negro macho del cable Grove a la toma de tierra de la protoboard (-).

- Conecta el extremo macho rojo del cable Grove al carril de alimentación de la protoboard (+).

- Conecta el extremo macho amarillo del cable Grove al pin D11 del Arduino.


Ejecuta el código con: 

```
tinygo flash -target nano-rp2040 ./step2/
```

Al pulsar el botón, el LED verde debería encenderse.


### step3.go - LED verde, botón, LED rojo

![Arduino](./assets/step3.jpg)

Ahora añadiremos un segundo LED, que también controlaremos con el mismo pulsador. Un LED se encenderá cuando pulsemos el botón, y el otro se encenderá cuando soltemos el botón.

- Conecta el LED rojo del Grove a uno de los cables suministrados con el conector Grove en un extremo, y los puentes macho en el otro.

- Conecta el extremo negro macho del cable Grove al conjunto de pines superior izquierdo (-) de la protoboard.

- Conecta el extremo macho rojo del cable Grove al conjunto de patillas superior derecho (+) de la protoboard.

- Conecta el extremo macho amarillo del cable Grove al pin D10 del Arduino.

Ejecuta el código con: 

```
tinygo flash -target nano-rp2040 ./step3/
```

El LED rojo debería encenderse. Cuando pulses el botón, se encenderá el LED verde y se apagará el LED rojo. Cuando suelte el botón, el LED verde se apagará y el LED rojo se volverá a encender.

### step4.go - LED verde, botón, LED rojo, zumbador, botón táctil

![Arduino](./assets/step4.jpg)

En este paso vamos a añadir dos nuevos dispositivos. El primero es un sensor táctil capacitivo. Esencialmente actúa como un botón, pero sólo tienes que tocarlo para activarlo. El segundo es un pequeño zumbador piezoeléctrico. Cuando se envía corriente al zumbador, éste emite un ruido.

- Conecta el sensor táctil Grove a uno de los cables incluidos, con el conector Grove en un extremo y pines macho en el otro.

- Conecta el cable negro al pin en la esquina superior izquierda de la protoboard (-).

- Conecta el cable rojo al pin en la esquina superior derecha de la protoboard (+).

- Conecta el amarillo al pin D9 del Arduino.

- Conecta el zumbador Grove a uno de los cables incluidos, con el conector Grove en un extremo y pines macho en el otro.

- Conecta el cable negro al pin en la esquina superior izquierda de la protoboard (-).

- Conecta el cable rojo al pin en la esquina superior derecha de la protoboard (+).

- Conecta el amarillo al pin D8 del Arduino.

Ejecuta el código con: 

```
tinygo flash -target nano-rp2040 ./step4/
```

Al tocar el sensor táctil, el zumbador debería emitir un sonido.


### step5.go - LED verde, botón, LED rojo, zumbador, sensor táctil, dial

![Arduino](./assets/step5.jpg)

El siguiente dispositivo que añadiremos es un dial giratorio (o potenciómetro). El dial giratorio es un dispositivo analógico. La cantidad de voltaje que puede pasar a través de él depende de cuánto se gire el dial.

Para leer el voltaje que pasa por el dial, necesitaremos un [Conversor analógico a digital (ADC)](https://en.wikipedia.org/wiki/Analog-to-digital_converter). El Arduino Nano RP 2040 connect tiene varios ADC integrados.

Lo usaremos para controlar el brillo del LED rojo. Para ello, necesitaremos cambiar de una simple señal digital de encendido o apagado a Modulación por Ancho de Pulso (PWM) (https://en.wikipedia.org/wiki/Pulse-width_modulation). Podemos usar PWM para aumentar o disminuir el brillo del LED.

- Conecta el dial (potenciómetro) Grove a uno de los cables incluidos, con el conector Grove en un extremo y pines macho en el otro.

- Conecta el cable negro al pin en la esquina superior izquierda de la protoboard (-).

- Conecta el cable rojo al pin en la esquina superior derecha de la protoboard (+).

- Conecta el amarillo al pin A0 del Arduino.

Ejecuta el código con: 

```
tinygo flash -target nano-rp2040 ./step5/
```

Ajustar el sensor del dial debería controlar el brillo del LED rojo.


### step6.go - LED verda, botón, LED rojo, zumbador, sensor táctil, dial, pantalla OLED

![Arduino](./assets/step6.jpg)

Ahora añadiremos una pantalla OLED SSD1306 para mostrar el estado de los botones y el dial. Controlaremos esta pantalla mediante una [interfaz I2C](https://en.wikipedia.org/wiki/I%C2%B2C).

- Conecta un cable _jumper_ dede el pin "GND" de la placa de la pantalla OLED al pin en la esquina superior izquierda de la protoboard (-).

- Conecta un cable _jumper_ dede el pin "VCC" de la placa de la pantalla OLED al pin en la esquina superior derecha de la protoboard (+).

- Conecta un cable _jumper_ dede el pin "SDA" de la placa de la pantalla OLED al pin A4 del Arduino Nano RP2040.

- Conecta un cable _jumper_ dede el pin "SCL" de la placa de la pantalla OLED al pin A5 del Arduino Nano RP2040.


Disponemos de dos paquetes TinyGo para facilitar el uso de pantallas pequeñas, como la SSD1306 del kit.

El paquete [TinyFont](https://github.com/tinygo-org/tinyfont/) renderiza las fuentes en cualquiera de las pantallas compatibles del repositorio de controladores de TinyGo.

El paquete [TinyDraw](https://github.com/tinygo-org/tinydraw) incluye varias primitivas de dibujo, como círculos, líneas y triángulos, que se pueden usar con cualquiera de las pantallas compatibles.


Ejecuta el código con: 

```
tinygo flash -target nano-rp2040 ./step6/
```

El dial debería mostrar su posición actual en la pantalla OLED. La pantalla OLED también debería tener dos círculos vacíos que se iluminarán al pulsar el botón para encender el LED azul y al pulsar el sensor táctil, respectivamente.


### step7.go - LED verde, botón, LED rojo, zumbador, sensor táctil, dial, MQTT

![Arduino](./assets/step6.jpg)

En este paso nos conectaremos a un servidor de mensajería máquina a máquina mediante el [protocolo MQTT](https://en.wikipedia.org/wiki/MQTT). No se requiere hardware adicional.

Sustituye los valores correctos para tu configuración WiFi en el siguiente comando:

```
tinygo flash -target nano-rp2040 -ldflags="-X main.ssid=TinyGoHackDay -X main.pass=community" ./step7/
```

## Cómo saber si funciona

Instala las herramientas de cliente de `mosquitto` para tu sistema operativo y luego ejecuta:

```
mosquitto_sub -h 'test.mosquitto.org' -t 'tinygohackday'
```

Al ejecutar este comando, deberías ver los mensajes. Estos se envían desde tu equipo a un bróker MQTT proporcionado por la Fundación Eclipse y se ejecuta en un servidor en la nube.
