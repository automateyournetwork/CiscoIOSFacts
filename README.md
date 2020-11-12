# CiscoIOSFacts

Ansible Playbooks to gather and transform Cisco IOS Facts into human readable documentation automatically

[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/automateyournetwork/CiscoIOSFacts)

## Written by John Capobianco

Using the Ansible ios_facts module these playbooks first gather facts, displays the facts to the screen, saves RAW JSON, Nice JSON, Nice YAML, CSV, Markdown, and interactive HTML Mind Map files from the returned stateful data. 

### Prerequisites

1) Install Ansible

    $ pip install --user ansible

    Centos:

    yum install python

    yum install ansible

2) Check version of Ansible

    $ansible --version

    ansible 2.9.1

3) Install JMESPATH

pip install --user jmespath

4) Install node.js and npm

curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

5) Clone the Repository

    git clone https://github.com/automateyournetwork/CiscoIOSFacts.git

### CUSTOMIZE

In the hosts file replace the dummy CORE / DISTRIBUTION / ACCESS hostnames with your own hostnames. 
Ensure Linux host running Ansible playbook can SSH into targetted hosts using prompted username and password. 

### Run the playbook

After updating the hosts file with the proper hostnames run the playbook.

cd CiscoIOSFacts

cd playbooks

ansible-playbook CiscoCoreFacts.yml

<answer prompts for credentials> 

<playbook gathers facts>

<playbook creates files>

cd ..

cd documentation/CAMPUS/FACTS/CORE/

ls

Review files

Run CiscoDistFacts.yml or CiscoAccessFacts.yml after customizing hosts and gather facts and create reports for those logical layers.

### Topology

![Toplogy](/topology.png?raw=true")

### Output files

The following files are created per host:

IOS Facts - General 

(inventory_hostname)_IOS_Facts_RAW.json - ALL RAW JSON returned data

(inventory_hostname)_IOS_Facts_Nice.json - All JSON returned data filtered to Nice JSON

(inventory_hostname)_IOS_Facts.yml - All returned data in Nice YAML

(inventory_hostname)_IOS_facts.csv - Custom fields in CSV

(inventory_hostname)_IOS_facts.md - Custom fields in Markdown

(inventory_hostname)_IOS_facts.html - Custom fields interactive HTML mind map

IOS Facts - IP Addresses

(inventory_hostname)_IP_facts.csv - All IP addresses in CSV

(inventory_hostname)_IP_facts.md - All IP addresses in Markdown

(inventory_hostname)_IP_facts.html - All IP Address interactive HTML mind map

IOS Facts - Interfaces

Includes physical interfaces, SVIs, port-channels, subinterfaces, tunnel interfaces, and loopback interfaces

(inventory_hostname)_Interface_facts.csv - All interfaces in CSV

(inventory_hostname)_Interface_facts.md - All interfaces in Markdown

(inventory_hostname)_Interface_facts.html - All interfaces interactive HTML mind map

IOS Facts - Neighbors

Includes all CDP detected neighbors

(inventory_hostname)_Neighbor_facts.csv - All neighbors in CSV

(inventory_hostname)_Neighbor_facts.md - All neighbors in Markdown

(inventory_hostname)_Neighbor_facts.html - All neighbors interactive mind map

#### DEVELOPMENT NOTES

Developed with VS Code, Ansible, CentOS

Tested at vertical scale (1+n devices in the CORE / DIST / ACCESS groups) and horizontally against:

Cisco Catalyst 2960,3560,3750,3850,4500,6500,9300 hardware platforms
