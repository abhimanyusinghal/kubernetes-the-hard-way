# Provisioning Compute Resources

Note: You must have an Azure Subscription and be able to Create VMs on Azure Subscription. 

Do the below:

Generate SSH Key Pair node
`$ssh-keygen`

Leave all settings to default.

View the generated public key ID at:

```
$cat .ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD......8+08b vagrant@master-1
```

Use public key to create all VMs

- Deploys 5 VMs - 2 Master, 2 Worker and 1 Loadbalancer with the name 'kubernetes-ha-* '
- All VMs must use Ubuntu 18.04 
- All VMs must be on the same VNET

    | VM            |  VM Name               | Purpose       |
    | ------------  | ---------------------- |:-------------:|
    | master-1      | kubernetes-ha-master-1 | Master        |
    | master-2      | kubernetes-ha-master-2 | Master        |
    | worker-1      | kubernetes-ha-worker-1 | Worker        |
    | worker-2      | kubernetes-ha-worker-2 | Worker        |
    | loadbalancer  | kubernetes-ha-lb       | LoadBalancer  |


- Install's Docker on Worker nodes

- Runs the below command on workder nodes to allow for network forwarding in IP Tables.

  This is required for kubernetes networking to function correctly.
    > sysctl net.bridge.bridge-nf-call-iptables=1

## SSH to the nodes Using SSH Client Tools

Use your favourite SSH Terminal tool (putty).

Use the above IP addresses. 

**Username:** `azureuser`

## Verify Environment

- Ensure all VMs are up
- Ensure VMs are assigned a Public IP addresse
- Ensure you can SSH into these VMs using the IP and private keys
- Ensure the VMs can ping each other
- Ensure the worker nodes have Docker installed on them. Version: 18.06
  > command `sudo docker version`
