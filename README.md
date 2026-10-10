\# Lab 00 – Hardware Inventory



| What | Value | Where I got it |

|------|-------|----------------|

| CPU model | AMD Ryzen 5 3550H with Radeon Vega Mobile Gfx | Get-CimInstance Win32\_Processor |

| Cores | 4 | Get-CimInstance Win32\_Processor |

| Threads | 8 | Get-CimInstance Win32\_Processor |

| Total RAM | 8 GB | Get-CimInstance Win32\_PhysicalMemory |

| RAM modules | 1 | Get-CimInstance Win32\_PhysicalMemory |

| RAM speed | 2667 MHz | Get-CimInstance Win32\_PhysicalMemory |

| Disk model | 8589934592 | Get-PhysicalDisk |

| Disk type | SSD NV | Get-PhysicalDisk |

| Free space on VM volume | 410.38 GB | Get-Volume |

| Firmware type | UEFI | Confirm-SecureBootUEFI |

| Firmware version and date | v1.12 11/5/2020 5:00:00 am | Get-CimInstance Win32\_BIOS |

| Virtualization enabled | true | Get-CimInstance Win32\_Processor |



\## Virtualization

Virtualization is enabled (VirtualizationFirmwareEnabled = True)



\## What did not work

Confirm-SecureBootUEFI gave an error, so I used Get-ComputerInfo instead

