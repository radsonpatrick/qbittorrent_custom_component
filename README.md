![hacs_badge](https://img.shields.io/badge/hacs-custom-orange.svg) [![BuyMeCoffee][buymecoffeebedge]][buymecoffee]

# Acknowledgements
<a href = (https://github.com/danielbibit)>@danielbibit</a> I adapted his code for use in new version to homeasssistant.

<a href = (https://github.com/boralyl)>@boralyl</a> for you excelent tutorial : <a href = "https://aarongodfrey.dev/home%20automation/building_a_home_assistant_custom_component_part_1/">Building a Home Assistant Custom Component</a>.
 

# qBitTorrent Custom Component

[![qbittorrent](https://github.com/linuxserver/docker-templates/raw/master/linuxserver.io/img/qbittorrent-icon.png)](https://www.qbittorrent.org/)

Custom component to get  information  qBitTorrent for the home assistant  

# Installation

## HACS

- Have [HACS](https://hacs.xyz/) installed, this will allow you to easily update.

- Add https://github.com/radsonpatrick/qbittorrent_custom_component as a custom repository with Type: Integration
- Click Install under "qBitTorrent" integration.
- Restart Home-Assistant.

## Manual

- Copy directory custom_components/custom_qbittorrent to your <config dir>/custom_components directory.
- Configure.
- Restart Home-Assistant.

## Configuration for sensor:

```yaml
sensor:
  - platform: qbittorrent
    name: qbit  #optional
    host: "http://hostname:8080"
    username: "admin"
    password: "adminadmin"
    monitored_variables:
      - 'current_status'
      - 'total_torrents'
      - 'active_torrents'
      - 'inactive_torrents'
      #- 'downloading_torrents' if you not need remove or comment
      #- 'seeding_torrents'
      - 'resumed_torrents'
      - 'paused_torrents'
      - 'completed_torrents'
      - 'download_speed'
      - 'upload_speed'
```
### in lovelace : 

<img src="img/sensor.png" width="400">

<img src="img/torrents_active.png" width="400">

<img src="img/torrents_progress.png" width="400">

***

## Configuration for switch:
 ### configurate your `alternative_speed` in qbittorrent interface

```yaml
switch:
  - platform: qbittorrent
    name: qbit #optional
    host: "http://hostname:8080"
    username: "admin"
    password: "adminadmin"
```
### in lovelace:

<img src="img/alternative_speed.png" width="400">

***

## Configuration for Number (limit global speed value)
  not confuse between `alternative_speed` switch and `limit_speed_switch`.
  
  `limit_speed_switch` you get one value between `min:` and `max:`, for limit global download speed
  
  ### `value` = 0 is unlimited speed

```yaml
number:
  - platform: custom_qbittorrent 
    name: qbit_limit_speed #optional
    host: "http://192.168.1.2:8080"
    username: "admin"
    password: "adminadmin"
    min: 0
    max: 120  #value in Mb/s
    step: 0.5
```
### in lovelace:

<img src="img/number_limit_speed_in_mbps.png" width="400">

***

[buymecoffee]: https://www.buymeacoffee.com/radsonpatrick
[buymecoffeebedge]: https://camo.githubusercontent.com/cd005dca0ef55d7725912ec03a936d3a7c8de5b5/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6275792532306d6525323061253230636f666665652d646f6e6174652d79656c6c6f772e737667
