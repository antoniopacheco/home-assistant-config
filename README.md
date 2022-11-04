# Tony's Home assistant configuration files

[![GitHub stars](https://img.shields.io/github/stars/antoniopacheco/home-assistant-config.svg?style=plasticr)](https://github.com/antoniopacheco/home-assistant-config/stargazers)
[![GitHub last commit](https://img.shields.io/github/last-commit/antoniopacheco/home-assistant-config.svg?style=plasticr)](https://github.com/antoniopacheco/home-assistant-config/commits/develop)
[![HA Version](https://img.shields.io/badge/Running%20Home%20Asssistant-2022.11.0b%20-darkblue)](https://github.com/home-assistant/core/releases/tag/2022.11.0b)
[![Yaml Lint](https://github.com/antoniopacheco/home-assistant-config/workflows/Yaml%20Lint/badge.svg)](https://github.com/antoniopacheco/home-assistant-config/actions?query=workflow%3A%22Yaml+Lint%22)

## Table of content

- [All my automations](#automations)
- [Actionable Notifications](#actionable-notifications)
- [Input booleans](#input-booleans)
- [My devices](#my-devices)

<!-- start automations -->
## Automations

1. [Light Automations](#lights-automations) (15 automations)
2. [Control switches](#control-switches)
3. [Blinds Automations](#blinds-automations) (6 automations)
4. [Media Player Automations](#media-player) (4 automations)
5. [Notifications](#notifications) (3 automations)
6. [other Automations](#other-automations) (8 automations)

### Lights automations

code [here](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml)

#### Porche

- Lights are turned on automatically 60 minutes after sunset
- Lights are turned off automatically at midnight

#### Living Room

- [Lights are turned on automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L58) when movement is detected in a dark living room (except when someone is [watching tv in the living room](#watching-in-living-room))
- Lights are [turned off automatically](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/lights.yaml#L86) when no movement is detected

#### Kitchen

- Lights are turned on automatically when movement is detected in the kitchen (except when someone is [watching tv in the living room](#watching-in-living-room))
- Lights are turned off automatically when no movement is detected for 30 seconds (except when [the kitchen is in busy status](#busy-in-kitchen))

#### Stairs

- Lights are turned on automatically when movement is detected on dark stairs
- Lights are turned off automatically when no movement is detected

#### Master bedroom

- Lights are turned on automatically  when movement is detected in a dark master bedroom (except when in [sleep mode](#sleeping))

- Night light is turned on automatically when movement is detected dark master bedroom while in sleep mode

- Lights are turned off automatically when no movement is detected (except when in [busy mode](#busy-in-master-bedroom))

#### Guest bedroom

- Lights are turned on automatically  when movement is detected in a dark guest bedroom (except when in sleep mode)

- Lights are turned off automatically when no movement is detected in guest bedroom

#### Loft

- Lights are turned on automatically when movement is detected in a dark loft (except when someone is watching tv in the loft)
- Lights are turned off automatically when no movement is detected (Except when [busy in the loft](#busy-in-loft)

#### Entryway

- Lights are turned on automatically when movement is detected after sunset and before sunrise
- Lights are turned off automatically when no movement is detected

### Blinds automations

code in [here](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/blinds.yaml)

- Blinds are open automatically at sunrise (except when on [vacation mode](#vacation-mode))
- Blinds are closed automatically at sunset

### Control switches

Code in [here](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/control_switches.yaml)

#### kitchen

- Mark the [kitchen as busy](#busy-in-kitchen) and turn on the lights, call [still busy in Alexa](#ask-if-still-busy-in-the-kitchen) in 15 minutes

- Mark [the kitchen](#busy-in-kitchen) as not busy and turn off lights when clicking a button

#### Master bedroom

- Ready to sleep Automation:
    - adjust temperature
    - turn on fan
    - turn off the master bedroom lights if there is no movement
    - set [sleep mode](#sleeping) on
    - set [busy in the master bedroom](#busy-in-master-bedroom) to "false"
    - turn off other fans and lights if [the guest mode](#guest-mode) is off

- Click on a button to turn on the lights
    - lights will turn on
    - [Alexa will ask](#ask-if-busy-in-the-master-bedroom) if you want to keep the lights on

#### Living room

- open blinds
- close blinds
- set blinds to 50% with press and hold

### Media player

media player automations [here](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/media_player.yaml)

#### Living Room

- watching tv in the living room
    - turn on receiver
    - turn off the living room lights
    - close blinds if is before sunset
    - turn off kitchen lights if not [busy](#busy-in-kitchen)
    - set [watching in the living room](#watching-in-living-room) to "true"
- stop watching tv in the living room
    - set [watching in the living room](#watching-in-living-room) to "false"

#### Loft

- watching tv in the loft
    - set [watching in the loft](#watching-in-the-loft) to "true"
    - turn off the lights if not [busy in the loft](#busy-in-loft)
- stop watching tv in the loft
    - set [watching in the loft](#watching-in-the-loft) to "false"

### Notifications

Notifications automations [here](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/notifications.yaml)

#### Alexa notifications

All alexa notifications are muted when sleep mode is on

- notify via Alexa when the washer is done

- notify via Alexa when the dryer is done

- notify via Alexa when the dishwasher is done

### Other Automations

You can see a list of other [utilities automations](https://github.com/antoniopacheco/home-assistant-config/blob/develop/automations/utilities.yaml) to update the start and end date of several services like:

- sprinklers
- dishwasher
- washer
- dryer
- reset "sleeping" at 10 am

<!-- end-automations -->

<!-- start actionable notifications -->
## Actionable Notifications

### Alexa actionable notifications

for help on how to setup you can follow [this tutorial](https://www.youtube.com/watch?v=uoifhNyEErE&t=234s)
or use [this repo](https://github.com/keatontaylor/alexa-actions)

#### Master Bedroom

#### Ask if busy in the master bedroom

- if the answer is yes it will change [busy in the master bedroom](#busy-in-master-bedroom) to "true", and will trigger [Ask if still busy in the master bedroom](#ask-if-still-busy-in-the-master-bedroom) in 15 minutes

#### Ask if still busy in the master bedroom

- if the answer is yes, it will trigger itself again in 15 minutes
- if the answer is no, or no answer is detected, it will change [busy in the master bedroom](#busy-in-master-bedroom) to "false" and turn off the master bedroom lights

#### Kitchen

#### Ask if still busy in the kitchen

- if the answer is yes, it will trigger itself again in 15 minutes
- if the answer is no, or no answer is detected, it will change [busy in the kitchen](#busy-in-kitchen) to "false" and turn off the kitchen lights
<!-- end actionable notifications -->
## Input booleans

### busy in kitchen

 wheter if someone is [bussy in the kitchen](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L10) or not, controlled via [control switch](#control-switches)

## busy in living room

 wheter if someone is [busy in the living room](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L14) or not

## busy in master bedroom

Whether someone is [busy in the master bedroom](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L18) or not

## sleeping

 wheter we are in [sleeping mode](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L22) or not

## guest_sleeping

Whether guests are in [sleeping mode](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L26) or not

## busy in loft

Whether someone is [busy in the loft](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L30) or not

## watching in living room

 Whether someone is [watching tv in the living room](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L34) or not

## watching in the loft

 Whether someone is [watching tv in the loft](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L38) or not

## cleaned today

Whether the floor was [cleaned](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L42) today](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L42) or not

## vacation mode

 Whether [vacation mode is on](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L46) or not

## guest mode

Whether if the [guest](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L50)[mode is](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L50) on](https://github.com/antoniopacheco/home-assistant-config/blob/develop/includes/input_booleans.yaml#L50) or not

## My Devices

### Hardware
- Raspberry Pi 4
- Zigbee/zwave adapter [HUSBZB-1](https://amzn.to/3DqKy90)

### Sensors

- Motion Sensos: [Aqara Motion Sensor](https://amzn.to/3zvXmtC)
- Door and window sensor: [Aqara Door and Window sensor](https://amzn.to/3NoM0wW)
- Temperature sensor: [Aqara temperature and Humidity Sensor](https://amzn.to/3SU46bt)
- buttons: Ikea Tradfri

### Lights
- [Lutron caseta](https://amzn.to/3SVCQt1)
- Inovelli series blue
- night lights [GE](https://amzn.to/3fsruPK)
- smart switches [sonoff s31](https://amzn.to/3SU8tmT)

### Media
 - TV's : [Samsung the frame](https://amzn.to/3fljZdp)
 - Voice assistant: [Alexa echo dot](https://amzn.to/3gV0yIB)
 - [Apple TV](https://amzn.to/3sTpToU)

### Appliances
 - Dishwasher: Smart Linear Wash 39dBA Dishwasher in Stainless Steel
 - Refrigerator: Bespoke  with family hub
 - Vacuum: [Irobot S9+ + brava jet](https://amzn.to/3TX0cQf)

### Blinds
- [Ikea Fyrtur](https://amzn.to/3fmNwmO)
