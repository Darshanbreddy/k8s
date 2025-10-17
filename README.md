<img width="1919" height="762" alt="image" src="https://github.com/user-attachments/assets/1076f9ee-9741-4489-b42b-8f28f4596331" /># Kubernetes Repo

Installed KIND, Docker, Kubectl using the install.sh file was the first step

Then created a new directory called kind and created a new KIND cluster with 1 control plane(Master node) and 3 Worker node, can be seen in config.yml file

I ran into a error in the begnning(Deleted nodes: ["kindcluster-1-worker" "kindcluster-1-worker2" "kindcluster-1-worker3" "kindcluster-1-control-plane"]
ERROR: failed to create cluster: failed to init node with kubeadm: command "docker exec --privileged kindcluster-1-control-plane kubeadm init --config=/kind/kubeadm.conf --skip-token-print --v=6 --skip-phases=preflight" failed with error: exit status 1
Command Output: I1017 06:03:11.477139      93 initconfiguration.go:190] loading configuration from "/kind/kubeadm.conf")
To fix this error I just changed the version to kindest/node:v1.31.2, earlier it was kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55

Output of nodes after creating KIND cluster
ubuntu@ip-172-31-44-250:~/kind$ kubectl get nodes
NAME                          STATUS   ROLES           AGE     VERSION
kindcluster-1-control-plane   Ready    control-plane   4m14s   v1.31.2
kindcluster-1-worker          Ready    <none>          3m59s   v1.31.2
kindcluster-1-worker2         Ready    <none>          3m58s   v1.31.2
kindcluster-1-worker3         Ready    <none>          3m59s   v1.31.2

