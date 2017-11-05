# Week 9 Project: Honeypot

Time spent: **15** hours spent in total

## Report
### Setup
A honeypot was set up following Modern Honey Network (MHN)'s multi-snort honeypot sensor management using a network of virtual machines (set up using Vagrant and VirtualBox), centralized server management site, Snort installations, and stealthy Dinoaeas. Conpot, Dionaea, Kippo, and Snort were the intrusion detection softwares used. The central server management site was a Python Flask application that exposed HTTP API which honeypots could use to connect and register, download deploy scripts and Snort rules, and send intrusion detection logs. The site also allowed sysadmins to manage Snort rules (enable/disable, download, etc.) as well as view a list of new attacks.

### Installation
* Install Git
   ```
   $ sudo apt-get update
   $ sudo apt-get install git -y
   ```
* Install the MHN admin application
   ```
   $ cd /opt
   $ sudo git clone https://github.com/RedolentSun/mhn.git
   $ cd mhn
   $ sudo ./install.sh
   ```
* Check the number of services that are running
  ```
  $ sudo supervisorctl status 
  ```
* Using MHN to deploy honeypot
  1. Login to the MHN server webapp.
  2. Click the "Deploy" link in the upper-left corner. 
  3. Select the type of honeypot from the dropdown menu.
  4. Copy the deployment command.
  5. Run this command as root after logging to a honeypot server.
* Splunk and ArcSight integration
  ```
  $ sudo ./install_hpfeeds-logger-splunk.sh
  $ sudo ./install_hpfeeds-logger-arcsight.sh
  ```

### Summary
ACK, Connect, Maimon, and TCP SYN scans were undertaken using the Nmap security scanner. Additionally, open ports were probed to determine version and service information as well as for OS detection.

* Number of attacks: 81
* Most attacked IP: 10.254.254.1 (5 attacks)
* Most attacked port: 80 (5 times)
* Most attacked honeypot: dionaea (6 attacks)
* Most attacked sensor: mhn-honeypot (5 attacks)

## License
Modern Honeypot Network

Copyright (C) 2017 - Anomali, Inc.

This program free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA
