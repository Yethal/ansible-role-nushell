# Ansible Role: Nushell

Installs Nushell on Linux and macOS systems

## Requirements

None.

## Role Variables

Available variables are listed below:

|Variable|Descriprion|Default|
|-|-|-|
|install_path|Directory where nushell binary will be stored|/usr/local/bin|
|nushell_version|either 'latest' or version tag|latest|

## Dependencies

None.

## Local testing
Run `vagrant up` from within root directory of the project to set up Ubuntu Server VM and run the role inside.

Alternatively run `pip install -r requirements.txt` and run automated tests via molecule by running `molecule test`

## Example Playbook

    - hosts: servers
      become: false # role should run as user you wish to install nushell for
      roles:
         - yethal.nushell

## License

BSD

## Author Information

[yethal](https://github.com/Yethal)
