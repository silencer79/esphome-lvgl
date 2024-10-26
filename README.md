# ESPHome configs and LVGL examples for cheap touchscreen devices

## Supported Devices
* Sunton `ESP32-2432S028R` 2.8" with resistive touch and USB micro-B.
* Sunton `ESP32-8048S043` 4.3" with capactivive touch and USB-C.
* Sunton `ESP32-8048S050` 5.0" with capactivive touch and USB-C.
* Elecrow `DIS05035H` CrowPanel 3.5" (v2.2) with resistive touch and USB-C.

## File Structure
If all you are looking for is a device-specific config then look no further than the `devices/` directory. The YAML files in there are clean and free from anything not related to the devices themselves. They are intended to be used as [Packages](https://esphome.io/components/packages.html) in a higher-level YAML, which allows for device-specific YAML and common YAML to be kept in separate files, avoiding duplicate code and making it easier to update groups of devices. 

The example YAML files in the root of this repo demonstrate how to use each device's YAML with some common YAML, including a resolution-specific (but not device-specific) LVGL layouts. 

## Advanced YAML Techniques
Aside from the ESPHome Packages feature used to separate device-specfic YAML from common YAML config, there are some other potentially unfamiliar techniques in use here. For example, the files within `dashboards/` use [YAML anchors and aliases](https://ref.coddy.tech/yaml/yaml-anchors) which help reduce code duplication. I use anchors and aliases instead of `styles` and `style_definitions` as they support reuse of anything I want instead of being restricted to just styles, and because they override the default `theme` when used. There is a bug or perhaps an odd design choice that prevent `styles`/`style_definitions` from overriding `theme`. I define my anchors within a made-up key called `.sizing` as anything prefixed with a dot will not cause errors when parsed by ESPHome.

# TODO
This readme isn't finished :)