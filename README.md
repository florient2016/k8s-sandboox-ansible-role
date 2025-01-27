## Kubernetes Deployment Role
=========

Ansible Role for Deploying Kubernetes on 3 Nodes

This Ansible role deploys a Kubernetes cluster on 3 nodes: 1 controller and 2 workers. 
The role installs all necessary prerequisites, Kubernetes tools, and joins the worker nodes to the controller.

Features

- Installs Kubernetes prerequisites (e.g. Docker, containerd)
- Installs Kubernetes tools (e.g. kubeadm, kubelet, kubectl)
- Configures the controller node
- Joins worker nodes to the controller node
- Enables Kubernetes services (e.g. API server, scheduler, controller manager)

## Requirements
------------

- Ansible 2.9 or later
- 3 nodes with a supported Linux distribution (e.g. rhel distribution)
- Internet access for package installation

## Role Variables
--------------

- The `kubernetes_version` variable specifies the version of Kubernetes to be installed, in this case, version "1.27.0-0". Similarly, the calico_version variable indicates the version of Calico, a networking solution for Kubernetes, to be used, which is "v3.25.0".

- The `controller_hostname` variable sets the hostname for the Kubernetes control plane node, named "control". The worker_nodes list defines the hostnames of the worker nodes in the cluster, which are "worker1" and "worker2".

- The `k8s_packages` list includes the essential Kubernetes packages that need to be installed on the nodes: kubelet, kubeadm, and kubectl. These packages are crucial for running and managing the Kubernetes cluster.

- The `required_packages` list enumerates additional packages necessary for the setup. These include Docker-related packages (docker-ce, containerd.io, docker-buildx-plugin, docker-compose-plugin), utilities (yum-utils, curl, wget), and storage-related packages (device-mapper-persistent-data, lvm2). The presence of yum-utils twice in the list appears to be a redundancy.

## Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Getting Started
----------------

1. Clone this repository to your Ansible roles directory.
2. Update the k8s_version, controller_node, and worker_nodes variables in the defaults/main.yml file.
3. Create a playbook that includes this role and targets your nodes.
4. Run the playbook using ansible-playbook.

## Example Use Case
-------
Deploy a Kubernetes cluster on 3 nodes:
```bash
   - name: Deploy Kubernetes cluster
  hosts: controller,worker1, worker2
  become: yes
  roles:
    - k8s-deploy

## License
-------

BSD

## Contributing
------------------

Contributions are welcome! Please submit a pull request with your changes.

## Issues
------------------

If you encounter any issues, please open an issue on this repository.

I hope this helps! Let me know if you need any further assistance.
