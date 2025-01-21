# TinyGo Music Jam

Make music using your own TinyGo-based customized MIDI controller using audio software running on your notebook computer.

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

Thanks to USB-MIDI standard, the Arduino will appear as a standard MIDI controller. You can use it to connect to online instruments that use the Web MIDI API.


## Online Synths and Instruments

This is just a list of a few of the available online synths and other virtual instruments.

https://midi.city/

https://www.websynths.com/microtonal/

https://www.gsn-lib.org/apps/cardboardsynth/index.html

https://g200kg.github.io/webaudio-tinysynth/soundedit.html

https://signal.vercel.app/

https://juno-106.js.org/

https://virtualpiano.eu/

https://experiments.withgoogle.com/ai/sound-maker/view/

## Hardware Controllers

A hardware MIDI controller lets you control the virtual instruments running on your computer.

Each of the TinyGo programs for the MIDI Controller is intended to run directly on the external hardware to send MIDI commands via the USB interface to your computer.

The musical activities can be done with either the Arduino RP2040 Nano or Badger2040.

### Arduino RP2040 Nano

You can use a Arduino RP2040 board along with one of the button kits that we have brought with us.

To follow the MIDI activities using the Arduino RP2040 Nano, [click here](./arduino.md)

### Badger2040

If you have a Badger2040 you can use it as your MIDI controller. Check with us for some accessories you will need.

To follow the MIDI activities using the Badger2040, [click here](https://github.com/conejoninja/badger2040/tree/main/tutorial/musicjam)
