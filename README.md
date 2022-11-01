# Tony's Home assistant configuration files

[![GitHub stars](https://img.shields.io/github/stars/antoniopacheco/home-assistant-config.svg?style=plasticr)](https://github.com/antoniopacheco/home-assistant-config/stargazers)
[![GitHub last commit](https://img.shields.io/github/last-commit/antoniopacheco/home-assistant-config.svg?style=plasticr)](https://github.com/antoniopacheco/home-assistant-config/commits/develop)
[![HA Version](https://img.shields.io/badge/Running%20Home%20Asssistant-2022.11.0b%20-darkblue)](https://github.com/home-assistant/core/releases/tag/2022.11.0b)
[![Yaml Lint](https://github.com/antoniopacheco/home-assistant-config/workflows/Yaml%20Lint/badge.svg)](https://github.com/antoniopacheco/home-assistant-config/actions?query=workflow%3A%22Yaml+Lint%22)

## Table of content

- [All my automations](#automations)
- [Input booleans](#input-booleans)
- [My devices](#my-devices)

<!-- start-automations -->
## Automations
1. [Light Automations](#lights-automations) (15 automations)
2. [Control switches](#control-switches)
3. [Blinds Automations](#blinds-automations) (6 automations)
4. [Media Player Automations](#media-player) (4 automations)
5. [Notifications](#notifications) (3 automations)
6. [other Automations](#other-automations) (8 automations)



### Lights automations

#### Porche
- Lights are [turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L18) 60 minutes after sunset
- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L31) at midnight

#### Living Room
- Lights are [turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L58) when movement is detected on dark living room (except when someone is [watching tv on living room](#watching-in-living-room))
- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L86) when no movement is detected


#### Kitchen
- Lights are [turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L114) when movement is detected on kitchen (except when someone is [watching tv on living room](#watching-in-living-room))
- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L137) when no movement is detected for 30 seconds (except when [kitchen is in bussy status](#busy-in-kitchen))

#### Stairs
- Lights are [turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L166) when movement is detected on dark stairs
- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L192) when no movement is detected

#### Master bedroom
- Lights are [turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L220) when movement is detected on dark room (except when in [sleep mode](#sleeping))

- Night light is [tuned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L244) when movement is detected on dark room while in sleep mode

- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L269) when no movement is detected

#### Loft
- Lights are [turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L299) when movement is detected on dark living room (except when someone is watching tv on loft)
- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L324) when no movement is detected (Except when [busy in loft](#busy-in-loft) is activye)

#### Entryway
- Lights are [turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L350) when movement is detected after sunset and before sunrise
- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L372) when no movement is detected

### Blinds automations
- Blinds are [open automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/blinds.yaml#L9) on sunrise (except when on [vacation mode](#vacation-mode))
- Blinds are [closed automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/blinds.yaml#L34) on sunset

### Control switches

#### kitchen
- Mark [kitchen as bussy and turn on lights](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/control_switches.yaml#L17) for 15 minutes when clicking button

- Mark [kitchen as not bussy and turn off lights](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/control_switches.yaml#L17) when clicking button

#### Master bedroom
- Ready to sleep [Automation](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/control_switches.yaml#L78)
    - adjust temperature
    - turn on fan
    - set [sleep mode](#sleeping) on
    - turn off other fans and lights if [guest mode](#guest-mode) is off

#### Living room
- [open blinds](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/control_switches.yaml#L150)
- [close blinds](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/control_switches.yaml#L171)
- [set blinds to 50%](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/control_switches.yaml#L192) with press and hold

### Media player
#### Living Room
- [watching](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/media_player.yaml#L18) tv on living room
    - turn on receiver
    - turn off living room lights
    - close blinds if is before sunset
    - turn off kitchen lights if not [busy](#busy-in-kitchen)
    - set [watching in living room](#watching-in-living-room) true
- [stop watching](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/media_player.yaml#L63) tv on living room
    - set [watching in living room](#watching-in-living-room) false

#### Loft
- [watching](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/media_player.yaml#L89) tv on loft
    - set [watching in loft](#watching-in-the-loft) to true
    - turn off lights if not [busy in loft](#busy-in-loft)
- [stop watching](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/media_player.yaml#L118) tv on loft
    - set [watching in loft](#watching-in-the-loft) to false

### Notifications
#### Alexa notifications
- [notify](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/notifications.yaml#L17) via alexa when washer is done

- [notify](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/notifications.yaml#L34) via alexa when dryer is done

- [notify](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/notifications.yaml#L51) via alexa when dish washer is done
### Other Automations
you can see a list of other [utilities automations](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/utilities.yaml) to update the start and end date of several services like:
- sprinklers
- dishwasher
- washer
- dryer


<!-- end-automations -->

## Input booleans
 ### busy in kitchen
 wheter if someone is [bussy in the kitchen](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L10) or not, controlled via [control switch](#control-switches)

 ## busy in living room
 wheter if someone is [bussy in the living room](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L14) or not

## busy in master bedroom
 wheter if someone is [bussy in the master bedroom](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L18) or not

## sleeping
 wheter we are in [sleeping mode](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L22) or not

## guest_sleeping
 wheter guests are in [sleeping mode](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L26) or not

## busy in loft
 wheter if someone is [bussy in the loft](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L30) or not

## watching in living room
 wheter if someone is [watching tv in the living room](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L34) or not

## watching in the loft
 wheter if someone is [watching tv in the loft](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L38) or not

## cleaned today
 wheter if floor was [cleaned today](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L42) or not 

 ## vacation mode
 wheter if [vacation mode is on](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L46) or not 

 ## guest mode
 wheter if [guest mode is on](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L50) or not 

## My Devices