# dht-to-mqtt
An ARM-RaspberryPI dockerized Python application to send DHT11/DHT22 sensor values to an MQTT broker

- Setup a static IP address (optional, strongly suggested) with `nmtui`
- Rasperry PI's I2C interfacing must be enabled (`raspi-config` -> `Interface options` -> `I2C` -> REBOOT)
- Before running, please create a `.env` file in the main folder, looking like:

## Docker sample
```
docker run -name dht-to-mqtt --privileged --restart=unless-stopped --network host -e MQTT_HOSTNAME=nas.home -e MQTT_USERNAME=${MQTT_USERNAME} -e MQTT_PASSWORD=${MQTT_PASSWORD} mistercaste/dht-to-mqtt
```

## Docker compose sample
```
services:
  dht-to-mqtt:
    image: mistercaste/dht-to-mqtt:1.0.1
    container_name: dht-to-mqtt
    network_mode: host
    privileged: true
    restart: always
    environment:
      - MQTT_HOSTNAME=nas.home
      - MQTT_USERNAME=${MQTT_USERNAME}
      - MQTT_PASSWORD=${MQTT_PASSWORD}
```
