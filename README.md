 
# Ansible-Prod-Ready-Directory-Structure & Playbooks
This is my Ansible skeleton. It provide a nice structure to work comfortably with Ansible. You don't need to follow all principes of this structure to use Ansible.

# FIRST VERIFY ..
ansible_distribution_release - ansible all -m setup -a "filter=ansible_distribution*" 
ansible all -m setup -a "filter=*"

SUCCESS => { "ansible_facts": { "ansible_distribution": "Amazon", "ansible_distribution_file_parsed": true, "ansible_distribution_file_path": "/etc/system-release", "ansible_distribution_file_variety": "Amazon", "ansible_distribution_major_version": "NA", "ansible_distribution_release": "NA", "ansible_distribution_version": "(Karoo)" }, "changed": false, "failed": false }

# MAKE SURE YOU SET

```
"ansible_distribution_release" & "ansible_distribution_major_version" . 
BEFORE YOU RUN THE PAYBOOKS !! 
"ansible_distribution": "CentOS" 
"ansible_distribution": "Amazon" 
"ansible_distribution": "Ubuntu" 
"ansible_distribution": "Debian"
```

# Goal and features
The goal of this template is to provide a quick way to start with Ansible. It is a mix of best practices gathered around the web and the result of my own experience. You will find here an extremely modular structure, which should not let the user doubt where to put the correct files. Some advanced topics are covered into the docs folder

# Basically, this structure provides:

- A nice default ansible.cfg file
- A way to organise hosts and groups
- An efficient way to organise variables, depending hosts, groups or environments
- It helps to avoid the recommended messy structure
- Most of files are grouped under directories to avoid confusion
- Provide a nice subset of plugins
- Provide default playbooks to really start quickly your development


# Quick Start
To help you to start quickly, there are few entrey point to have your first playbook working. First, you need to add the targets you want to manage.


# Roles
1. Tomcat
2. Nginix
3. Nginixinc.Nginix (Galaxy role)
4. MongoDB
5. MariaDB
6. NIST_COMPLIANCE (playbook for implementing NIST profile for all servers)

# Playbooks 
ansible-playbook  /opt/ansible-tgs/playbooks/nginix-standalone.yml -vvvv 
 
# File structure
The files structure is organised this way: 
```
.
├── LICENSE
├── README.md                             # Documentation entry point
├── ansible.cfg -> config/ansible.cfg     # Symlink to vagrant config
├── config                              # Configuration directory
│   ├── ansible.cfg                       # Ansible configuration
│   ├── ssh_config                        # SSH configuration
│   ├── tmp                               # Temporary files
│   └── vault_password                    # Default vault file
├── docs                                # Advanced documentation topics
│   ├── skel-start.md
│   └── skel-tips.md
├── inventory                           # Inventory directory
│   ├── dev                           # Dev inventory
|   |    ├── group_vars                          # Group vars directory
|   |    |    ├── all.yml                           
|   |    |    ├── nginix-server                     
|   |    |    ├── apache-servers                        
|   |    |    └── DB-servers                          
|   |    ├── host_vars                           # Host vars directory
|   |    
│   ├── preprod                       # Preprod inventary
│   └── prod                          # Production inventory
├── playbooks                           # Playbook directory
│   ├── 0_local_requirements.yaml         # Configure local system
│   ├── 1_target_test.yml                 # Test targets
│   ├── 2_target_requirements.yml         # Basic configuration of targets
│   └── 3_target_sysadmin.yml             # Advanced confivuration of targets
├── plugins                             # Plugin directory
│   ├── action                            # Action plugins
│   ├── callback                          # Callback plugins
│   ├── connection                        # Connection plugins
│   ├── filter                            # Filter plugins
│   ├── lookup                            # Lookup plugins
│   ├── modules                           # Modules plugins
│   └── vars                              # Vars plugins
└── roles                               # Roles directory
    ├── local                             # Locale roles
    ├── profiles                          # Profile roles
    ├── requirements.yml                  # Vendor roles list
    └── vendors                           # Vendor roles
```

# Compatibility
This skeleton will mainly work with Ansible 2.2. It could run on lower versions, but it has not been tested. Definitely not compatible with 1.x branch. Please checkout the correct branch of this repo to get the matching version.

As this skeleton comes with some python plugins, you may need to install extra Python dependencies if you want to use them:

string_utils: slugify
ipaddr: netaddr
Usually, a simple pip install slugify netaddr should let use those plugins. At this stage, documentation for the plugins is pretty poor, and you may need to read the source code if you want to understand how to use them.

# Releases
Compatibility for Ansible-2.2
Make some clean, stabilise the code
Update the documentation documentation
License
Please read GNU AFFERO GENERAL PUBLIC LICENSE.

 
