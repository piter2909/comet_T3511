Home Assistant config for Comet T3511 temperature & humidity sensor
Communication via modbus.

PL to EN translation:

emperatura = temperature
wilgotnosc = humidity
cisnienie = atmospheric pressure (because device shows atmospheric preassure)

This is an example config, edit configuration.yaml and add below lines, modify them to your needs.

Host IP address is default device address (192.168.1.213)
---------------------------------------------------------------------------------
COPY BELOW INTO CONFIGURATION.YAML:
---------------------------------------------------------------------------------
modbus:
  - name: modbus_comet_hub
    type: tcp
    host: 192.168.1.213
    port: 502
    delay: 10
    timeout: 5
    sensors:
      - name: comet_temperatura
        address: 48
        unit_of_measurement: °C
        device_class: temperature
        state_class: measurement
        scale: 0.1
        precision: 1
	input_type: holding
      - name: comet_wilgotnosc
        address: 49
        unit_of_measurement: "%"
        device_class: humidity
        state_class: measurement
        scale: 0.1
        precision: 1
	input_type: holding
      - name: comet_cisnienie
        address: 51
        unit_of_measurement: hPa
        device_class: atmospheric_pressure
        state_class: measurement
        scale: 0.1
        precision: 1
	input_type: holding
