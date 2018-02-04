# bruh-sensornode-dp
Enhancements to Bruh Automation's Sensor Node for Home Assistant on a ESP8266

04 Feb 2018 by David Payne - Set LED pins to output to prevent dull blue glow on power up/reset
                           - Allow modal colour and brightness fading from effects in HA
                           - add -     effect: true
                                       effect_list: [colorfade_slow, colorfade_fast, flash, none]
                                to mqtt_json light
                           - Send modal states back in sendstate
                           - fix heat index for Celsius (hardcoded as C)
                           - Change PIR to binary_sensor to allow nice icon
                                 binary_sensor:
                                   - platform: mqtt
                                     state_topic: "bruh/sensornode1"
                                     name: "SN1 PIR"
                                     value_template: '{{ value_json.motion }}'
                                     payload_on: "motion detected"
                                     payload_off: "standby"
                                     device_class: motion
