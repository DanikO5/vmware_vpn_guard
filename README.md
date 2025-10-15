# VMware VPN Guard

---

## Description

**VMware VPN Guard** is a lightweight Python-based VPN kill switch specifically designed for **VMware** virtual machine users. It continuously monitors your system's active network interfaces for a defined **VPN connection**. If the VPN disconnects, it automatically terminates `vmware.exe` and `vmware-vmx.exe` processes to prevent virtual machines from connecting to the internet without VPN protection.

---

## Features

- Real-time VPN status monitoring.
- Automatic termination of VMware processes when VPN disconnects.
- Windows system tray integration with live status indicators.
- Visual tray icon updates (green for active VPN, red for inactive).
- User-friendly notifications for connection events.

---

## How It Works

1. The script checks all network interfaces using the `` library.
2. It looks for an interface name containing a user-defined keyword (default: `Bitdefender`).
3. If no active VPN interface is found, it:
   - Displays a warning in the system tray.
   - Terminates VMware processes.
4. When the VPN reconnects, VMware processes are allowed to run normally again.

---

## Requirements

- **Operating System:** Windows 10 or later
- **Python:** 3.8+

### Python Packages:

Install dependencies via pip:

```bash
pip install psutil pillow pystray
```

---

## Usage

1. Clone or download this repository.
2. Edit the `VPN_INTERFACE_KEYWORD` variable in `vmware_vpn_guard.py` to match your VPN adapter name (e.g., `"NordVPN"`, `"Bitdefender"`).
3. Run the script:
   ```bash
   python vmware_vpn_guard.py
   ```
4. A system tray icon will appear:
   - 🟢 Green: VPN is active (VMware allowed)
   - 🔴 Red: VPN inactive (VMware blocked)
5. Right-click the tray icon to view status or quit the program.

---

## Configuration

You can customize these constants inside the script:

```python
VPN_INTERFACE_KEYWORD = "Bitdefender"  # The keyword used to detect your VPN
VM_PROCESS_NAMES = ["vmware.exe", "vmware-vmx.exe"]  # VMware processes to kill
CHECK_INTERVAL = 5  # Seconds between checks
```

---

## Disclaimer

Use this script responsibly. Killing VMware processes may result in **data loss** for unsaved work in running virtual machines. Always test the configuration safely before relying on it.

---

## License

This project is provided for personal and educational use only. Commercial redistribution or modification without permission is prohibited.

---

## Author

**Daniel Y.**\
Created on October, 2025.

