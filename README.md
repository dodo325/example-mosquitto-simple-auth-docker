# Running Mosquitto with auth in Docker

Simple example of how to run Mosquitto with auth in Docker. I have used the [official Eclipse Mosquitto MQTT Broker Docker image](https://hub.docker.com/_/eclipse-mosquitto/).

## Usage

Place the Mosquitto credentials to the `.env` file that will be used by the [docker-compose](https://docs.docker.com/compose/).

```bash
MOSQUITTO_USERNAME=mosquitto
MOSQUITTO_PASSWORD=mosquitto
```
### Give access:

```bash
sudo chmod o+w log/mosquitto.log
sudo chmod o+w config/mosquitto.conf
```

### Build and run

```bash
docker-compose up -d --build
```

### Testing

Try the [MQTT client](http://mqttfx.org/) to connect to the Mosquitto MQTT Broker. Use `127.0.0.1:1883` for a local environment.

Or use official `mosquitto_pub` and `mosquitto_sub` utilities for publishing and subscribing.

```bash
# Subscribe to topic.
mosquitto_sub -h localhost -t test -u "mosquitto" -P "mosquitto"

# Publish a message.
mosquitto_pub -h localhost -t test -m "hello." -u "mosquitto" -P "mosquitto"
```
