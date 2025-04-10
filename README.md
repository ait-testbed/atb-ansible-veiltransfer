Role Name
=========

This role installs the **VeilTransfer server**. For more information, visit the [VeilTransfer GitHub repository](https://github.com/infosecn1nja/VeilTransfer). It includes:

- Installation of **Go 1.22.12** (if necessary).
- Creation of a **Systemd service** to run the VeilTransfer server using the **QUIC protocol**.
- Automatic certificate generation for secure communication.

Requirements
------------

This role requires:

- **Ubuntu** (other Linux distros might work but are not officially supported).
- **Go** version **>= 1.22.12**.

If Go is not installed or is outdated, this role will install or update it to the required version.

Role Variables
--------------

- **`veiltransfer_user`** *(Required)*  
  The user who will install and run the VeilTransfer server. This user **must be supplied** when calling the role.

- **`go_version`** *(Optional)*  
  The version of Go to install. Default is `1.22.12`. Only used if Go is not installed or is outdated.

- **`veiltransfer_repo`** *(Optional)*  
  The URL of the VeilTransfer GitHub repository. Default is `https://github.com/infosecn1nja/VeilTransfer.git`.

- **`veiltransfer_folder_path`** *(Optional)*  
  The folder path for the data transferred by the VeilTransfer server. Default is `/home/{{ veiltransfer_user }}/stolen_data.tar.gz`.


Dependencies
------------

- **Go 1.22.12** or higher to compile VeilTransfer.
- **Systemd** to create a service for the VeilTransfer server.


Example Playbook
----------------

```yaml
---
- name: Install and configure VeilTransfer server
  hosts: servers
  become: true
  vars:
    veiltransfer_user: "veiluser"  # Ensure this user is provided
  roles:
    - role: veiltransfer

License
-------



Author Information
------------------


