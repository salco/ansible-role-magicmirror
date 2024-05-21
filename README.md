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

### Quality of life
* autologin
* disable screen saver
* hide mouse

| Name | Description | Default value |
| -- | -- | -- |
| `use_plymouth` | Bool used to determine if you want plymounth splashscreen from magicmirror | `false` |
| `use_qol`| Bool used to get all the quality of life improvement | `false` |
| `use_audiocfg`| Bool used to setup audio on target | `false` |
| `magicmirror_units` | can be `imperial` or `metric` | `metric` |
| `magicmirror_nodejs_stable_branch` | Stable branch name for nodejs installer | `20.x` |
| `magicmirror_min_nodejs_version` | Minimal nodejs version string | `v17.7.2` |
| `magicmirror_pm2_user` | User account to use pm2 with | `{{ ansible_user_id }}` |
| `magicmirror_src_dir` | Parent directory to checkout MagicMirror repository | `{{ ansible_env.HOME }}/src` |
| `magicmirror_timeformat` | The form of time notation that will be used. Possible values are `12` or `24`. | `24` |
| `magicmirror_plymouth_theme_dir` | Path to plymouth themes directory for MagicMirror | `/usr/share/plymouth/themes/MagicMirror` |
| `magicmirror_apt_packages` | Dependent apt packages that will be installed (default list) | curl, wget, git, build-essential, unzip, unclutter, x11-xserver-utils |
| `magicmirror_audio_output_device` | Audio output device, valid options are -  `0`: Automatic, `1`: Analogue (headphone jack), `2`: HDMI | `0` |
| `magicmirror_audio_capture_device` | Audio capture device | 'hw:1,0' |

## Other option
> *INFO* need to be move later: List of third party modules clone url's, example syntax

An example to help the description below.
```.yml
magicmirror_extra_modules:
  My-SystemStats:
    name: 'MMM-SystemStats'
    position: 'bottom_right'
    classes: 'small dimmed'
    header: "System Stats"
    config: |
      updateInterval: 10000,
      animationSpeed: 0,
      align: 'right',
      thresholdCPUTemp: 167
  MMM-connection-status:
    name: MMM-connection-status
    url: 'https://github.com/sheyabernstein/MMM-connection-status.git'
    npm_install: yes
    extra_cmd: "echo 'some text'"
```

- `magicmirror_extra_modules` : The list of all modules you want to deploy
  - _<your_unique_key_name>_ : an unique name it's use to address sub-variables during itteration in [config.js](templates/config.js.j2)

Here is the list of all option you can define under "_<your_unique_key_name>_":

| Name | Description | Optional |
| -- | -- | -- |
| `name` | The module name |  |
| `url` |  TBD | |
| *`header`* | To display a header text above the module, add the header property. | __yes__ |
| *`position`* | The location of the module in which the module will be loaded. Possible values are `top_bar`, `top_left`, `top_center`, `top_right`, `upper_third`, `middle_center`, `lower_third`, `bottom_left`, `bottom_center`, `bottom_right`, `bottom_bar`, `fullscreen_above`, and `fullscreen_below` | __yes__ |
| *`animateIn`* | Special animate name when a module appears. See: [this site](https://animate.style/)  | __yes__ |
| *`animateOut`* | Special animate name when a module should hide. See: [this site](https://animate.style/)  | __yes__ |
| *`config`* | An object with the module configuration properties. Check the documentation of the module for more information.  | __yes__ |

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
Repo forked from https://gitlab.com/flyingchipmunk_ansible/magicmirror
Matthew C. Veno
