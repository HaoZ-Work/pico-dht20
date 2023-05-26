# pico-dht20

This is a MicroPython library for
[DHT20](http://www.aosong.com/en/products-67.html) temperature and humidity sensor. This fork is modified to have unified API with `dht` library from micropython. 

## Example
```python
from machine import Pin, SoftI2C
from utime import sleep

from dht20 import DHT20


# use sda and scl port on ESP32
i2c0_sda = Pin(21)
i2c0_scl = Pin(22)
i2c0 = SoftI2C(sda=i2c0_sda, scl=i2c0_scl)

dht20 = DHT20(i2c0)
dht.measure()

while True:
    measurements = dht20.measurements
    print(f"Temperature: {dht.temperature()} °C, humidity: {dht.humidity} %RH")
    sleep(1)
