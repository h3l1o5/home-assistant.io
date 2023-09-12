---
title: Yardian
description: Instructions on how to integrate Yardian device within Home Assistant.
ha_category:
  - Irrigation
  - Switch
ha_config_flow: true
ha_release: 2023.9
ha_iot_class: Local Polling
ha_codeowners:
  - '@h3l1o5'
ha_domain: yardian
ha_platforms:
  - switch
ha_integration_type: integration
---

The Yardian integration allows you to control your [Yardian Smart Sprinkler Controller](https://yardian.com/products/yardian-pro-smart-sprinkler-controller/).

There is currently support for the following platform within Home Assistant:

- [Switch](#switch) - Allows you to view the status of zones and control them.

{% include integrations/config_flow.md %}

During the configuration, you will have to manually set the **Host** and the **Access Token**. You can find them inside your [Yardian App](https://yardian.com/app/).

![Yardian Host/Token Location](/images/integrations/yardian/yardian_config_flow.jpg)

## Services

### yardian.start_irrigation

Start a zone for a given number of minutes. This service accepts an Yardian Zone switch entity and allows a given duration.

| Service Data Attribute | Optional | Description                                           |
| ---------------------- | -------- | ----------------------------------------------------- |
| `entity_id`            | no       | The Yardian Zone switch to turn on.                   |
| `duration`             | no       | Number of minutes for this zone to be turned on.      |

### yardian.stop_irrigation

Stop a zone.

| Service Data Attribute | Optional | Description                                           |
| ---------------------- | -------- | ----------------------------------------------------- |
| `entity_id`            | no       | The Yardian Zone switch to turn off.                  |

## Configuration

You can do some customization through the `configuration.yaml` file.

### Watering Duration

To customize the watering duration for an Yardian Zone switch `entity_id`.
For those Yardian Zone switch which are not given this value, the duration will be set to 6 minutes by default.

```yaml
# Example of customizing the watering duration
yardian:
  duration:
    switch.yardian_smart_sprinkler_myzone1: 12
    switch.yardian_smart_sprinkler_myzone2: 24
    switch.yardian_smart_sprinkler_myzone3: 30
```
