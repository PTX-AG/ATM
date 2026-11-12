# ATM 1.0.0 Beta — build 2026.1111.1

Released 2026-11-11. A beta update of ATM for macOS, in two packages.

| Package | For | macOS | Size | SHA-256 |
|---|---|---|---|---|
| `ATM-1.0.0-beta-2026.1111.1-arm64.dmg` | Apple silicon | 15 or later | 10.4 MB | `6f067d9d10aae8acd247c6ac36c81623975faec1681affb183195eeca609834c` |
| `ATM-1.0.0-beta-2026.1111.1-x86_64.dmg` | Intel | 15 to 26 | 11.0 MB | `298a426559458040abe41c64a64d009f48a5659020606f0791220c0abc4a66b1` |

Both packages are signed with a Developer ID, notarized by Apple and stapled, so they open without a Gatekeeper
warning, even offline. To check a download, run `shasum -a 256` on the DMG and compare it with the table.

## New in this build

**CPU, GPU and memory clocks**
- The Performance page, the menu bar popups and the menu bar show how fast the CPU, the GPU and the memory run.
  Settings › Menu bar has three new items for them: CPU frequency, GPU frequency and Memory frequency.
- Apple silicon: each CPU cluster's clock and the GPU's, live, for example "3.70 GHz". The memory shows the memory
  controller's state, for example "F5, the top" or "F3 of F5": macOS gives no MHz for it, so ATM doesn't invent one.
- Intel: the CPU clock is live once ATM's helper is installed (the helper reads it from macOS's `powermetrics`).
  Each AMD graphics card's clock is live with no helper. The memory shows its configured speed, for example
  "5600 MHz (configured)", the value the Mac is set to, not a measurement.

**Run at login**
- Settings › General has a Run at login switch, so ATM opens each time you log in, after every restart.

**Fixed**
- On Intel CPUs with performance and efficiency cores (12th generation and later), the CPU page counts performance
  cores, not threads: 8, not 16, on an i9-13900KF.
- On Intel Macs, readings a Mac never gives (an AMD card's renderer and tiler figures, power keys the SMC never
  answers) are no longer counted as "limited" in the capabilities summary.

**If you use ATM's helper on an Intel Mac:** after installing this build, remove the helper in Settings › Privacy ›
Remove Helper and turn fan control on again, so the new helper that reports CPU clocks takes over.

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

## Fixed in the first beta (2026.1110.2)

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
- On a Hackintosh, the memory speed is the one OpenCore reports to macOS, which may differ from the BIOS setting.
- ATM doesn't update itself. Download new versions from the Releases page.

## Requirements

- Apple silicon package: a Mac with Apple silicon and macOS 15 Sequoia or later.
- Intel package: an Intel Mac (or Hackintosh, best effort) with macOS 15 Sequoia to macOS 26 Tahoe.
