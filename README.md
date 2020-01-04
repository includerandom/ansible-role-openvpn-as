openvpn_as
==========

[![Build Status](https://travis-ci.org/kbrebanov/ansible-openvpn_as.svg?branch=master)](https://travis-ci.org/kbrebanov/ansible-openvpn_as)

Installs and configures OpenVPN Access Server

Requirements
------------

This role requires Ansible 1.9 or higher.

Role Variables
--------------

| Name                                                        | Default                                                                                                                                                                                                               | Description                                                                                                                                                  |
|:------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| openvpn_as_version                                          | 2.1.2                                                                                                                                                                                                                 | Version of OpenVPN Access Server to install                                                                                                                  |
| openvpn_as_ubuntu_trusty_sha256sum                          | d9d539e7a497ed36a15100a8f24e4fcb42b98581bfc5d79e0bb07b7e4c4a608b                                                                                                                                                      | SHA 256 sum of Ubuntu Trusty package                                                                                                                         |
| openvpn_as_ubuntu_xenial_sha256sum                          | f00cf38d9fb51beb66ddb9d67b508952d9170b6d94e821465a09d58fb14ce475                                                                                                                                                      | SHA 256 sum of Ubuntu Xenial package                                                                                                                         |
| openvpn_as_password                                         | $6$j8B0A1aiU$53BF5A6qO74IDJWTDqgaafnBar1c.LOKK7sdBxwXJY/K/I/XUFAWNsfm78dI9YBDPTHJlmaZoE.QFg.3DEobO1 (openvpn by sha512sum)                                                                                            | Password for openvpn admin user                                                                                                                              |
| openvpn_as_admin_ui_https_ip_address                        | "{{ ansible_default_ipv4.interface }}"                                                                                                                                                                                | The IP address for the Admin Web Server                                                                                                                      |
| openvpn_as_admin_ui_https_port                              | 943                                                                                                                                                                                                                   | The port for the Admin Web Server                                                                                                                            |
| openvpn_as_connect                                          | true                                                                                                                                                                                                                  | Enable AS Connect functionality                                                                                                                              |
| openvpn_as_cs_admin_only                                    | false                                                                                                                                                                                                                 | Restrict Client Web Server access to Access Server administrators                                                                                            |
| openvpn_as_cs_auto_generate                                 | true                                                                                                                                                                                                                  | If enabled, automatically generate a client configuration when a client logs into the site and successfully authenticates                                    |
| openvpn_as_cs_cws_ui_offer_android                          | true                                                                                                                                                                                                                  | Offer Android client                                                                                                                                         |
| openvpn_as_cs_cws_ui_offer_autologin                        | true                                                                                                                                                                                                                  | Offer autologin profile                                                                                                                                      |
| openvpn_as_cs_cws_ui_offer_ios                              | true                                                                                                                                                                                                                  | Offer iOS client                                                                                                                                             |
| openvpn_as_cs_cws_ui_offer_linux                            | true                                                                                                                                                                                                                  | Offer Linux client                                                                                                                                           |
| openvpn_as_cs_cws_ui_offer_mac                              | true                                                                                                                                                                                                                  | Offer Mac OS X client                                                                                                                                        |
| openvpn_as_cs_cws_ui_offer_server_locked                    | false                                                                                                                                                                                                                 | Offer server-locked profile                                                                                                                                  |
| openvpn_as_cs_cws_ui_offer_user_locked                      | true                                                                                                                                                                                                                  | Offer user-locked profile                                                                                                                                    |
| openvpn_as_cs_cws_ui_offer_win                              | true                                                                                                                                                                                                                  | Offer Windows client                                                                                                                                         |
| openvpn_as_cs_https_ip_address                              | "{{ ansible_default_ipv4.interface }}"                                                                                                                                                                                | The IP address for the Client Web Server                                                                                                                     |
| openvpn_as_cs_https_port                                    | 943                                                                                                                                                                                                                   | The port for the Client Web Server                                                                                                                           |
| openvpn_as_cs_ssl_reneg                                     | false                                                                                                                                                                                                                 | Support SSL/TLS renegotiation                                                                                                                                |
| openvpn_as_cs_tls_version_min                               | 1.2                                                                                                                                                                                                                   | Minimum SSL/TLS protocol version accepted by Access Server web server (default, ssl2, ssl3, 1.0, 1.1, 1.2)                                                   |
| openvpn_as_host_name                                        | "{{ ansible_default_ipv4.address }}"                                                                                                                                                                                  | Hostname or IP address of VPN server                                                                                                                         |
| openvpn_as_iptables_append                                  | false                                                                                                                                                                                                                 | Append OpenVPN Access server rules instead of prepending                                                                                                     |
| openvpn_as_iptables_web                                     | true                                                                                                                                                                                                                  | If true, open up web ports on the firewall using iptables                                                                                                    |
| openvpn_as_iptables_vpn_disable_filter                      | false                                                                                                                                                                                                                 | Disable OpenAccess server from modifying iptables filter rules                                                                                               |
| openvpn_as_iptables_vpn_disable_mangle                      | false                                                                                                                                                                                                                 | Disable OpenAccess server from modifying iptables mangle rules                                                                                               |
| openvpn_as_iptables_vpn_disable_nat                         | false                                                                                                                                                                                                                 | Disable OpenAccess server from modifying iptables nat rules                                                                                                  |
| openvpn_as_sa_company_name                                  | OpenVPN Technologies, Inc.                                                                                                                                                                                            | The company name will be shown in the UI                                                                                                                     |
| openvpn_as_sa_logo_image_file                               | ''                                                                                                                                                                                                                    | Path to custom logo image file                                                                                                                               |
| openvpn_as_sa_show_c2s_routes                               | true                                                                                                                                                                                                                  | Enable client gateway                                                                                                                                        |
| openvpn_as_sa_ssl_lib                                       | openssl                                                                                                                                                                                                               | SSL library to use (openssl or polarssl)                                                                                                                     |
| openvpn_as_vpn_client_config_directives                     | []                                                                                                                                                                                                                    | Additional OpenVPN client config directives                                                                                                                  |
| openvpn_as_vpn_client_routing_inter_client                  | false                                                                                                                                                                                                                 | Enable or disable packet routing between clients                                                                                                             |
| openvpn_as_vpn_client_routing_reroute_dns                   | false                                                                                                                                                                                                                 | Push DNS servers to clients                                                                                                                                  |
| openvpn_as_vpn_client_routing_reroute_gw                    | false                                                                                                                                                                                                                 | Re-route all client traffic through the VPN                                                                                                                  |
| openvpn_as_vpn_client_routing_superuser_c2c_access          | false                                                                                                                                                                                                                 | Allow VPN users with Administrator privilege to access all VPN client IP addresses                                                                           |
| openvpn_as_vpn_daemons                                      | [{client_netmask_bits: 20, client_network: 172.27.224.0, listen_ip_address: "{{ ansible_default_ipv4.interface }}", listen_port: 443, listen_protocol: tcp, server_ip_address: "{{ ansible_default_ipv4.address }}"}] | VPN server network settings                                                                                                                                  |
| openvpn_as_vpn_general_osi_layer                            | 3                                                                                                                                                                                                                     | VPN tunneling topology (2: Layer 2 ethernet bridging, 3: Layer 3 routing/NAT)                                                                                |
| openvpn_as_vpn_server_config_directives                     | []                                                                                                                                                                                                                    | Additional OpenVPN server config directives                                                                                                                  |
| openvpn_as_vpn_server_daemon_enable                         | true                                                                                                                                                                                                                  | Enable VPN server daemon                                                                                                                                     |
| openvpn_as_vpn_server_daemon_tcp_port                       | 943                                                                                                                                                                                                                   | VPN server TCP port                                                                                                                                          |
| openvpn_as_vpn_server_daemon_udp_port                       | 1194                                                                                                                                                                                                                  | VPN server UDP port                                                                                                                                          |
| openvpn_as_vpn_server_dhcp_option_adapter_domain_suffix     | ''                                                                                                                                                                                                                    | Setting a default suffix will enable Windows clients to resolve host names to FQDN names                                                                     |
| openvpn_as_vpn_server_dhcp_option_dns_0                     | ''                                                                                                                                                                                                                    | Primary DNS server to push to clients                                                                                                                        |
| openvpn_as_vpn_server_dhcp_option_dns_1                     | ''                                                                                                                                                                                                                    | Secondary DNS server to push to clients                                                                                                                      |
| openvpn_as_vpn_server_dhcp_option_domains                   | []                                                                                                                                                                                                                    | List of internal domains that clients will resolve through the AS-pushed DNS server(s)                                                                       |
| openvpn_as_vpn_server_duplicate_cn                          | true                                                                                                                                                                                                                  | Allow multiple concurrent VPN connections for a user                                                                                                         |
| openvpn_as_vpn_server_google_auth_enable                    | false                                                                                                                                                                                                                 | Require that users provide a Google Authenticator one-time password for every VPN login                                                                      |
| openvpn_as_vpn_server_group_pool                            | ['172.27.240.0/20']                                                                                                                                                                                                   | When a group does not have a specific Dynamic IP Address pool setting, the dynamic IP address pool for the group will be allocated from this list of subnets |
| openvpn_as_vpn_server_routing_allow_private_nets_to_clients | true                                                                                                                                                                                                                  | Allow access from private subnets to all VPN client IP addresses and subnets                                                                                 |
| openvpn_as_vpn_server_routing_gateway_access                | true                                                                                                                                                                                                                  | Allow clients to access network services on the VPN gateway IP address                                                                                       |
| openvpn_as_vpn_server_routing_private_access                | nat                                                                                                                                                                                                                   | Allow VPN clients access to private subnets (non-public networks on the server side) (no, nat, route)                                                        |
| openvpn_as_vpn_server_routing_private_networks              | []                                                                                                                                                                                                                    | List of private subnets that all clients should have access to                                                                                               |
| openvpn_as_vpn_server_routing_routed_subnets                | []                                                                                                                                                                                                                    | List of private subnets which should be reachable via routing instead of NAT                                                                                 |
| openvpn_as_vpn_server_static_netmask_bits                   | 24                                                                                                                                                                                                                    | Number of bits in static netmask                                                                                                                             |
| openvpn_as_vpn_server_static_network                        | ''                                                                                                                                                                                                                    | Any static VPN IP addresses specified for particular users must be within this network                                                                       |
| openvpn_as_vpn_server_tls_version_min                       | 1.2                                                                                                                                                                                                                   | Minimum TLS protocol version accepted by OpenVPN server (default, 1.0, 1.1 or 1.2)                                                                           |
| openvpn_as_vpn_tls_refresh_interval                         | 360                                                                                                                                                                                                                   | TLS sessions are re-negotiated at this specified interval (in minutes)                                                                                       |
| openvpn_as_xmlrpc_relay_level                               | 1                                                                                                                                                                                                                     | XML-RPC/REST API (0: Disable API, 1: Enable limited API, 2: Enable complete API)                                                                             |
| openvpn_as_auth_module_type                                 | pam                                                                                                                                                                                                                   | Configure Primary Authentication. Default auth is **pam**, but you can switch to **ldap**, **local** or **radius**                                           |
| openvpn_as_vpn_server_routing_private_access                | nat                                                                                                                                                                                                                   | VPN clients can have access to private subnets (non-public networks on the server side). You can set: **none**, **nat** or **route**                         |
| openvpn_as_ssl_certificate                                  | none                                                                                                                                                                                                                  | Define your ssl certificate                                                                                                                                  |
|   ca_bundle                                                 | none                                                                                                                                                                                                                  | Put here path to ca_bunlde (aka letsecrypt fullchain.pem)                                                                                                    |
|   cert                                                      | none                                                                                                                                                                                                                  | Put here path to ca_bunlde (aka letsecrypt cert.pem)                                                                                                         |
|   priv_key                                                  | none                                                                                                                                                                                                                  | Put here path to privkey (aka letsecrypt privkey.pem)                                                                                                        |
| openvpn_as_auth_ldap_bind_dn                                | "cn=UserAD, DC=example, DC=net"                                                                                                                                                                                       | Put here ldap path to user                                                                                                                                   |
| openvpn_as_auth_ldap_bind_pw                                | "UserPasswor"                                                                                                                                                                                                         | Put here ldap path user password                                                                                                                             |
| openvpn_as_auth_ldap_add_req                                | none                                                                                                                                                                                                                  | Additional LDAP Requirement filter memberOf or uniquemember                                                                                         |

Dependencies
------------

None

Example Playbook
----------------


Install OpenVPN Access Server
```yaml
- hosts: all
  roles:
    - kbrebanov.openvpn_as
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
