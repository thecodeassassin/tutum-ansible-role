# Tutum agent Ansible playbook role

## Synopsis

This role allows you to automate installing a tutum agent on a new node. This way you can have end-to-end automation
for all your new nodes and you no longer need to manually run the installation script.

### What is Tutum?

Tutum.co is a hosted docker orchestration platform that allows you to deploy your docker containers easily via a very
strong UI and API. It also has built-in monitoring and health checking. It also allows you to register your docker images
in its private registry.

Yes, it's free.

## Installation

Add the role to your requirements.yml:

    - src: thecodeassassin.tutum-ansible-role
      name: tutum-ansible-role
      
      
Add the role to your role list:

    ---
    - hosts: all
      sudo: yes
    
      roles:
        - { role: tutum-ansible-role, tutum_api_header: "ApiKey tutum_username:your_api_token" }


### Role variables

The only required variable is the api header. You can get this from https://dashboard.tutum.co/account/#container-api-key.

```
# set the api header (required)
tutum_api_header: ApiKey thecodeassassin:1234567890abcdefghijklmnop
```

Optional variables:
```
# Tutum repository
tutum_repo: "repo.tutum.co"

# Tutum host (also the host of the API)
tutum_host: "https://dashboard.tutum.co/"

# Tutum default uuid (will be set automatically by the agent)
tutum_uuid: ""

# Link to the tutum gpg key
tutum_gpg_key: "https://files.tutum.co/keys/A87A2270.pub"

# Tutum certified common name (Will be the name of your node, this will be set by the agent upon start)
tutum_cert_common_name: ""

```

### Paramaterized Role

    ---
    - hosts: all
      roles:
        - { role: tutum-ansible-role, tutum_api_header: "ApiKey thecodeassassin:1234567890abcdefghijklmnop" }
    

## Credits
Created by Stephen "TheCodeAssassin" Hoogendijk