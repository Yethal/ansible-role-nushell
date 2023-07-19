# Ansible Role: Nushell

Installs Nushell on Linux and macOS systems

## Requirements

None.

## Role Variables

Available variables are listed below:
For more information about variables marked with an asterisk please read the Caveats section

| Variable               | Description                                                     | Default             |
| ---------------------- | --------------------------------------------------------------- | ------------------- |
| nushell_binary_path    | Directory where nushell binary will be stored                   | /usr/local/bin      |
| nushell_version        | either 'latest' or version tag                                  | latest              |
| config_url             | url ansible should download config.nu file from                 | nushell preset file |
| env_url                | url ansible should download env.nu file from                    | nushell preset file |
| login_url              | url ansible should download login.nu file from                  | nushell preset file |
| set_shell              | whether ansible should set nu as default shell of the user\*    | false               |
| install_plugins        | whether ansible should install bundled plugins                  | true                |
| install_configs        | whether ansible should install config files                     | true                |
| overwrite_configs      | whether ansible should overwrite config files on update         | true                |
| plugins                | which plugins should be registered by default                   | all plugins         |
| add_to_profile         | whether ansible should add path to nu to .profile\*             | false               |
| disable_banner         | whether built-in nushell banner should be disabled              | false               |
| nu_users               | List of users for which config and plugins should be registered | []                  |
| add_hostname_to_prompt | Whether inventory hostname should be added to default prompt    | false               |
| clear_login_file       | Whether login.nu should be cleared of all non-commented lines   | false               |

## Plugin installation

`plugins` field should be a list of names

## Caveats

Setting user shell to nushell breaks Ansible ssh connection therefore it is not recommended to set `set_shell` parameter to true unless you're using Ansible to provision your local machine or you have a separate user for running Ansible as. As a workaround you can set `add_to_profile` parameter to true which instead will add nushell to autostart for interactive sessions while maintaining compatibility with Ansible

## Dependencies

None.

## Local testing

Alternatively run `pip install -r requirements.txt` and run automated tests via molecule by running `molecule test --all`

## Example Playbook

    - hosts: servers
      roles:
         - yethal.nushell
      vars:
        add_to_profile: true
        disable_banner: true
        nu_users:
            - "{{ ansible_env.SUDO_USER }}"

## License

BSD

## Author Information

[yethal](https://github.com/Yethal)
