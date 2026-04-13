# Anycubic Cloud Home Assistant Integration

This component is confirmed working with:
- Kobra S1 Combo
- Kobra 3 Combo
- Kobra 2
- Kobra 2 Max
- Kobra 2 Pro
- Photon Mono M5s (Basic support still)
- M7 Pro (Basic support still)

If this works for another printer model, please open an issue and let me know.
If it does not work, please report that too.

Anycubic Cloud is polled for updates every minute, while MQTT updates can arrive multiple times per second.


## Frontend Card

This integration pairs with my [Anycubic card for Home Assistant](https://github.com/ViperRNMC/hass-anycubic_card).


## Gallery


<img width="300" alt="" src="screenshots/kobra3-1.png"> <img width="300" alt="" src="screenshots/anycubic-ace-ui.gif"> <img width="300" alt="" src="screenshots/kobra2-2.png">
<img width="300" alt="" src="screenshots/kobra3-print.png"> <img width="200" alt="" src="screenshots/kobra2-1.png">


## Features

- Supports multiple printers
- Start print services / UI panel
- Pause/Resume/Cancel print buttons
- Edit ACE slot colours/settings via services / UI panel
- File manager via services / UI panel
- Retraction/Extrude services
- Printer sensors e.g. temperature, fan, print speed etc
- Job sensors e.g. name, progress, image preview, time, print params
- ACE sensors
- Firmware Update entities
- ACE drying management with customisable presets
- ACE spool management with customisable colour presets
- Configurable MQTT Connection Mode (Defaults to Printing Only)


## Panel

It also comes with a frontend panel which will be added to your sidebar.
Current features:
- Basic printer info (+ the printer card above)
- File manager (requires MQTT connection to be active)
- Start print services


## Installation

1. Pick an authentication method and obtain your login token.
2. Add this repository to HACS under ... (menu) > Custom Repositories as an **Integration**
3. Restart Home Assistant
4. Go to Settings > Integrations > Add New and search Anycubic
5. Select your chosen authentication mode
6. Paste your **token** into the `User Token` or `Slicer Access Token` box.
7. Select your printer, then you're good to go!
8. Optionally configure additional options in the Home Assistant integration `configure` menus.


### Slicer Authentication

> [!IMPORTANT]  
> Slicer token flow is supported for Windows and macOS.

1. Make sure Slicer Next is logged in, then close it.
2. Locate your `AnycubicSlicerNext` config directory.
   You can open this directly from Slicer Next via `Help` -> `Show Configuration Folder` on macOS.
> [!NOTE]  
>
> Typical locations are:
> ```
> %AppData%\AnycubicSlicerNext\AnycubicSlicerNext.conf
> ```
> or on macOS:
> You can open this directly from Slicer Next via `Help` -> `Show Configuration Folder`.
> ```
> ~/Library/Application Support/AnycubicSlicerNext/AnycubicSlicerNext.conf
> ```
3. Copy the full `access_token` value without quotes. It is typically a 344-character string.
4. To prevent Slicer and Home Assistant from using the same token at the same time, clear it in the Slicer config file.
    Set `access_token` to an empty string, for example: `"access_token": "",`

<img width="400" alt="" src="screenshots/auth_slicer_token.png">


### Web Authentication

> [!IMPORTANT]  
> Web authentication no longer supports MQTT updates.

1. Go to the [Anycubic Cloud Website](https://cloud-universe.anycubic.com/file)
2. Log in
3. Open Developer Tools in your browser
4. Paste `window.localStorage["XX-Token"]` into the **console**
5. Copy the long string of letters and numbers without the `''` characters. This is your token.

<img width="400" alt="" src="screenshots/anycubic_api_token.png">

### Re-Authentication

If you log out or your token expires, Home Assistant will show a re-authentication warning.
Grab a new token using one of the methods above.


## Donations

Support this fork by opening issues and PRs in this repository.


## Thanks

Thanks to @WaresWichall for the original Anycubic Cloud integration work.
Thanks to @dangreco for the original work on Threedy, which I first modded and later completely rewrote with Lit instead of React.
