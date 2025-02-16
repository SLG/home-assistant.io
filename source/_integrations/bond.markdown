---
title: Bond
description: Instructions on setting up Bond Bridge within Home Assistant.
ha_category:
  - Hub
  - Cover
  - Fan
  - Light
  - Switch
ha_iot_class: Local Push
ha_release: 0.113
ha_domain: bond
ha_codeowners:
  - '@prystupa'
ha_config_flow: true
ha_quality_scale: platinum
ha_zeroconf: true
ha_platforms:
  - cover
  - fan
  - light
  - switch
---

The Bond integration allows you to control appliances through your [Bond Bridge](https://bondhome.io/). Duplicates your RF remote control.

Supported devices (see Requirements section below):

- Ceiling fans
- Shades
- Fireplaces

## Tested Bond Devices

The following devices have been tested with Home Assistant and confirmed to be working:

- Bond Bridge v1 (snowbird)
- Bond Bridge v2 (zermatt)
- Bond Bridge Pro (zermatt-pro)
- Smart By Bond Fans (breck)

## Prerequisites

To use Bond controlled devices in your installation, add your Bond hub host and access token from the integrations page. Instructions for how to obtain an access token can be found on the [Bond Local API](http://docs-local.appbond.com/#section/Getting-Started/Get-Device-Information) documentation, which includes a section for how to obtain the [IP address of the device](http://docs-local.appbond.com/#section/Getting-Started/Finding-the-Bond-IP) which you will need to obtain the access token.

{% include integrations/config_flow.md %}

## Requirements

This integration supports Bond bridges with firmware v2.10.x and up.
Bond bridges with firmware v2.9.x and lower will **not** work correctly. Please
upgrade your firmware from Bond app before adding this integration.

## BPUP Support (Push updates)

Firmware version 2.10.8 or newer is required for push updates. The integration
will fallback to polling for 2.10.x versions lower than .8

### Service `bond.start_increasing_brightness`

Start increasing the light brightness.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | no | String or list of strings of `entity_id`s.

### Service `bond.start_decreasing_brightness`

Start decreasing the light brightness.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | no | String or list of strings of `entity_id`s.

### Service `bond.stop`

Stop any in-progress action and empty the queue. Calling this service will
stop any increase or decrease in brightness that is in progress.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | no | String or list of strings of `entity_id`s.

