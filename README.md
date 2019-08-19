**Prerequisites:** 
- Virtualbox
  + Signed kernel module if you are using Secure Boot in UEFI
- Vagrant
- Ansible


**To Run:**
- clone the repository
- `vagrant up`
- copy your ssh key to each machine
  + `ssh-copy-id vagrant@192.168.50.101`
  + ...
- `cd ansbile`
- `ansible-playbook swarm.yml -i hosts`
- check [http://192.168.50.101:9000](http://192.168.50.101:9000) for a Docker UI