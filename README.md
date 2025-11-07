# VPN CLI

A simple command-line tool for managing OpenVPN connections on Linux systems. This tool provides an easy-to-use interface for starting, stopping, and managing OpenVPN client connections using systemd.

## Features

- Start, stop, and restart VPN connections
- Check connection status
- Enable/disable VPN at system boot
- View connection logs in real-time
- List all available VPN configurations
- Color-coded output for better readability

## Prerequisites

- Linux system with systemd
- OpenVPN installed
- sudo privileges
- OpenVPN configuration files in `/etc/openvpn/client/`

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd vpn-cli
```

2. Make the script executable:
```bash
chmod +x vpn
```

3. (Optional) Create a symbolic link to use the command system-wide:
```bash
sudo ln -s $(pwd)/vpn /usr/local/bin/vpn
```

## Usage

```bash
vpn <command> <vpn-name>
```

### Commands

| Command | Description |
|---------|-------------|
| `start <name>` | Start OpenVPN connection |
| `stop <name>` | Stop OpenVPN connection |
| `restart <name>` | Restart OpenVPN connection |
| `status <name>` | Show connection status |
| `enable <name>` | Enable VPN to start at boot |
| `disable <name>` | Disable VPN from starting at boot |
| `logs <name>` | Show recent logs (follows log output) |
| `list` | List all available VPN configurations |

### Examples

Start a VPN connection:
```bash
vpn start abc
```

Stop a VPN connection:
```bash
vpn stop abc
```

Check connection status:
```bash
vpn status abc
```

View logs in real-time:
```bash
vpn logs abc
```

List all available VPN configurations:
```bash
vpn list
```

Enable VPN to start automatically at boot:
```bash
vpn enable abc
```

## Configuration

Place your OpenVPN configuration files (`.conf`) in `/etc/openvpn/client/`. The VPN name used in commands should match the configuration filename without the `.conf` extension.

For example, if you have `/etc/openvpn/client/myserver.conf`, use:
```bash
vpn start myserver
```

## How It Works

This tool is a wrapper around systemd's OpenVPN client service (`openvpn-client@.service`). It translates simple commands into the appropriate `systemctl` operations, making VPN management more intuitive.

## License

This project is provided as-is for personal and educational use.
