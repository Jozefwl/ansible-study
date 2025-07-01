# ansible-study
This repository is used for learning ansible for my bachelor's degree.


## TODO
- Automate rke2 deployment on new machine and adding to rancher GUI
- Make helm chart for easier deployments and rollbacks
- Add deployment strategies
- Consolidate tasks so that user doesn't have to call 4 cmds
- Automate making StorageClass for new cluster and PV
- Fix bad naming

## Finished
- Expose ports
- Add custom registry
- Get frontend repo and build docker image
- Deploy docker image on kubernetes


## Run playbook:
cd playbooks

sudo ansible-playbook playbook.yaml -e TARGET_NODE=local

sudo ansible-playbook playbook.yaml -e TARGET_NODE=local --tags registry

# Documentation
Use --tags registry for installation of registry
Use --tags rollback for removal of deployment

## Rolling deployment (default)
sudo ansible-playbook deployment-strategies.yaml -e TARGET_NODE=local

## Blue/Green deployment
```bash 
sudo ansible-playbook deployment-strategies.yaml -e TARGET_NODE=local -e deployment_strategy=blue-green
```

## Canary deployment with specific IPs
```bash
sudo ansible-playbook deployment-strategies.yaml -e TARGET_NODE=local -e deployment_strategy=canary -e canary_user_ips='["192.168.1.100","192.168.1.101"]'
```
## A/B testing deployment
```bash
sudo ansible-playbook deployment-strategies.yaml -e TARGET_NODE=local -e deployment_strategy=ab-testing -e ab_test_percentage=30
```
## Shadow deployment
```bash
sudo ansible-playbook deployment-strategies.yaml -e TARGET_NODE=local -e deployment_strategy=shadow
```
## Recreate deployment
```bash
sudo ansible-playbook deployment-strategies.yaml -e TARGET_NODE=local -e deployment_strategy=recreate
```

# Downtime Checker
## Usage
Located in directory tests
```bash
node downtime_checker.js [url]
```