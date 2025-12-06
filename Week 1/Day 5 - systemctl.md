# Notes - Day 5

## systemctl - System and Service Manager

**Purpose:** Control the systemd system and service manager in Linux

### Service Management Commands

- `systemctl status service_name` - Check if a service is running, stopped, or failed
- `systemctl start service_name` - Start a service immediately (requires admin rights)
- `systemctl stop service_name` - Stop a running service (requires admin rights)
- `systemctl restart service_name` - Restart a service (useful after config changes, requires admin rights)
- `systemctl enable service_name` - Enable service to start automatically on boot (requires admin rights, doesn't start immediately)
- `systemctl disable service_name` - Disable service from starting on boot (requires admin rights)
- `systemctl is-enabled service_name` - Check if a service is enabled to start on boot

### Listing Services and Sockets

- `systemctl list-units --type=service` - List all active services
- `systemctl list-sockets` - List sockets available for interprocess communication (IPC)
- `systemctl --show-types list-sockets` - Show socket types
- `systemctl --show-types list-sockets --all` - Show all sockets including inactive ones

### System Control Commands

- `systemctl poweroff` - Shut down the system
- `systemctl reboot` - Reboot the system
- `systemctl -i reboot` - Reboot ignoring logged-in users

### Viewing Logs with journalctl

- `journalctl -u service_name` - View logs for a specific service
- `journalctl -u service_name -n 50` - View last 50 log entries for a service

### Process Management

- `ps aux | grep service_name` - Check running processes for a specific service

### Key Points to Remember

- **Enable vs Start:** `enable` sets service to start on boot but doesn't start it now; `start` runs it immediately
- Most service management commands require admin/sudo privileges
- Use `restart` after making configuration changes to apply them
- Common services to practice with: ssh, sshd, nginx, apache2