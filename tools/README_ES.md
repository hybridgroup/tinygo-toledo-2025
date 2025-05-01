# Utilidades

## BLE Scanner

Úsalo para escanear dispositivos Bluetooth cercanos.

```
go run ./blescanner/
```

## AP Connect

Sirve para conectar un Arduino con WiFi a un punto de acceso.

```
tinygo flash -target nano-rp2040 -ldflags="-X main.ssid=thessid -X main.pass=thepassword" ./apconnect/
```
