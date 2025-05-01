# MIDI Music Jam using the Arduino RP2040 Nano

## Qué necesitas

    - Arduino Nano RP2040 Connect IoT
    - Kit MIDI Starter
    - Ordenador con Go 1.24+ and TinyGo instalados, un puerto USB

### Controladores TinyGo

Todas las dependencias de código que necesitarás ya están en el archivo de módulos Go en este directorio, por lo que se descargarán e instalarán automáticamente. No necesitas hacer nada, cuando sigas las siguientes instrucciones serán descargados por TinyGo.

Sólo para tu información, los drivers de TinyGo que te permiten conectarte a sensores, pantallas y otros dispositivos periféricos externos se encuentran en el repositorio separado en https://github.com/tinygo-org/drivers.


## Conectando el Arduino Nano RP2040 Conéctalo a tu ordenador

<img src="https://docs.arduino.cc/static/8b9e4e17c1e1afa836057c5ba87c27c9/2f891/pinout.png" alt="Arduino Nano RP2040 Connect" width="600"/>


Conecta el Arduino Nano RP2040 Connect a tu ordenador mediante un cable USB. (Puede que haya un en el kit proporcionado)

## Ejecutar el código

Los programas TinyGo se ejecutarán directamente en el microcontrolador Arduino. El procedimiento es básicamente

- Edita tu programa TinyGo.
- Compílalo y flashéalo en tu Arduino.
- El programa se ejecuta desde el Arduino.


¡Empecemos!

## Código

### hola - LED incorporado

Arduino Nano RP2040 Connect](./assets/step0.jpg)

Esto prueba que puedes compilar y flashear tu Arduino con código TinyGo, haciendo parpadear el LED incorporado.

Ejecuta el siguiente comando para compilar tu código, y flashearlo en el Arduino:

```
tinygo flash -target nano-rp2040 ./hello/
```

Una vez que el Arduino está flasheado correctamente, el LED ámbar incorporado a la derecha de la toma USB debería empezar a encenderse y apagarse una vez por segundo. Ahora todo está configurado correctamente y ya está listo para continuar.

### onenote

Crearemos un sencillo controlador MIDI que envie una única nota.

- Conecta uno de los pines de tierra del Arduino a la toma de tierra de la protoboard (-).

- Conecta un cable negro desde uno de los pines del botón azul de la protoboard al raíl de tierra de la protoboard (-).

- Conecta un cable de color desde la otra patilla del botón azul de la protoboard a la patilla D12 del Arduino.

Para compilar y flashear el ejemplo `onenote` en el Arduino Nano RP2040:

        tinygo flash -target nano-rp2040 ./onenote/

Pulsa el botón.

Esto debería enviar mensajes MIDI desde el Arduino a tu ordenador por el cable USB.

Abre una página web con uno de los sintetizadores en línea mencionados anteriormente. Deberías ser capaz de utilizar tu nuevo controlador MIDI personalizado para hacer música.

¡Diviértete!

### chorder

Este controlador MIDI envía acordes enteros con un solo toque. Utiliza exactamente la misma configuración de cableado que el programa `onenote`.

Cada vez que pulses el controlador, tocará el siguiente acorde de la progresión de acordes programada.

Para compilar y flashear el programa `chorder` en Arduino Nano RP2040:

        tinygo flash -target nano-rp2040 ./chorder/

Inicie uno de los sintetizadores en línea. Deberías poder utilizar tu nuevo controlador MIDI personalizado para hacer música.

Diviértete.

### fourkeys

Este controlador MIDI envía cuatro notas diferentes.

- Conecta un cable negro desde una patilla del botón verde de la protoboard a la barra de masa de la protoboard (-).

- Conecta un cable de color desde la otra patilla del botón verde de la protoboard a la patilla D11 del Arduino.

- Conecta un cable negro desde una patilla del botón rojo de la protoboard a la toma de tierra de la protoboard (-).

- Conecta un cable de color desde la otra patilla del botón rojo de la protoboard a la patilla D10 del Arduino.

- Conecta un cable negro desde una de las patillas del botón amarillo de la protoboard a la toma de tierra de la protoboard (-).

- Conecta un cable de color desde la otra patilla del botón amarillo de la protoboard a la patilla D9 del Arduino.

Para compilar y flashear el programa `fourkey` en el Arduino Nano RP2040:

        tinygo flash -target nano-rp2040 ./fourkey/
