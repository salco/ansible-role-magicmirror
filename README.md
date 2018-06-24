# magicmirror

Ansible role for installing and configuring MagicMirror

## Requirements

### Control Machine Requirements
* Ansible >= 2.2

### Target Host Requirements
These packages are required on the target host and are by default listed in the `magicmirror_apt_packages` variable and there is a task to install them already. They are listed here for completeness, there is no manual installation needed.

* curl
* wget
* git
* build-essential
* unzip
* unclutter
* x11-xserver-utils
* sox
* libsox-fmt-all
* swig3.0
* python-pyaudio
* python3-pyaudio
* libatlas-base-dev

pip modules required. They are listed here for completeness, there is no manual installation needed.
 * pyaudio

## Role Variables

Dependent apt packages that will be installed (default list)

    magicmirror_apt_packages:
        - curl
        - wget
        - git
        - build-essential
        - unzip
        - unclutter
        - x11-xserver-utils
        # alexa related
        - sox
        - libsox-fmt-all
        - swig3.0
        - python-pyaudio
        - python3-pyaudio
        - libatlas-base-dev
        # end alexa related

Audio output device, valid options are -  0: Automatic, 1: Analogue (headphone jack), 2: HDMI

    magicmirror_audio_output_device: 0

Audio capture device

    magicmirror_audio_capture_device: 'hw:1,0'

User account to use pm2 with

    magicmirror_pm2_user: pi

Parent directory to checkout MagicMirror repository

    magicmirror_src_dir: /home/{{ magicmirror_pm2_user }}/src

Minimal nodejs version string

    magicmirror_min_nodejs_version: v5.1.0

Stable branch name for nodejs installer

    magicmirror_nodejs_stable_branch: 9.x

Used internally in role to set whether nodejs needs to be upgraded

    magicmirror_nodejs_upgrade_needed: no

Path to plymouth themes directory for MagicMirror

    magicmirror_plymouth_theme_dir: /usr/share/plymouth/themes/MagicMirror

12 or 24 hr time format

    magicmirror_timeformat: 12

imperial or metric units

    magicmirror_units: imperial

Default timezone

    magicmirror_timezone: America/New_York

API key from http://www.openweathermap.org

    magicmirror_weather_api_key:

Header for calendar module

    magicmirror_calendar_header: US Holidays

Calendar module 'location' value

    magicmirror_weather_location: Boston

ID from http://www.openweathermap.org/help/city_list.txt

    magicmirror_weather_locationid:

List of newsfeeds

    magicmirror_newsfeeds:
    - { title: New York Times, url: "http://www.nytimes.com/services/xml/rss/nyt/HomePage.xml" }

Hide private events

    magicmirror_calendar_hideprivate: false

List of calendars

    magicmirror_calendars:
    - { symbol: "calendar-check-o ", url: "webcal://www.calendarlabs.com/templates/ical/US-Holidays.ics" }

External json file for compliments module

    magicmirror_compliments_file:

List of third party modules clone url's, example syntax

```
  - name: MMM-connection-status
    url: 'https://github.com/sheyabernstein/MMM-connection-status.git'
    npm_install: yes
    extra_cmd:
```
    magicmirror_extra_modules:

Whether to add watchdog module in config

    magicmirror_watchdog_enabled: true

Name of pm2 app to restart on failure

    magicmirror_watchdog_pm2_app: 'MagicMirror'

Whether to add systemstats module in config

    magicmirror_systemstats_enabled: true

Header for SystemStats module

    magicmirror_systemstats_header: System Stats

Update Interval in ms, defaults to 10s

    magicmirror_systemstats_updateinterval: 10000

Whether to add MyCommute module in config

    magicmirror_mycommute_enabled: false

Header for mycommute module

    magicmirror_mycommute_header: Traffic

Google API key, https://developers.google.com/maps/documentation/javascript/get-api-key

    magicmirror_mycommute_api_key:

Starting address (home)

    magicmirror_mycommute_origin:

Start time when module will be visible (24-hr format, defaults to midnight)

    magicmirror_mycommute_starttime: '00:00'

End time when module will be visible (24hr format, defaults to one minute before midnight)

    magicmirror_mycommute_endtime: '23:59'

Array of days to hide module. Valid numbers are 0 through 6, 0 = Sunday, 6 = Saturday. i.e. [0,6] hides on the weekend.

    magicmirror_mycommute_hidedays:

Format of total travel time

    magicmirror_mycommute_traveltimeformat: m [min]

How often to poll for traffic updates in milliseconds. Defaults to 10 minutes (10 * 60 * 1000)

    magicmirror_mycommute_pollfrequency: 600000

Array of destinations

    magicmirror_mycommute_destinations:

Whether to add alexa module in config

    magicmirror_alexa_enabled: false

Alexa AVS client id

    magicmirror_alexa_clientid:

Alexa AVS client secret

    magicmirror_alexa_clientsecret:

Alexa AVS device id

    magicmirror_alexa_deviceid:

Alexa AVS refresh token

    magicmirror_alexa_refreshtoken:

Alexa AVS wake word

    magicmirror_alexa_wakeword: Smart Mirror

Whether to add the PIR sensor module in config

    magicmirror_pirsensor_enabled: false

BCM pin number sensor's digital out is connected to

    magicmirror_pirsensor_pin: 22

Turn off HDMI port when no motion?

    magicmirror_pirsensor_powersaving: true

Delay befor turning off HDMI port in seconds

    magicmirror_pirsensor_powersaving_delay: 10


## Dependencies

None.

## Example Playbook

    - name: Setup MagicMirror
      import_role:
        name: magicmirror

## License

The MIT License (MIT)

Copyright (c) 2018 Matthew C. Veno

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

https://opensource.org/licenses/MIT

## Author Information

Matthew C. Veno
