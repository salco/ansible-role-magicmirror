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

List of calendars

    magicmirror_calendars:
    - { symbol: "calendar-check-o ", url: "webcal://www.calendarlabs.com/templates/ical/US-Holidays.ics" }


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
