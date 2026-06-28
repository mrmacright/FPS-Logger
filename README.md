# Enable Metal HUD on iPhone, iPad & Apple TV!

Launch Metal HUD instantly for games, view connected devices, customize HUD presets

<img width="300" alt="MetalHUDVideo" src="https://github.com/user-attachments/assets/affeb269-0c07-4c13-90bd-3e12c754ed25" />

## Download 
▶ [App Store](https://apps.apple.com/app/fps-logger/id6763967836)

## Requirements 
▶ macOS Tahoe 26.2 or later and [M1 or later](https://support.apple.com/en-au/116943)

## Supported platforms for Metal HUD

▶ [iOS 17 or later](https://support.apple.com/en-au/guide/iphone/iphe3fa5df43/17.0/ios/17.0)

▶ [iPadOS 17 or later](https://support.apple.com/en-au/guide/ipad/ipad213a25b2/17.0/ipados/17.0)

▶ Apple TV 4K (1st gen, 2017) or later

> [!IMPORTANT]
> - System-wide HUD support is not possible — Metal HUD works per app by design on iOS, iPadOS, & tvOS  
> - Can I use this app on iPhone or iPad without a Mac? No — Metal HUD requires a Mac for activation on iOS
> - iOS 16 or earlier is not supported as `devicectl` is unavailable

## Manual commands in terminal

**List devices**:
```
xcrun devicectl list devices
```

**Find running apps**:
```
xcrun devicectl device info processes --device <DEVICE_UDID> | grep 'Bundle/Application'
```

**Launch with Default HUD**:
```
xcrun devicectl device process launch \
  -e '{"MTL_HUD_ENABLED": "1"}' \
  --console \
  --device <DEVICE_UDID> \
  "/private/var/containers/Bundle/Application/UUID/AppName.app/"
```

**Custom HUD location**: 

Available options are:
`topleft`, `topcenter`, `topright`, `centerleft`, `centered`, `centerright`, `bottomright`, `bottomcenter`, `bottomleft`
```
xcrun devicectl device process launch \
    --device <device-udid> \
    -e 'MTL_HUD_ENABLED=1' \
    -e 'MTL_HUD_ALIGNMENT=<position>' \
    "/private/var/containers/Bundle/Application/UUID/AppName.app/
```

**Custom HUD scale**:

0.0–1.0. Default: 0.2
```
xcrun devicectl device process launch \
  -e '{"MTL_HUD_ENABLED": "1", "MTL_HUD_SCALE": "<scale>"}' \
  --console \
  --device <device-udid> \
  "/private/var/containers/Bundle/Application/UUID/AppName.app/"
```
**Full HUD customization**:
```
xcrun devicectl device process launch \
  -e '{"MTL_HUD_ENABLED": "1", "MTL_HUD_ELEMENTS": "device,layersize,layerscale,memory,refreshrate,thermal,gamemode,fps,fpsgraph,framenumber,gputime,frameinterval,frameintervalgraph,frameintervalhistogram,presentdelay,metalcpu,gputimeline,shaders,metalfx", "MTL_HUD_ALIGNMENT": "<position>", "MTL_HUD_SCALE": "<scale>"}' \
  --console \
  --device <device-udid> \
  "/private/var/containers/Bundle/Application/UUID/AppName.app/"
```
**Unpair device**:
```
xcrun devicectl manage unpair --device <DEVICE-UDID>
```

## Special thanks

<a href="https://www.elverils.com">
  <img src="https://github.com/user-attachments/assets/03bb3fe6-1b72-4cfb-99ef-c25b0bf147c9" alt="Elverils logo" width="450" />
</a>

[Nat Brown](https://x.com/natbro?lang=en)

[LordOfTheUnicorn](https://github.com/LordOfTheUnicorn)

and to many others who have helped! Thanks
