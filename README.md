# Radeon Event Analyzer

**Radeon Event Analyzer** is a Python-based Windows diagnostic utility that scans System Event Logs for events potentially related to AMD Radeon GPU drivers, graphics crashes, driver timeouts, and GPU-related errors.

It filters Windows events using a predefined collection of AMD GPU-related keywords and exports matching entries to a JSON file for further analysis.

## Features

- Scans Windows System Event Logs.
- Filters events potentially related to AMD Radeon GPUs and drivers.
- Detects driver crashes, hangs, resets and timeouts.
- Searches for DirectX, Direct3D, Vulkan and OpenGL-related errors.
- Detects common GPU-related BSOD codes and `LiveKernelEvent` reports.
- Searches for PCIe, WHEA and other potentially hardware-related events.
- Detects driver installation, update, rollback and removal-related events.
- Exports filtered events into `data.json`.
- Requires no third-party Python packages.

## Supported Event Categories

- **AMD Driver Errors** — `amdkmdag`, `amdwddmg`, `atikmdag` and other AMD-related components.
- **GPU Crashes & Timeouts** — GPU hangs, resets, device lost events and execution timeouts.
- **DirectX & Graphics APIs** — DXGI, Direct3D, Vulkan, OpenGL and related errors.
- **BSOD & LiveKernelEvents** — common graphics-related stop codes and kernel events.
- **Hardware & PCIe Events** — WHEA, PCI Express and bus/interconnect-related events.
- **Driver Installation Events** — driver updates, installation failures, removal and rollback.

## Requirements

- Windows
- Python 3.8 or newer
- Administrator privileges may be required

## Usage

Clone the repository:

```bash
git clone https://github.com/USERNAME/Radeon-Event-Analyzer.git
```

Navigate to the project directory:

```bash
cd Radeon-Event-Analyzer
```

Run the script:

```bash
python main.py
```

After execution, matching events will be saved to:

```text
data.json
```

## Output Format

Events are exported as JSON objects containing:

| Field | Description |
|---|---|
| `id` | Windows Event ID |
| `date` | Event timestamp |
| `source` | Event source |
| `description` | Event description |

## Example

```json
[
    {
        "id": "4101",
        "date": "Example timestamp",
        "source": "Display",
        "description": "Example graphics-related event"
    }
]
```

## How It Works

Radeon Event Analyzer retrieves entries from the Windows System Event Log using `wevtutil`.

The retrieved event data is parsed, and each event is checked against a predefined keyword list containing AMD Radeon driver-related terms, graphics API errors, GPU failure indicators and hardware-related event keywords.

Events containing matching keywords are collected and exported to `data.json`.

## Disclaimer

Radeon Event Analyzer is an informational diagnostic tool. Matching events do not necessarily indicate that the AMD Radeon driver is the cause of a problem.

The tool does not modify system settings, install or uninstall drivers, or attempt to repair system issues.

