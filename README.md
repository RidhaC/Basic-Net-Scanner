# Network Scanner

A command-line based tool that helps you analyze hosts and services on a network using multiple scan techniques. It's built for system administrators and cybersecurity professionals to evaluate network configurations and identify potential risks.

## Features

- **ICMP Ping Sweep**: Detect live hosts via ICMP echo requests.
- **TCP Port Scanning**: Reveal open ports and detect running services.
- **ARP Discovery**: Identify devices on the local subnet using ARP.
- **Flexible Scan Modes and Timeouts**: Run quick scans or deep assessments with custom timeouts.
- **Port Selection and Ranges**: Specify individual ports or port ranges to scan.
- **Clear, Detailed Output**: View structured and informative scan results.

## Requirements

- **Python 3.6+**: Ensure Python is properly installed.
- **Scapy >= 2.5.0**: Used for crafting and sending packets.
- **Root/Admin Access**: Necessary for certain operations involving raw sockets.

## Installation

1. **Clone the Repository**:

```bash
git clone https://github.com/RidhaC/network-scanner.git
cd network-scanner
```

2. **Install Dependencies**:

```bash
pip install -r requirements.txt
```

## Usage

Run the scanner with the following format:

```bash
python src/main.py <target> [options]
```

### Example Commands

- **Run all scan types on a single IP**:

```bash
python src/main.py 192.168.1.1
```

- **Only ICMP (Ping) scan**:

```bash
python src/main.py 192.168.1.1 -t icmp
```

- **Scan selected ports**:

```bash
python src/main.py 192.168.1.1 -p 22,80,443
```

- **Scan a port range**:

```bash
python src/main.py 192.168.1.1 -p 1-1024
```

- **ARP scan on a subnet**:

```bash
python src/main.py 192.168.1.0/24 -t arp
```

### Command-Line Arguments

- `target`: IP address or CIDR range to scan (**required**)
- `-t`, `--type`: Type of scan to run (`icmp`, `tcp`, `arp`, or `all`) – default: `all`
- `-p`, `--ports`: Specific ports or port ranges (e.g. `80,443` or `20-25`)
- `-T`, `--timeout`: Response timeout per scan in seconds – default: `2`

## Directory Structure

```
network-scanner/
├── src/
│   ├── main.py         # CLI interface
│   └── scanner.py      # Scanning logic
├── tests/              # Test scripts
├── docs/               # Optional documentation
├── requirements.txt    # Python libraries
└── README.md           # Project instructions
```

## Security Notice

- **Authorization Required**: Use this tool only on networks you have permission to scan.
- **May Trigger Alerts**: Scanning can be flagged by intrusion detection/prevention systems.
- **Some Scans May Fail**: Firewalls or host protections may block ICMP, TCP, or ARP traffic.
- **Requires Elevated Privileges**: Depending on OS, some scan types need admin/root access.
