# kubernete-scripts
Repository for bash and python scripts in a kubernetes environment


## NODE-ROLES SCRIPT

Prerequisites:
  - kubectl installed where the script will be ran
  - kubectx installed for changing contexts

This script checks every cluster within your kubernetes environment for nodes that have no roles assigned to them. There will be instances where the nodes did not get assigned a role properly such as control-plane, master, or worker. This script helps identify which nodes have no assigned roles quickly.

- This script may be modified to print out nodes with specific roles by changing the grep commands from "none" to desired keyword such as worker. Then edit the echo command to state "This node has a worker role: " $node. 

OUTPUT if all the nodes have been properly assigned a role:
```
> ./node-roles.sh
Getting nodes from each cluster and putting them in a file called nodes
nodes file saved
All nodes have assigned roles
```

## KIAM KILLER SCRIPT

Prerequisites:
  - kubectl installed where the script will be ran
  - kubectx installed for changing contexts

This script loops through each cluster and does a rolling restart on each kiam deployment and daemonset. This gracefully restarts kiam server pods and kiam agent pods.