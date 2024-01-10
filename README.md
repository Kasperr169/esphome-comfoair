# ComfoAir
Port of ComfoAir protocol to ESPHome.io firmware forked from modified firmware by @nyxnyx 
This fork is created to develop/add sensors such as:
- Time to filter change -> testing
- Filter time reset button -> not done yet
- Additional ComfoCool support is planned in the future. But it needs more work and analysis of the protocol.

Also units of some sensors are corected thru yaml file.

Add to your yaml configuration the definition of `external_components`:
```
external_components:
  - source:
      type: git
      url: https://github.com/kasperr169/esphome-comfoair
    components: [comfoair]
```
and than use it:
```
uart:
  id: uart_bus
  baud_rate: 9600
  tx_pin: TX #or define by yourself
  rx_pin: RX #or define by yourself

comfoair:
  name: "ComfoAir 550"
  uart_id: uart_bus
  fan_supply_air_percentage:
    name: "Fan supply (%)"
  fan_exhaust_air_percentage:
    name: "Fan exhaust (%)"
  fan_speed_supply:
    name: "Supply fan speed"
    unit_of_measurement: "RPM"
  fan_speed_exhaust:
    name: "Exhaust fan speed"
    unit_of_measurement: "RPM"
  is_bypass_valve_open:
    name: "Is bypas open?"
  is_preheating:
    name: "is preheating active?"
  outside_air_temperature:
    name: "Outside temperature"
  supply_air_temperature:
    name: "Supply temperature"
  return_air_temperature:
    name: "Return temperature"
  exhaust_air_temperature:
    name: "Exhaust temperature"
  enthalpy_temperature:
    name: "Enthalpy temperature"
  ewt_temperature:
    name: "EWT temperature "
  reheating_temperature:
    name: "Reheating temperature"
  return_air_level:
    name: "Return level"
  supply_air_level:
    name: "Supply level"
  is_supply_fan_active:
    name: "Is supply fan active?"
  is_filter_full:
    name: "Is filter full?"
  bypass_factor:
    name: "Bypass factor"
  bypass_step:
    name: "Bypass step"
  bypass_correction:
    name: "Bypass correction"
  is_summer_mode:
    name: "Is summer mode?"
  filter_weeks:
    name: "Filter weeks"
    unit_of_measurement: "weeks"
```

The sensor defined here is a full list of sensor - if you remove sensor from yaml it will be not monitored.


For visualization: 

Have a look at simple_thermostat.yaml and https://github.com/nervetattoo/simple-thermostat

Or checkout https://github.com/wichers/lovelace-comfoair and follow the instructions.
