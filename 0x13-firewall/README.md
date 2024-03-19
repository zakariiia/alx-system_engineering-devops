# Firewall

In this project, I used `ufw` to configure firewalls on my issued web servers.

## Tasks :page_with_curl:

* **0. Block all incoming traffic but**
  *  Bash script that installs a `ufw` firewall to block all incoming traffic except for
  ports `22`, `443` and `80` on a web server.

* **1. Port forwarding**
  *  `ufw` configuration file that
  configures a firewall to redirect port `8080/TCP` to port `80/TCP`.
