# owserver

The app provides owserver enabling access to 1-Wire sensors over serial, i2c, usb, w1, pbm, ha7net fake devices.

## Configuration

**Note**: _Remember to restart the app whenever configuration change._

Example app configurations:

```yaml
devices:
  - device_type: serial
    device: /dev/ttyUSB0
owhttpd: true
temperature_scale: Celsius
debug: false
```

```yaml
devices:
  - device_type: ha7net
    ha7net_server: 192.168.50.1
  - device_type: ha7net
    ha7net_server: 192.168.50.2
owhttpd: true
temperature_scale: Celsius
debug: false
```
**Note**, these are just example configurations, don't copy, please create your own.


### Option: `owhttpd`

Enable to start the embedded owhttpd server _(Default true)_.
owhttpd server is exposed via **Ingress (Open Web UI)**

### Option: `device`

Specify owserver device, if using the "serial_or_i2c" type.

### Option: `device_type`

Specify owserver device_type from the options below:
- serial_or_i2c device
- usb device
- ha7net device
- w1 device (direct access via GPIO on RasPi)
- fake device (random simulated device)

Specify "/dev/null" as device, if using usb/ha7net/w1/fake type.

### Option: `temperature_scale`

Specify temperature scale used by owserver from the options below:
- Celsius _default_
- Fahrenheit 
- Kelvin 
- Rankine 

### Option: `ha7net_server`

Specify ha7net server. Use it with ha7net device only.

### Option: `debug`

Specify debug mode for owserver.


## Home Assistant integration

1. Configure and start app. With default configuration app starts with fake (mocked) devices.
1. Add to Home Assistant through the Integrations. Go to Integrations, Add Integration, Choose 1-Wire
    - Host: `provide app's hostname (from app details page)`
    - Port: `4304` _(default)_
1. ... or use Home Asistant auto discovery (since 2025.2.0). Go to Integrations, find discovered app and Add it.
1. That's it. On the integrations page wou will find 1-Wire integration with 1-Wire devices.