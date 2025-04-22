# Ansible role: VeilTransfer

This role installs the **VeilTransfer server**. For more information, visit the [VeilTransfer GitHub repository](https://github.com/infosecn1nja/VeilTransfer). It includes:

- Installation of **Go 1.22.12** (if necessary).
- Creation of a **Systemd service** to run the VeilTransfer server using the **QUIC protocol**.
- Automatic certificate generation for secure communication.

## Requirements

This role requires:

- **Ubuntu** (other Linux distros might work but are not officially supported).
- **Go** version **>= 1.22.12**.

If Go is not installed or is outdated, this role will install or update it to the required version.

## Role Variables

| Variable                   | Required | Default                                             | Description                                                                             |
| -------------------------- | -------- | --------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `veiltransfer_user`        | Yes      | `None`                                              | The user who will install and run the VeilTransfer server.                              |
| `go_version`               | No       | `1.22.12`                                           | The version of Go to install. Only used if Go is not installed or is outdated.          |
| `veiltransfer_repo`        | No       | `https://github.com/infosecn1nja/VeilTransfer.git`  | The URL of the VeilTransfer GitHub repository to clone.                                 |
| `veiltransfer_received_file` | No       | `stolen_data.tar.gz` | The destination for received data transfers. |


## Dependencies

- **Go 1.22.12** or higher to compile VeilTransfer (gets installed if Go is not installed or is outdated )
- **Systemd** to create a service for the VeilTransfer server.


## Example Playbook

```yaml
---
- name: Install and configure VeilTransfer server
  hosts: servers
  become: true
  roles:
    - role: veiltransfer
      vars:
        veiltransfer_user: "veiluser"

```

## License

GPL-3.0

## Author Information

Thorina Boenke (https://www.ait.ac.at)


