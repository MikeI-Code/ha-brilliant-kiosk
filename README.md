# Brilliant Kiosk for Home Assistant

Manage [Brilliant](https://www.brilliant.tech/) smart-home panels that run the
[brilliant-ha-kiosk](https://github.com/MikeI-Code/brilliant-ha-kiosk) Home Assistant kiosk:
install, update and roll back the kiosk, watch its health, and change its settings from Home
Assistant.

## What you get

For each panel, a device named after the room Brilliant uses (for example *Kitchen Brilliant
kiosk*), linked under the panel's own MQTT device:

- **Update entity** for the kiosk software, with stable and nightly channels and release notes.
- Kiosk version, install state, memory use, and the state of each kiosk service.
- Restart kiosk and reboot buttons; dim and minimum brightness levels.
- Actions (admin only) to read and change kiosk settings and Brilliant bus values, and to read
  redacted logs.
- Repair notices when the panel's settings drift or its MQTT setup disagrees with the options.

## Install

Home Assistant 2026.11 and newer: **Settings → Marketplace → Add from link**, enter
`MikeI-Code/ha-brilliant-kiosk`, install, and restart when asked. (Older versions with HACS: add
it as a custom repository of type Integration.)

Then **Settings → Devices & services → Add integration → Brilliant Kiosk**. Panels running a
current kiosk are discovered over MQTT with their address filled in; you enter the panel's root
password and confirm its SSH host key.

## Documentation

Full documentation (configuration, actions, troubleshooting, known limitations):
[docs/home-assistant-integration.md](https://github.com/MikeI-Code/brilliant-ha-kiosk/blob/nightly/docs/home-assistant-integration.md).

The integration is developed, tested (100 % coverage, `mypy --strict`) and released from
[brilliant-ha-kiosk](https://github.com/MikeI-Code/brilliant-ha-kiosk); this repository is its
Home Assistant distribution. It talks to panels through the
[pybrilliantkiosk](https://pypi.org/project/pybrilliantkiosk/) library. Please file issues in
[brilliant-ha-kiosk](https://github.com/MikeI-Code/brilliant-ha-kiosk/issues).
