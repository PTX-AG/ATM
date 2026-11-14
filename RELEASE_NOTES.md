# ATM 1.0.0 Beta — build 2026.1114.2

Released 2026-11-14. A beta update of ATM for macOS, in two packages.

| Package | For | macOS | Size | SHA-256 |
|---|---|---|---|---|
| `ATM-1.0.0-beta-2026.1114.2-arm64.dmg` | Apple silicon | 15 or later | 11.0 MB | `57eb2107ea78aafb5666def7ea986655027ba7f4de6eb5e0661ef1d7e0c05240` |
| `ATM-1.0.0-beta-2026.1114.2-x86_64.dmg` | Intel | 15 to 26 | 11.5 MB | `4903ee2d4879bc0cf2c0a32a58859389c60089dff82a225a7258277372a21dc9` |

Both packages are signed with a Developer ID, notarized by Apple and stapled, so they open without a Gatekeeper
warning, even offline. To check a download, run `shasum -a 256` on the DMG and compare it with the table.

## New in this build

**Updates from GitHub, when you allow it**
- ATM can now tell you when a newer build is out, show what's new, and install it when you say so: Install, Skip
  This Version or Remind Me Later. It never installs anything by itself.
- Nothing is checked until you allow it. On the second launch ATM asks whether to check for updates automatically;
  Settings › General has the same switch, "Check for updates automatically", and a Check Now button.
- With the switch on, ATM asks GitHub once a day. "Check for Updates…" in the app menu and in the menu bar's menu
  checks once, whether the switch is on or not.
- Each update is checked before it opens: the list of updates must carry ATM's own update signature, the DMG must be
  signed by ATM's developer, and ATM refuses a build older than the one you have.
- If a daily check finds an update while ATM's window is closed, the menu bar's menu and Settings say so, and, if you
  allowed ATM's notifications, a notification does too.

**CPU power**
- The Performance page's CPU section shows the CPU's power on Intel Macs too.
- Settings › Menu bar has a CPU power row of its own, with the CPU's total and its clusters. The Power row keeps the
  rest, and Power rows you saved before move over by themselves.
- Intel: with ATM's helper installed, the sensors list has "CPU Package", the whole package's power, read from
  macOS's `powermetrics`. The SMC key that used that name is now "CPU Cores (Package)".

**Lighter**
- With the Processes page in front, reading the process list takes about half the CPU it did: the data comes as a
  quarter of the bytes.
- The command bar names its readings once per kind instead of once per reading every second.

**Fixed**
- On an Intel Hackintosh, six power sensors that VirtualSMC always reads as 0 no longer show as unavailable. A real
  Intel Mac keeps them.
- The app inside the DMG now passes Apple's strictest signature check (`codesign --verify --strict`). The
  2026.1111.1 DMGs' copy didn't, though Gatekeeper accepted it.
- SQLite, used for the optional app history, is updated to 3.54.1 for a security fix.

**If you use ATM's helper on an Intel Mac:** after installing this build, remove the helper in Settings › Privacy ›
Remove Helper and turn fan control on again, so the new helper that reports the CPU package power takes over.

## What's in it

**Menu bar**
- Pick what sits in the menu bar and in what order: CPU, memory, network, disk, temperature, fans, power, battery,
  Bluetooth device batteries and a clock with extra time zones. Show them as one combined item or one item each.
- Click for a popup with the last 60 seconds of CPU, memory, network and disk, the top processes for each, and
  sections for the GPU, battery, fans and temperatures. Each metric can open its own popup.
- Thermal pressure, and optional notifications when a temperature passes a limit you set or data stops updating.
- The CPU, the GPU and the memory clocks, for example "3.70 GHz" (Apple silicon) or "5600 MHz (configured)" (Intel
  memory).

**Window**
- **Processes:** every app and background process with CPU, memory, disk and network use, with heat shading. Search
  by name, PID or owner, and end a task.
- **Performance:** CPU with performance and efficiency cores, memory and pressure, each disk, each network interface,
  the GPU, the Neural Engine and temperature, over 60 seconds, 5 minutes or an hour.
- **App history:** which apps used CPU, memory, disk and network this session.
- **Startup:** your login items and launch agents, with a switch to turn your own off and on.
- **Users, Details, Services:** who is signed in, the full process list, and the system's services.
- **Sensors:** every temperature, fan, power, voltage and current sensor ATM can read, with minimum, maximum,
  trend, age and source. Pin sensors to see them as graphs.
- Light and dark appearance. Refresh every 1, 2 or 5 seconds, or pause collection. Run at login, in Settings ›
  General.

**Fan control (optional)**
- Set fan speeds from the menu bar popup, after you approve ATM's helper once in System Settings. Fans go back to
  automatic when ATM quits. Every change is logged in `/Library/Logs/ATM/fan-changes.log`.
- The same helper lets the Processes page show every process's use, including other users' and the system's.
  Remove it in Settings › Privacy.

**Help map more Macs**
- Settings › Developer › Collect sensor data runs a short, guided sensor recording and zips it to your Desktop, so you
  can send it in. It checks every record for private details first.

## Privacy

ATM uses the network only to check GitHub for updates, and only after you allow it (Settings › General). The request
carries the names and versions of ATM and its updater; GitHub sees your Mac's internet address, as with any web
page. Your readings stay on this Mac: ATM has no accounts and no analytics. A value it can't read shows as "—",
never as 0.

## Known limitations

- Builds 2026.1111.1 and older have no update check: install this build by hand once, and later builds can announce
  themselves.
- The Intel package has been tested on an Intel Hackintosh, not yet on a real Intel Mac. Sensor names and some
  readings may differ on real Intel Macs.
- Sensor names for M3 to M6 Macs are partly estimated from the Macs measured so far and are marked unverified. They
  will be corrected as sensor data comes in.
- The Intel package supports macOS up to 26 Tahoe, the last macOS for Intel Macs.
- On a Hackintosh, the memory speed is the one OpenCore reports to macOS, which may differ from the BIOS setting.

## Requirements

- Apple silicon package: a Mac with Apple silicon and macOS 15 Sequoia or later.
- Intel package: an Intel Mac (or Hackintosh, best effort) with macOS 15 Sequoia to macOS 26 Tahoe.
