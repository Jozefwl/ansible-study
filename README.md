# ansible-study
This repository is used for learning ansible for my bachelor's degree.


## first automation task
I want to automate this:
- Automate getting of cluster kubeconfig from rancher installation
- Add custom registry
- Get my frontend and backend repo (website-blog and backend-metrics)
- Build frontend on local, make it a docker image, then turn it into kubernetes deployment and service
- Run backend on k3s machine itself as it needs to track cpu, mem usage
- Use nginx to expose the ports


## Run playbook:
cd playbooks

sudo ansible-playbook playbook.yaml -e TARGET_NODE=debian

sudo ansible-playbook playbook.yaml -e TARGET_NODE=local_rancher --tags k8s
