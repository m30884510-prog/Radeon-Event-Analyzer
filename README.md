[README.md](https://github.com/user-attachments/files/35419688/README.md)
# Radeon Event Analyzer

**Radeon Event Analyzer** is a lightweight Windows diagnostic utility for finding Windows Event Log entries that may be related to AMD Radeon graphics drivers, GPU crashes, driver timeouts, and graphics-related hardware errors.

The application includes a **Tkinter graphical interface** and can also export matching events to `data.json` for further inspection or sharing when asking for technical support.

> Radeon Event Analyzer is an event-collection and filtering tool. It helps you investigate possible causes of graphics problems, but it does not automatically determine the root cause or repair your system.

## Features

- **Graphical interface:** view the collected events in a desktop GUI built with Tkinter.
- **Event timestamps:** see when each detected event occurred.
- **Windows Event Log scanning:** checks up to the latest 10,000 entries from the Windows System event log.
- **AMD driver event detection:** looks for entries associated with components such as `amdkmdag`, `amdwddmg`, and other AMD-related terms.
- **GPU crashes and timeouts:** searches for driver hangs, resets, device-lost events, and execution timeouts.
- **Graphics API errors:** checks for potentially relevant DirectX, DXGI, Direct3D, Vulkan, and OpenGL entries.
- **BSOD and LiveKernelEvent indicators:** includes common graphics-related stop codes and LiveKernelEvent reports.
- **Hardware-related events:** checks for WHEA, PCIe, and other potentially relevant hardware or bus errors.
- **Driver installation events:** looks for driver update, installation, removal, and rollback-related entries.
- **JSON export:** saves matching events to `data.json`.
- **No third-party Python packages required.**

## Requirements

- Windows
- Python 3.8 or newer, if running from source
- Tkinter (normally included with the standard Windows Python installer)
- Administrator permissions may be required to access some event log information

## Getting started

### Option 1: Download the packaged version

1. Open the [Radeon Event Analyzer repository](https://github.com/m30884510-prog/Radeon-Event-Analyzer).
2. Download **Radeon Event Analyzer v2.1.zip** from the repository files.
3. Extract the archive.
4. Launch the application using the files included in the archive.

### Option 2: Run the Python script

1. Download **Radeon Event Analyzer v2.1.zip** from the repository.
2. Extract the archive.
3. Open the extracted folder that contains `main.py`.
4. Run the application:

```bash
python main.py
```

If Windows blocks access to some event records, try running the application from an elevated terminal or with administrator permissions.

## How it works

1. The application reads entries from the Windows System Event Log using the Windows `wevtutil` utility.
2. It checks up to the most recent 10,000 events.
3. Event information is examined for a predefined set of AMD Radeon, graphics API, GPU failure, and hardware-related keywords.
4. Potentially relevant entries are displayed in the Tkinter interface, including their timestamps.
5. Matching entries can be exported to `data.json` for later review.

The analyzer uses keyword-based filtering. This makes it useful for collecting clues, but it cannot guarantee that every relevant event will be found or that every matched event is related to the actual problem.

## Event categories

| Category | Examples of matched information |
| --- | --- |
| AMD driver events | `amdkmdag`, `amdwddmg`, `atikmdag`, and other AMD-related components |
| GPU crashes and timeouts | Driver hangs, GPU resets, device-lost events, execution timeouts |
| Graphics APIs | DirectX, DXGI, Direct3D, Vulkan, OpenGL |
| BSOD and LiveKernelEvent | Common graphics-related stop codes and LiveKernelEvent reports |
| Hardware and PCIe | WHEA, PCI Express, and bus/interconnect-related events |
| Driver installation | Driver updates, installation failures, removal, and rollback events |

## JSON output

Matching events are exported to `data.json`. Each event contains the following fields:

| Field | Description |
| --- | --- |
| `id` | Windows Event ID |
| `date` | Date and time when the event was recorded |
| `source` | Event source or provider |
| `description` | Event description or message |

Example structure:

```json
[
  {
    "id": "4101",
    "date": "2025-01-15 18:42:10",
    "source": "Display",
    "description": "Example graphics-related event"
  }
]
```

The example is illustrative; actual event IDs, timestamps, sources, and descriptions depend on the events recorded by Windows on your computer.

## Important notes

- A detected event is **not proof** that the AMD Radeon driver or GPU caused the issue.
- Windows may record unrelated events that happen to contain matching keywords.
- Some graphics problems may not produce an event that matches the analyzer's filters.
- The tool is intended for diagnostics and log collection. It does not change GPU settings, install or uninstall drivers, or attempt to repair Windows.

## Contributing and feedback

Bug reports, suggestions, and improvements are welcome. When reporting an issue, include the application version, your Windows version, a brief description of what happened, and relevant sanitized log output. Do not publish personal information or other sensitive data from your event logs.

## Disclaimer

Radeon Event Analyzer is provided **as is**, for informational and diagnostic purposes. Always review diagnostic results before making changes to your system. The author is not responsible for problems caused by actions taken based on the tool's output.
