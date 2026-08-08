# Zemismart Zigbee Blind

Hubitat Elevation driver for Tuya **TS0601** and **TS130F** Zigbee curtain,
blind and shade motors — Zemismart, Moes, Lonsonho and many white-label
variants. Originally authored by **Amos Yuen**; maintained by **kkossev** and
contributors under Apache 2.0.

The driver is maintained in the
[HubitatCommunity/zemismart-zigbee-blind](https://github.com/HubitatCommunity/zemismart-zigbee-blind)
repository. Community thread:
[Release — Zemismart Zigbee Blind driver](https://community.hubitat.com/t/release-zemismart-zigbee-blind-driver/67525).

Current version: **3.6.1** (2026-04-01)

## Features

- Open, close, stop and set position (0–100 %).
- Step open and step close with configurable step amount.
- Pushable-button facade (1 = Open, 2 = Close, 3 = Stop, 4 = Step Open,
  5 = Step Close).
- Motor direction and mode (lift / tilt) control.
- Speed control for supported models.
- Battery percentage reporting for supported models.
- Device health monitoring via `healthStatus` and ping round-trip time (`rtt`).
- Alexa-compatible `SwitchLevel` and `Switch` capabilities.
- Per-model automatic defaults set on Configure (position inversion, mixed
  DP2 reporting, open/close substitution).
- `calibrate` command for model-specific limit and parameter writes.
- Tuya time synchronisation.

## Prerequisites

Before pairing, use the physical device or its supplied remote to set the
motor's fully-open and fully-closed travel limits. Most models require this
step before they can respond correctly to position commands. The driver can
set limits itself only for a small number of models (ZM85EL, ZM25TQ, Moes
Touch Curtain Switch, and a few others via the `calibrate` command).

## Installation

> **Note:** The Hubitat Package Manager listing for this driver is currently
> out of date. Install or update the driver manually using the steps below.

1. In the Hubitat UI go to **Drivers Code** and click **New Driver → Import**.
2. Paste the URL below and click **Import**, then **Save**:

```
https://raw.githubusercontent.com/HubitatCommunity/zemismart-zigbee-blind/refs/heads/main/Zemismart%20Zigbee%20Blind.groovy
```

3. Open the device page for your blind/curtain device.
4. Select `ZemiSmart Zigbee Blind` as the driver and save.
5. Click **Configure** to load the correct defaults for your model.

If the driver was not installed before pairing, re-pair the device without
deleting it first so Hubitat re-runs driver selection.

## Supported device families

"Not tested" means the fingerprint is present but no community test report exists yet. If your device pairs automatically but does not behave correctly, click **Configure** and report results in the [community thread](https://community.hubitat.com/t/release-zemismart-zigbee-blind-driver/67525).

### Zemismart TS0601 motors (Tuya EF00 cluster)

| Device / commercial name | Zigbee model | Manufacturer ID(s) | Notes |
|---|---|---|---|
| Zemismart AM43 roller blind motor (AM43-0.45/40-ES-EZ) | TS0601 | `_TZE200_zah67ekd` | |
| Zemismart AM43 roller blind motor (AM43-0.45/40-ES-EB) | TS0601 | `_TZE200_icka1clh` | Not tested |
| Zemismart AM43 roller blind motor | TS0601 | `_TZE200_rddyvrci` | Inverted open/close/stop commands |
| Zemismart M515EGBZTN blind motor | TS0601 | `_TZE200_xuzcvlku`, `_TZE200_gubdgai2` | Mixed DP2 reporting |
| Zemismart M515EGZT blind motor | TS0601 | `_TZE200_nueqqe6k` | Mixed DP2 reporting |
| Zemismart ZM85EL electric curtain robot (zm85el-2z) | TS0601 | `_TZE200_cf1sl3tj` | Click-control, border and situation-set DPs |
| Zemismart ZM25TQ tubular motor | TS0601 | `_TZE200_fzo2pocs`, `_TZE200_udank5zs` | Limit-setting DPs 103–105; `_TZE200_fzo2pocs` has two firmware versions |
| Zemismart ZM25RX rechargeable roller motor (ZM25RX-0.8/30) | TS0601 | `_TZE200_7eue9vhc` | |
| Zemismart ZM16B tubular motor | TS0601 | `_TZE284_3mzb0sdz` | Position DP 8, target DP 9 |
| Zemismart ZM25EL tubular motor | TS0601 | `_TZE200_68nvbio9` | |
| Zemismart tubular motor | TS0601 | `_TZE200_4vobcgd3` | |
| Zemismart AM15 tubular roller blind motor | TS0601 | `_TZE200_iossyxra` | |
| Zemismart AM02 tubular motor | TS0601 | `_TZE200_cxu0jkjk` | |
| Zemismart AM25 tubular motor (Am25-1/30-ES-EZ) | TS0601 | `_TZE200_nv6nxo0c` | DC 5V rechargeable |
| Zemismart curtain motor | TS0601 | `_TZE200_cowvfni3`, `_TYST11_cowvfni3` | Do not invert position |
| Zemismart curtain motor (not tested) | TS0601 | `_TZE200_eegnwoyw` | |
| Zemismart zigbee motor (not tested) | TS0601 | `_TZE204_r0jdjrvi` | |
| Zemismart zigbee blind (legacy pre-TS0601) | mcdj3aq | `_TYST11_wmcdj3aq` | Direction may be reversed |
| Zemismart zigbee curtain motor (legacy pre-TS0601) | owvfni3 | `_TYST11_cowvfr` | |

### Other branded TS0601 motors (Tuya EF00 cluster)

| Device / commercial name | Zigbee model | Manufacturer ID(s) | Notes |
|---|---|---|---|
| Moes Touch Curtain Switch RF (ZTS-EUR-C) | TS0601 | `_TZE200_nhyj64w2` | Calibration DP 3, backlight DP 7, reversal DP 8 |
| Blindsmart plantation shutter motor | TS0601 | `_TZE284_myikb7qz` | DP 101–103 remaps; open/close via setPosition |
| Tuya LY-108 Cover (Z2M TS0601_cover_6) | TS0601 | `_TZE200_cpbo62rn`, `_TZE200_libht6ua` | Not tested |
| Hiladuo motorised roller shade | TS0601 | `_TZE200_9p5xmj5r` | |
| Zignito tubular roller blind motor | TS0601 | `_TZE200_uzinxci0`, `_TZE200_zpzndjez` | |
| Nova Digital ZBCMR-01 roller blind motor | TS0601 | `_TZE600_ogyg1y6b` | Not tested |
| Roximo curtain motor | TS0601 | `_TZE204_57hjqelq` | Not tested |
| Somgoms curtain switch | TS0601 | `_TZE200_axgvo9jh` | Not tested |
| HUARUI curtain motor | TS0601 | `_TZE200_zxxfv8wi` | Not tested |
| Novato Smart curtain track | TS0601 | `_TZE204_lh3arisb` | Not tested |
| Homeetec curtain/blind switch | TS0601 | `_TZE200_jhkttplm`, `_TZE200_5nldle7w` | Not tested |
| Tuya Zigbee Roller Blinds | TS0601 | `_TZE200_pw7mji0l` | |
| Tuya Zigbee Window Pusher | TS0601 | `_TZE200_g5wdnuow` | Not tested |
| Tuya curtain/blind switch | TS0601 | `_TZE200_p6vz3wzt` | Not tested |
| Generic TS0601 blind/curtain motor (tested) | TS0601 | `_TZE200_yenbr4om`, `_TZE200_5sbebbzs`, `_TZE200_xaabybja`, `_TZE200_hsgrhjpf`, `_TZE200_zuz7f94z`, `_TZE200_ergbiejo`, `_TZE200_wmcdj3aq`, `_TZE200_3i3exuay`, `_TZE200_5zbp6j0u`, `_TZE200_rmymn92d`, `_TZE200_nogaemzt`, `_TZE200_3ylew7b4` | |
| Generic TS0601 blind/curtain motor (not tested) | TS0601 | `_TZE200_eevqq1uv`, `_TZE200_fdtjuw7u`, `_TZE200_gaj531w3`, `_TZE200_r0jdjrvi`, `_TZE200_bqcqqjpb`, `_TZE200_nw1r9hp6`, `_TZE200_llm0epxg`, `_TZE200_n1aauwb4`, `_TZE200_xu4a5rhj`, `_TZE200_feolm6rk`, `_TZE200_nkoabg8w`, `_TZE200_pk0sfzvr`, `_TZE204_guvc7pdy`, `_TZE200_ol5jlkkr`, `_TZE200_b2u1drdv`, `_TZE200_zvo63cmo`, `_TZE200_g5xqosu7`, `_TZE204_g5xqosu7`, `_TZE284_fzo2pocs`, `_TZE200_p2qzzazi`, `_TZE200_clm4gdw4`, `_TZE200_2vfxweng`, `_TZE204_2rvvqjoa`, `_TZE200_zyrdrmno`, `_TZE200_libht6ua`, `_TZE200_zvo63cmo` | |

### TS130F curtain modules (ZCL WindowCovering cluster 0x0102)

| Device / commercial name | Manufacturer ID | Notes |
|---|---|---|
| QS-Zigbee-CP03 curtain module | `_TZ3000_zirycpws` | Tested |
| Moes MS-108ZR curtain switch module | `_TZ3000_1dd0d5yi` | Tested |
| Zemismart Smart curtain/shutter switch | `_TZ3000_74hsp7qy` | Not tested |
| Danor SK-Z802C-US curtain module | `_TZ3000_8h7wgocw` | Not tested |
| LoraTap SC500ZB curtain module | `_TZ3000_e3vhyirx` | Not tested |
| Nous B4Z curtain switch | `_TZ3000_yruungrl` | Not tested |
| Nous L12Z curtain module | `_TZ3000_jwv3cwak` | Not tested |
| Generic curtain module | `_TZ3210_dwytrmda`, `_TZ3000_4uuaja4a`, `_TZ3000_fccpjz5z`, `_TZ3000_vd43bbfq`, `_TZ3000_ke7pzj5d` | Not tested |

### TS030F (ZCL WindowCovering cluster 0x0102)

| Device / commercial name | Manufacturer ID | Notes |
|---|---|---|
| Lidl HG09648 Livarno roller blinds | `_TZB000_42ha4rsc` | Not tested |

## Capabilities and attributes

### Standard capabilities

- `Actuator`
- `WindowShade` — `open()`, `close()`, `stopPositionChange()`,
  `startPositionChange()`, `setPosition(position)`
- `Switch` / `SwitchLevel` — Alexa compatibility
- `PushableButton`
- `Battery`
- `Configuration`
- `Refresh`
- `HealthCheck`

### Custom attributes

| Attribute | Type | Description |
|---|---|---|
| `targetPosition` | number | Last commanded position (0–100 %) |
| `speed` | number | Motor speed (0–100), where supported |
| `healthStatus` | enum | `unknown`, `online`, or `offline` |
| `rtt` | number | Ping round-trip time in milliseconds |

### Commands

| Command | Parameters | Description |
|---|---|---|
| `open` | — | Move to fully open |
| `close` | — | Move to fully closed |
| `stopPositionChange` | — | Stop movement |
| `setPosition` | position (0–100) | Move to target position |
| `stepOpen` | step (optional) | Move toward open by step amount |
| `stepClose` | step (optional) | Move toward closed by step amount |
| `push` | button (1–5) | 1 Open · 2 Close · 3 Stop · 4 Step Open · 5 Step Close |
| `setSpeed` | speed (0–100) | Set motor speed (models that support it) |
| `calibrate` | cmd, val | Write model-specific limit or parameter |
| `configure` | — | Load all defaults for the detected model |
| `refresh` | — | Request current position and state |
| `ping` | — | Send a ping and record round-trip time |

## Preferences

| Preference | Description |
|---|---|
| Enable descriptionText logging | Log state changes at info level |
| Enable debug logging | Log raw Zigbee messages and parse detail |
| Mode | `lift` — motor runs until stopped; `tilt` — short press releases on button up |
| Direction | `forward` or `reverse` motor direction |
| Max Closed Position | Position threshold at or below which `windowShade` reports `closed` (default 1) |
| Min Open Position | Position threshold at or above which `windowShade` reports `open` (default 99) |
| Default Step Amount | Step size used when `stepOpen`/`stepClose` is called without a value (default 10) |
| *(Advanced)* Invert position reporting | Flip 0↔100 for devices that report position backwards |
| *(Advanced)* Ignore first Position report | Enable for models that send the target position before the current position on DP 2 |
| *(Advanced)* Substitute Open/Close with SetPosition | Use `setPosition(0/100)` instead of open/close commands for motors that do not respond in lift mode |
| *(Advanced)* Position report timeout (ms) | How long to wait for position reports before declaring movement finished (default 15 000 ms) |
| *(Advanced)* Force TS130F model | Override detection for units whose Data section shows `endpointId: F2` |
| *(Advanced)* Healthcheck method | `Disabled`, `Activity check`, or `Periodic polling` |
| *(Advanced)* Healthcheck interval | How often to check device health (2 min – 12 h) |

## Google Home integration

The recommended integration is
[Google Home Community](https://community.hubitat.com/t/alpha-community-maintained-google-home-integration/34957)
with these settings:

- **Device type**: `Window Shade`
- **Google Home device type**: `Curtain`
- **Device traits → Open/Close**
  - Open/Close attribute: `windowShade`
  - Open Position Command: `setPosition`