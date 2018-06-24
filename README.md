# For installing "Video Creator AWS" You need: 
***
1. [Server Ubuntu 16.04 LTS](https://aws.amazon.com/marketplace/pp/B01JBL2I8U)
2. [Amazon S3](https://aws.amazon.com/s3/)
3. [Amazon Simple Queue Service (SQS)](https://aws.amazon.com/sqs/)
4. [Mandrill API key](https://www.mandrill.com/)

## Step by step
***
### For install all needed packeges you need:
1. Install Ansible in you server [All methods](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

Run this command on server:
> $ sudo apt-get update
> $ sudo apt-get install software-properties-common
> $ sudo apt-add-repository ppa:ansible/ansible
> $ sudo apt-get update
> $ sudo apt-get install ansible

2. Сhange the variables in /group_vars/common.yml:

> bucket_name: "Your_Bucket_Name_S3"
> queue_name: "Your_Queue_Name_SQS"
> queue_region: "Your_Queue_Region"
> mandrill_api_key: "Your_Mandrill_API_key"

[How to get Your Mandrill API Key?](https://www.inboundnow.com/how-to-get-your-mandrill-api-key/)

3. Change IP for Ubuntu server IP in /hosts.ini

4. Run Ansible
If You run remotely:

> ansible -i hosts.ini -m ping setup_animation
> ansible-playbook -i hosts.ini setup_animation.yml

If You run on the server Ubuntu:

> ansible -i hosts.ini -m ping setup_animation --connect local
> ansible-playbook -i hosts.ini setup_animation.yml --connect local