# CiscoIOSFacts
Ansible Playbooks to gather and transform Cisco IOS Facts into human readable documentation automatically

## Written by John Capobianco

Using the Ansible ios_facts module these playbooks first gather facts, displays the facts to the screen, saves RAW JSON, Nice JSON, Nice YAML, CSV, Markdown, and interactive HTML Mind Map files from the returned stateful data. 

### Prerequisites

1) Install Ansible

    $ pip install --user ansible

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
    
Run CiscoDistFacts.yml or CiscoAccessFacts.yml after customizing hosts and gather facts and create reports for those logical layer.s

#### DEVELOPMENT NOTES 
Developed with VS Code, Ansible, CentOS
Tested at vertical scale (1+n devices in the CORE / DIST / ACCESS groups) and horizontally against Cisco 2960,3560,3750,3850,4500,6500,9300 hardware platforms.
