# TinyGo Music Jam

Haz música con tu propio controlador MIDI personalizado basado en TinyGo mediante un software de audio que se ejecuta en tu ordenador portátil.

```
┌────────────────────────────┐      ┌────────────────────────────────────────────────┐
│                            │      │                                                │
│ ┌────────────────────────┐ │      │ ┌──────────────────────┐                       │
│ │                        │ │      │ │                      │                       │
│ │                        │ │      │ │                      │                       │
│ │     MIDI Controller    │ │      │ │       USB-MIDI       │                       │
│ │                        ├─┼──────┼─►                      │                       │
│ │                        │ │      │ │                      │                       │
│ │                        │ │      │ │                      │                       │
│ │                        │ │      │ │                      │                       │
│ │                        │ │      │ │                      │                       │
│ └────────────────────────┘ │      │ └──────────┬───────────┘                       │
│                            │      │            │                                   │
│                            │      │            │                                   │
│                            │      │            │                                   │
│                            │      │            │                                   │
│                            │      │            │                                   │
│                            │      │ ┌──────────▼───────────┐                       │
│                            │      │ │                      ├─────────────────────┐ │
│                            │      │ │                      │                     │ │
│                            │      │ │     Web MIDI API     │ Web Software Synth  │ │
│                            │      │ │                      │                     │ │
│                            │      │ │                      ├─────────────────────┘ │
│                            │      │ │                      │                       │
│                            │      │ │                      │                       │
│                            │      │ │                      │                       │
│                            │      │ └──────────────────────┘                       │
│                            │      │                                                │
└────────────────────────────┘      └────────────────────────────────────────────────┘

  Arduino/Badger2040                  Computer

```

Gracias al estándar USB-MIDI, el Arduino aparecerá como un controlador MIDI estándar. Puedes utilizarlo para conectarte a instrumentos en línea que utilicen la API Web MIDI.



## Sintetizadores e instrumentos en línea

Esta es sólo una lista de algunos de los sintetizadores y otros instrumentos virtuales disponibles en línea:


https://midi.city/

https://www.websynths.com/microtonal/

https://www.gsn-lib.org/apps/cardboardsynth/index.html

https://g200kg.github.io/webaudio-tinysynth/soundedit.html

https://signal.vercel.app/

https://juno-106.js.org/

https://virtualpiano.eu/

https://experiments.withgoogle.com/ai/sound-maker/view/

## Controladores hardware

Un controlador MIDI de hardware te permite controlar los instrumentos virtuales que se ejecutan en tu ordenador.

Cada uno de los programas TinyGo para el controlador MIDI está pensado para ejecutarse directamente en el hardware externo para enviar comandos MIDI a través de la interfaz USB a tu ordenador.

Las actividades musicales se pueden realizar tanto con el Arduino RP2040 Nano como con el Badger2040.

### Arduino RP2040 Nano

Puedes utilizar una placa Arduino RP2040 junto con uno de los kits de botones que hemos traído.

Para seguir las actividades MIDI utilizando el Arduino RP2040 Nano, [haz clic aquí](./arduino.md)

### Badger2040

Si tienes un Badger2040 puedes usarlo como tu controlador MIDI. Consulta con nosotros algunos accesorios que necesitarás.

Para seguir las actividades MIDI utilizando el Badger2040, [haz clic aquí](https://github.com/conejoninja/badger2040/tree/main/tutorial/musicjam)
