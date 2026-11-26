# WSL VHDX Compactor

This PowerShell script compacts the VHDX files for the first Ubuntu (or Ubuntu-based) WSL distribution and Docker Desktop's WSL data disk to reclaim disk space.

## Features
- Automatically finds the Ubuntu WSL distribution's VHDX file path.
- Finds Docker's data disk at `%LOCALAPPDATA%\Docker\wsl\disk\docker_data.vhdx`, or uses `DOCKER_VHDX_PATH` if set.
- Logs the VHDX size before and after compacting.
- Runs `wsl --shutdown` and uses `diskpart` to compact the VHDX.
- Shows how much disk space you saved.

## Usage

Quit Docker Desktop completely, then run PowerShell as administrator:

```powershell
irm https://raw.githubusercontent.com/dibonjohnseron/ext/refs/heads/main/compact-wsl | iex
```

If Docker's data disk is in a different location (including older `docker-desktop-data` installations), set its full path first:

```powershell
$env:DOCKER_VHDX_PATH = 'D:\path\to\docker_data.vhdx'
irm https://raw.githubusercontent.com/dibonjohnseron/ext/refs/heads/main/compact-wsl | iex
```

If the default Docker disk is not found, the script warns and compacts only Ubuntu. It shuts down all WSL distributions and does not restart Docker Desktop.

The script reports errors in the PowerShell window rather than closing it. Compaction can take a while; wait for the total space saved or an error before closing the window.
