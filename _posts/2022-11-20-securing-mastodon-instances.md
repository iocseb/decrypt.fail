---
title: Securing Mastodon Instances
date: 2022-11-20
tags: [decentralization, infosec, older]
---

This post tries to consolidate information available across multiple websites on the
topic of securing a Mastodon server. (Where available, I linked to
[archive.org](http://archive.org)'s wayback-machine for long-term access.)

## Basic Server Security

- Use an OS that is supported through frequent security updates
- Configure automated security updates (instructions for [Ubuntu/Debian](https://web.archive.org/web/20220715173452/https://haydenjames.io/how-to-enable-unattended-upgrades-on-ubuntu-debian/))
- Use public key authentication for SSH ([guide](https://web.archive.org/web/20220607035429/https://www.linode.com/docs/guides/use-public-key-authentication-with-ssh/))
- Disable password based authentication for SSH (instructions for [Ubuntu](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Disable_Password_Authentication))
- Install Fail2Ban (instructions for [Ubuntu](https://web.archive.org/web/20220707210728/https://linuxize.com/post/install-configure-fail2ban-on-ubuntu-20-04/))
- Enable the host firewall and only allow incoming traffic on TCP ports 443, 80, and 22 (instructions for [iptables](https://github.com/packetbiral/mastodon-documentation/blob/master/Running-Mastodon/Security-Guide.md))
- Properly secure access to your hosting provider's backend with strong passwords and 2FA

## Mastodon Admin Account

- Don't use the instance's admin account as your day-to-day micro-blogging account! (Create separate accounts instead.)
- Use a random password with at least 16 characters for the admin account (store it in a password manager)
- Enable 2FA on the admin account

## Advanced Security Considerations

- Use a [bastion host](https://en.wikipedia.org/wiki/Bastion_host) (aka jump-host) to access the Mastodon server via SSH, and restrict SSH access to the bastion host on the Mastodon server's host firewall
- Use a [cloud firewall](https://www.linode.com/docs/products/networking/cloud-firewall/get-started/) from your hosting provider to only temporarily allow SSH access from your IP address
- Create a free account with [CrowdSec](https://www.crowdsec.net/) and add the Mastodon server as an instance to auto-block (crowd-sourced) known bad IP addresses
- Test the server's SSL/TLS configuration ([Qualys SSL Test](https://www.ssllabs.com/ssltest/)) and disable weak ciphers ([NginX hardening guide](https://web.archive.org/web/20220624022129/https://geekflare.com/nginx-webserver-security-hardening-guide/))
- Put a WAF (Web Application Firewall) in front of the Mastodon server (FOSS example: [ModSecurity](https://github.com/SpiderLabs/ModSecurity); other options are WAF-as-a-service from Cloudflare or any of the hyper-scalers)
- Install an EDR agent on the Mastodon server (FOSS example: [Wazuh](https://wazuh.com/))
- Restrict egress traffic through a headless [OpenSnitch](https://github.com/evilsocket/opensnitch) installation

*Some relevant links:*

- *<https://docs.joinmastodon.org/admin/prerequisites/>*
- *<https://haydenjames.io/how-to-enable-unattended-upgrades-on-ubuntu-debian/>*
- *<https://www.linode.com/docs/guides/use-public-key-authentication-with-ssh/>*
- *<https://linuxize.com/post/install-configure-fail2ban-on-ubuntu-20-04/>*
- *<https://github.com/packetbiral/mastodon-documentation/blob/master/Running-Mastodon/Security-Guide.md>*
- *<https://geekflare.com/nginx-webserver-security-hardening-guide/>*
