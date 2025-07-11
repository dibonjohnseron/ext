# WSL VHDX Compactor

This PowerShell script helps you compact the ext4.vhdx file of your Ubuntu (or Ubuntu-based) WSL distributions to reclaim disk space.

## Features
- Automatically finds the Ubuntu WSL distribution's VHDX file path.
- Logs the VHDX size before and after compacting.
- Runs `wsl --shutdown` and uses `diskpart` to compact the VHDX.
- Shows how much disk space you saved.

## Usage
```
irm https://raw.githubusercontent.com/dibonjohnseron/ext/refs/heads/main/compact-wsl | iex
```
