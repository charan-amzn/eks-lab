### Amazon Elastic Container Service for Kubernetes - Lab Session

* Generate Access Keys for your IAM user 

* Configure AWS CLI 

* Download eksctl and create cluster 

    *Linux users* 

    > curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

    > sudo mv /tmp/eksctl /usr/local/bin
    
    *macOS users - Alternative method*

    > brew tap weaveworks/tap

    > brew install weaveworks/tap/eksctl

    *Windows users*

    > chocolatey install eksctl

* Run following command to create EKS Cluster and Worker Nodes 

    > eksctl create cluster --region=us-east-1 --ssh-access --ssh-public-key=teja-key-pair.pem --version=1.12 --name=eks-lab

* Verify that EKS Cluster is created and Worker Node Autoscaling group is created 

    > kubectl get svc 

    > kubectl get nodes

* You have a working cluster with nodes associated and dedicated workstation using which we can make deployments. From the directory you cloned, using tomcat.yaml file in it, run this command 

    > kubectl apply -f tomcat.yaml

* Go to ELB Console, get CNAME of ELB and test that app is working fine

* Clean up deployment and service

    > kubectl delete -f tomcat.yaml 
