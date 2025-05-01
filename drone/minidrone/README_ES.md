# Minidrone Parrot

![Parrot Minidrone](../../images/minidrone.jpg)

El minidrone Parrot usa una interfaz Bluetooth que se puede programar con una API.

Puedes usar [TinyGo Bluetooth](https://tinygo.org/bluetooth) para controlar el drone desde tu ordenador.

## Qué necesitas

    - Minidrone Parrot
    - Un ordenador con Go 1.24+ instalado
    - Funciona en Linux, macOS or Windows

¿Tienes un Badger20400-W? Entonces también puedes controlar el drone con el firmware "Flightbadge"! Mira en la carpeta de tutoriales para encontrarlo.

## Instalación

Esta actividad usa el paquete TinyGo Bluetooth http://tinygo.org/bluetooth

También utiliza el paquete https://github.com/hybridgroup/tinygo-minidrone que contiene los wrappers para la interfaz Bluetooth del drone.

Cambia los directorios a este directorio donde se encuentran los archivos de módulos Go necesarios, y se instalarán todas las dependencias.

## Ejecutando el código

Cuando ejecutes cualquiera de estos ejemplos, compilarás y ejecutarás el código en tu ordenador. Cuando estés ejecutando el programa, te estarás comunicando con el minidrone utilizando la interfaz Bluetooth.

En Linux y Windows utilizarás la dirección MAC del dispositivo para conectarte.

En macOS deberá utilizar el ID Bluetooth del dispositivo para conectarse.

Por lo tanto, debes conocer el nombre correcto y luego la dirección MAC o ID de ese dispositivo para poder conectarte a él.

El nombre del dron debe aparecer en el lateral del mismo.

Para averiguar la dirección MAC única o el ID Bluetooth de un dispositivo, puedes utilizar el escáner Bluetooth que se encuentra en el directorio de herramientas de esta repo.

Primero, cambia el directorio actual al directorio `tools`:

```shell
cd tools
```

A continuación, ejecuta el comando del escáner de Bluetooth:

```shell
go run ./blescanner
```

## Código

### step01/main.go

Vamos a empezar con un simple despegue, y luego aterrizar. Asegúrate de que el dron está encendido y conoces la dirección MAC o el nombre correctos, luego ejecuta el código con:

```go run ./step1 [MAC address or Bluetooth ID]```

<hr>

### step02/main.go

En este ejemplo el drone planeará y devolverá algunos datos de la información de vuelo. Ejecuta el código con: 

```go run ./step2 [MAC address or Bluetooth ID]```

<hr>

### step03/main.go

El drone puede moverse hacia adelante, hacia atrás, hacia la derecha y la izquierda, todo ello manteniendo una altitud constante. Ejecuta el código con: 

```go run ./step3 [MAC address or Bluetooth ID]```

<hr>

### step04/main.go

El dron también puede moverse hacia arriba y hacia abajo, y puede girar a la izquierda y a la derecha. Ejecuta el código con: 

```go run ./step4 [MAC address or Bluetooth ID]```

<hr>

### step05/main.go

El dron puede realizar volteretas mientras vuela. Ejecuta el código con: 

```go run ./step5 [MAC address or Bluetooth ID]```

<hr>

### step06/main.go

Ahora es el momento del vuelo libre, controlado por ti, el piloto humano. Conecta el controlador DS3 a tu ordenador. Los controles son los siguientes:

* Triángulo       - Despegue
* X               - Aterrizaje
* Stick izquierdo - Altitud
* Stick derecho   - Dirección
* L1              - Voltereta hacia delante
* R1              - Voltereta hacia atrás



NOTA IMPORTANTE: debes pulsar el botón «P3» cuando tu programa se ejecute por primera vez para que los joysticks DS3 «clónicos» que estamos utilizando se enciendan completamente.

**macOS**

`go run ./step6 [Bluetooth ID]`

**Linux**

`go run step6 [MAC address]`

**Windows**:

`go run ./step6 [MAC address]`

<hr>

<hr>

### keyboard/main.go

¡Controla el minidrone con el teclado!

- [, ] control de despegue y aterrizaje
- w, s, a, d controlan el movimiento hacia delante, hacia atrás, hacia la izquierda y hacia la derecha.
- i, k, j, l controlan el movimiento hacia arriba, hacia abajo, girar en sentido contrario a las agujas del reloj y en sentido de las agujas del reloj
- t, g, f, h controlan el giro hacia delante, hacia atrás, hacia la izquierda y hacia la derecha
- r detiene todo movimiento en el minidrone para permitirle simplemente flotar.

