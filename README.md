# Brilliant Kiosk for Home Assistant

Manage [Brilliant](https://www.brilliant.tech/) smart-home panels that run the
[brilliant-ha-kiosk](https://github.com/MikeI-Code/brilliant-ha-kiosk) Home Assistant kiosk:
install, update and roll back the kiosk, watch its health, change its settings and read its
logs from Home Assistant. Integration version 0.2.0.

The panel's everyday entities (wired light, motion, display state, screensaver and night
switches, gestures) are published by the kiosk itself over MQTT. This integration is the admin
layer on top and links its device to that MQTT device.

## Requirements

* Home Assistant 2026.3.1 or newer, with the **MQTT** integration set up.
* A Brilliant panel with SSH switched on (Brilliant's **Root SSH Login** setting). The kiosk
  itself can be installed by this integration.

## Install

**Home Assistant 2026.11 and newer:** **Settings, Marketplace, Add from link**, enter
`MikeI-Code/ha-brilliant-kiosk`, install, and restart when asked.

**Home Assistant 2026.3.1 to 2026.10:** in HACS, add `https://github.com/MikeI-Code/ha-brilliant-kiosk`
as a custom repository of type *Integration*, download **Brilliant Kiosk**, restart.

Then **Settings, Devices & services, Add integration, Brilliant Kiosk**. A panel running a
current kiosk nightly is discovered over MQTT with its address filled in; you enter the panel's
root password (or paste a private key) and confirm its SSH host key. A panel without the kiosk
can be installed from the same dialog: it asks for the Home Assistant URL the panel should use, a
long-lived access token and your MQTT broker.

## What you get

For each panel, a device named **"\<Room\> Brilliant kiosk"** (Brilliant's own room name):

* **Update entity** for the kiosk, with Stable and Nightly channels and release notes.
* Kiosk version, install state, memory use, load, and the running state of each kiosk service.
* **Restart kiosk**, **Reboot panel**, **Reapply kiosk** and **Roll back kiosk** buttons; Dim
  level and Minimum level numbers.
* Actions (administrators only): `set_env`, `get_env`, `logs` (redacted), `bus_get`, `bus_set`,
  `install_version`.
* Repair issues when the panel's running and saved settings differ, or its MQTT provider does
  not match the options. MQTT is never switched off: the panel publishes either with the kiosk's
  built-in MQTT or through brilliant-mqtt.

## Documentation

Full documentation (configuration, installation parameters, entities, actions, repairs,
polling, known limitations, troubleshooting):
[docs/home-assistant-integration.md](https://github.com/MikeI-Code/brilliant-ha-kiosk/blob/main/docs/home-assistant-integration.md).
The kiosk itself is documented in the
[manual](https://github.com/MikeI-Code/brilliant-ha-kiosk/blob/main/docs/MANUAL.md).

This repository is the Home Assistant distribution of the integration. It is developed, tested
(100 % coverage, `mypy --strict`) and released from
[brilliant-ha-kiosk](https://github.com/MikeI-Code/brilliant-ha-kiosk), and talks to panels through
the [pybrilliantkiosk](https://pypi.org/project/pybrilliantkiosk/) library. Please file issues in
[brilliant-ha-kiosk](https://github.com/MikeI-Code/brilliant-ha-kiosk/issues).

Apache License 2.0. Brilliant is a trademark of its respective owner; this is an independent
community project, not affiliated with Brilliant or the Home Assistant project.
