# Ansible Role: Common Proxy

This role manages proxy settings of Linux systems.

[![Ansible Role: Common Proxy](https://img.shields.io/ansible/role/51252?style=flat-square)](https://galaxy.ansible.com/thorian93/ansible_role_common_proxy)
[![Ansible Role: Common Proxy](https://img.shields.io/ansible/quality/51252?style=flat-square)](https://galaxy.ansible.com/thorian93/ansible_role_common_proxy)
[![Ansible Role: Common Proxy](https://img.shields.io/ansible/role/d/51252?style=flat-square)](https://galaxy.ansible.com/thorian93/ansible_role_common_proxy)

## Here be Dragons!

This role was just created and I can and will not guarantee that it works properly! Use at your own risk! But also feel free to share any findings.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: ansible-role-common-proxy
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    common_proxy_git_configure: false
    common_proxy_profile_configure: false
    common_proxy_wget_configure: false
    common_proxy_systemd_configure: false

Choose which parts of the system should be configured with a proxy.

    common_proxy_server: 127.0.0.1

Configure which proxy server to use.

    common_proxy_port: 8080

Configure the proxy port.

    common_proxy_exceptions: "localhost, 127.0.0.0/8, ::1"

Configure proxy exceptions like e.g. local hosts.

    apt_proxy_server: "{{ common_proxy_server }}"
    apt_proxy_port: "{{ common_proxy_port }}"
    apt_proxy_username: ""
    apt_proxy_password: ""
    apt_proxy_exceptions: [ ]

Configure proxy for apt / aptitude. Default to common_proxy. Set to blank to remove.
    dnf_proxy_server: "{{ common_proxy_server }}"
    dnf_proxy_port: "{{ common_proxy_port }}"
    dnf_proxy_username: ""
    dnf_proxy_password: ""

Configure yum or dnf proxy. Set to blank to remove.

## Dependencies

None.

## OS Compatibility

This role ensures that it is not used against unsupported or untested operating systems by checking, if the right distribution name and major version number are present in a dedicated variable named like `<role-name>_stable_os`. You can find the variable in the role's default variable file at `defaults/main.yml`:

    role_stable_os:
      - Debian 10
      - Ubuntu 18
      - CentOS 7
      - Fedora 30

If the combination of distribution and major version number do not match the target system, the role will fail. To allow the role to work add the distribution name and major version name to that variable and you are good to go. But please test the new combination first!

Kudos to [HarryHarcourt](https://github.com/HarryHarcourt) for this idea!

## Example Playbook

    ---
    - name: "Run role."
      hosts: all
      become: yes
      roles:
        - ansible-role-common-proxy

## Contributing

Please feel free to open issues if you find any bugs, problems or if you see room for improvement. Also feel free to contact me anytime if you want to ask or discuss something.

## Disclaimer

This role is provided AS IS and I can and will not guarantee that the role works as intended, nor can I be accountable for any damage or misconfiguration done by this role. Study the role thoroughly before using it.

## License

MIT

## Author Information

This role was created in 2020 by [Thorian93](http://thorian93.de/).
