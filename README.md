# Learn Terraform - Provisionando un EKS Cluster


Primero instalamos terraform


```
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```


Segundo Instalamos awscli


```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
./aws/install
```


Tercero, configuramos aws-cli

```
aws configure
```


Cuarto mandamos los comandos de terraform

```
terraform init && terraform plan && terraform apply --auto-approve
```

Setear kubectl

```
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)

```

Ahora si queremos lo podremos enchular.

