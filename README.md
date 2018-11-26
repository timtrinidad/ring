# homebridge-ring-alarm
 
[![CircleCI](https://circleci.com/gh/dgreif/homebridge-ring-alarm.svg?style=svg)](https://circleci.com/gh/dgreif/homebridge-ring-alarm)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=HD9ZPB34FY428&currency_code=USD&source=url)
 
This [Homebridge](https://github.com/nfarina/homebridge) plugin provides a platform for the
 [Ring Alarm System](https://shop.ring.com/pages/security-system)
 
 ### Installation
 
 Assuming a global installation of `homebridge`:
 
 `npm i -g homebridge-ring-alarm`
 
 ### Homebridge Configuration
 
 Add the `RingAlarm` platform in your homebridge `config.json` file.  The platform options are passed directly into 
 [ring-api](https://github.com/jimhigson/ring-api) (with `poll` set to `false` since it's not needed
 for alarms)
 
 ```json
{
  "platforms": [
    {
      "platform": "RingAlarm",
      "email": "some.one@website.com",
      "password": "abc123!#"
    }
  ]
}
```

### Supported Devices
  * Security Panel
    * This is a software device that represents the alarm for a Ring location
    * Arm Home / Arm Away / Disarm alarm for Ring location.
    
    * Detect active burglar alarm
  * Base Station
    * Set Volume (Not currently supported in Home, but works in other apps like Eve)
    * Battery status
  * Keypad
    * Set Volume (Not currently supported in Home, but works in other apps like Eve)
    * Battery status
  * Contact Sensor
    * Detect if sensor is open or closed
    * Tamper status
    * Battery status
  * Motion Sensor
    * Detect motion
    * Tamper status
    * Battery status

### Alarm Modes

Ring Mode | HomeKit Mode
--- | ---
Disarmed | Off
Home | Home
Away | Away
Home | Night

Entry delays and bypassed sensors (ex. for Home mode) are all controlled in the Ring app.
These settings will automatically be used by HomeKit.

**Note**: Using `Night` mode in HomeKit will activate `Home` mode on the Ring alarm.
HomeKit should immediately switch to `Home` to match.  
