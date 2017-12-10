# volumio-mqtt
NodeJS MQTT adapter for volumio.org music player, to control your player using MQTT messages.

For example, if you have configured your mqtt_devicename in config.js to "player-01", you can control it by sending MQTT messages to topic "player-01/set/play" to start playback, or "player-01/set/volume/percent" and a payload of 50 to set volume to 50%.

# Configuration
Copy config.js.sample to config.js and adjust your settings:
Define mqtt_devicename (the prefix for mqtt messages) and mqttHost with the address of your mqtt broker.

config.js is listed in the .gitignore list and will not be overwritten when you pull from the git repository. 

# Install PM" process manager
Optional: You can use PM2 to run this script automatically on each reboot

$ sudo npm install pm2 -g
$ sudo pm2 startup
$ pm2 start pm2-process.json
$ pm2 list 
$ pm2 save

# MQTT Topics:

Setters:

- {devicename}/set/volume/percent       0 - 100
- {devicename}/set/volume/mute          true | false
- {devicename}/set/volume/push          + | -

- {devicename}/set/play
- {devicename}/set/stop
- {devicename}/set/pause

Getters: 

- {devicename}/get/status
- {devicename}/get/browsesources
- {devicename}/get/browselibrary
- {devicename}/get/multiroomdevices

Status responses:

- {devicename}/status/connected         true | false
- {devicename}/status/info
- {devicename}/status/browsesources
- {devicename}/status/browselibrary
- {devicename}/status/multiroomdevices


Volumio player API reference
https://volumio.github.io/docs/API/WebSocket_APIs.html
