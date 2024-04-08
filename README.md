# Learn Terraform - Provision an EKS Cluster

This repo is a companion repo to the [Provision an EKS Cluster tutorial](https://developer.hashicorp.com/terraform/tutorials/kubernetes/eks), containing
Terraform configuration files to provision an EKS cluster on AWS.

# ECK installation 

aws eks --profile sandbox --region eu-west-1 update-kubeconfig --name honeypot-eks-test
ksand create -f https://download.elastic.co/downloads/eck/2.10.0/crds.yaml
ksand apply -f https://download.elastic.co/downloads/eck/2.10.0/operator.yaml

# Get credential
ksand -n kube-system get secret quickstart-es-elastic-user -o go-template='{{.data.elastic | base64decode}}'



ksand port-forward service/quickstart-kb-http 5601 -n kube-system  

cuckoo sandbox - analiza statyczna, wywolanie programow, kasowanie plikow
virustotal - reguly YARA
  if self.remote.host != ip and "::ffff:" + self.remote.host != ip:
  if self.remote.host != ip and self.remote.host != "::ffff:" + ip:
  
modul do rejestracji polaczen - p0f? 