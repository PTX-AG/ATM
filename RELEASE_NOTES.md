# ATM 1.0.0 Beta — build 2026.1110.2

Released 2026-11-10. The first public beta of ATM for macOS, in two packages.

| Package | For | macOS | Size | SHA-256 |
|---|---|---|---|---|
| `ATM-1.0.0-beta-2026.1110.2-arm64.dmg` | Apple silicon | 15 or later | 10.4 MB | `d27561c468a4c5aabf352ccd3fda37e3804319069a72a11efd667e129c8bc135` |
| `ATM-1.0.0-beta-2026.1110.2-x86_64.dmg` | Intel | 15 to 26 | 10.9 MB | `27b6e3d6278ca2db61c4d22ae44e18a7817f6e36e420602b1dcf0f8efc2d41cf` |

Both packages are signed with a Developer ID, notarized by Apple and stapled, so they open without a Gatekeeper
warning, even offline. To check a download, run `shasum -a 256` on the DMG and compare it with the table.

## What's in it

**Menu bar**
- Pick what sits in the menu bar and in what order: CPU, memory, network, disk, temperature, fans, power, battery,
  Bluetooth device batteries and a clock with extra time zones. Show them as one combined item or one item each.
- Click for a popup with the last 60 seconds of CPU, memory, network and disk, the top processes for each, and
  sections for the GPU, battery, fans and temperatures. Each metric can open its own popup.
- Thermal pressure, and optional notifications when a temperature passes a limit you set or data stops updating.

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
- Light and dark appearance. Refresh every 1, 2 or 5 seconds, or pause collection.

**Fan control (optional)**
- Set fan speeds from the menu bar popup, after you approve ATM's helper once in System Settings. Fans go back to
  automatic when ATM quits. Every change is logged in `/Library/Logs/ATM/fan-changes.log`.
- The same helper lets the Processes page show every process's use, including other users' and the system's.
  Remove it in Settings › Privacy.

**Help map more Macs**
- Settings › Developer › Collect sensor data runs a short, guided sensor recording and zips it to your Desktop, so you
  can send it in. It checks every record for private details first.

## Privacy

ATM has no accounts, analytics or update checks and opens no network connections. A value it can't read shows as
"—", never as 0.

## Faster and lighter

- The Processes page uses about half the CPU it did and far less memory churn: rows update in place on each scan
  instead of being rebuilt.
- The Sensors page no longer redraws 60 times a second behind its CPU graph.
- With the window closed, ATM collects only what the menu bar shows.
- File › Export can save the stored minute-by-minute history of every reading, with any missed minutes marked.
  Settings says when that history can't be saved, and why.
- The Processes page's System line includes the CPU that no single process is charged for, so the rows add up.
- The DMG opens on a laid-out window with large icons: drag ATM onto Applications.

## Fixed since the earlier test builds

- In a narrow window, the command bar's controls give way one by one instead of cutting "Pause collecting" short.
- VoiceOver reads the right values again after you switch the menu bar away from one combined item.
- Some minutes published twice as many updates as they should after a slow sensor read. Every source now stays on
  one shared schedule, so a late reading falls back in step after one update.
- On Intel Macs, Settings › Tray could slow the whole app to a crawl while you added or removed items.
- On non-Retina displays, the refresh and graph-range choices no longer shorten to "…", and thin dividers draw as one
  whole pixel instead of a faint half pixel.
- On Intel Macs with more than one graphics card, GPU temperatures carry the card's name, for example
  "AMD Radeon RX 6900 XT GPU 1 Die".

## Known limitations

- The Intel package has been tested on an Intel Hackintosh, not yet on a real Intel Mac. Sensor names and some
  readings may differ on real Intel Macs.
- Sensor names for M3 to M6 Macs are partly estimated from the Macs measured so far and are marked unverified. They
  will be corrected as sensor data comes in.
- The Intel package supports macOS up to 26 Tahoe, the last macOS for Intel Macs.
- ATM doesn't update itself. Download new versions from the Releases page.

## Requirements

- Apple silicon package: a Mac with Apple silicon and macOS 15 Sequoia or later.
- Intel package: an Intel Mac (or Hackintosh, best effort) with macOS 15 Sequoia to macOS 26 Tahoe.
