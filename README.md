# CHC Ninja Back-End (chcninja-be)
Based on Dash Ninja By Alexandre (aka elbereth) Devilliers

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/f4a2d60364cd4c1cb34c81e23453f62a)](https://www.codacy.com/app/terracoin/chcninja-re?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=terracoin/chcninja-be&amp;utm_campaign=Badge_Grade)
[![Code Climate](https://codeclimate.com/github/terracoin/chcninja-be/badges/gpa.svg)](https://codeclimate.com/github/terracoin/chcninja-be)

Check the running live website at https://overview.terracoin.io

This is part of what makes the CHC Ninja monitoring application.
It contains:
- Private REST API (using PHP and Phalcon framework)

## Requirement:
* You will need a running website, official at https://chcninja.com uses apache2

For the REST API:
* PHP v5.6 with mysqli
* Phalcon v2.0.x (should work with any version)
* MySQL database with CHC Ninja Database (check chcninja-db repository)

## Optional:
* CHC Ninja Control script installed and running (to feed the database through this API)

## Install:
* Go to the root of your website for CHC private API (ex: cd /var/www/chcninja/cmd/)
* Get latest code from github:
```shell
git clone https://github.com/crymesomecrypto/chcninja-be.git
```

* Configure php to answer only to calls to api/index.php rewriting to end-point api/

## Configuration:
The initial idea was to be able to have a central application (chcninja-be) where one or several hub of nodes connect to in order to provide monitoring.

Current implementation takes as assumption that there is only one hub configured (there can be several nodes).

Identification of this app and possible hubs are done with SSL certificates and it was designed to run on IPv6 only.
You need to configure your web server (CHC Ninja official uses apache2) with your CA and create client certificates to trusted hubs to connect to it.

Once the server is configured correctly import the client certificate CN into cmd_hub to give access to that hub (this can be a remote host or ::1). Both the certificate and IPv6 are checked to match and give access.

Rest of documentation is not done yet (if ever).
