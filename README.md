# Terraform Providers

Este repositório tem por objetivo armazenar os principais módulos já desenvolvidos pelo terraform, promovendo assim o rápido provisionamento e configuração de ambiente, seguindo as melhores práticas e recomendações

# Instalação

## Terraform
Para utilização dos módulos é necessário primeiramente a Instalação do Terraform

```bash
curl https://releases.hashicorp.com/terraform/1.0.10/terraform_1.0.10_linux_amd64.zip -o ./terraform.zip
unzip terraform.zip
sudo mv terraform /usr/local/bin/
```

A verificação da instalação do Terraform pode ser realizada através do comando:

```bash
terraform -v
```

## Exemplo de Utilização
```
  module "vpn" {
      source                   = "git@github.com:astechmind/terraform-aws-vpn.git"
      version                  = "2.0.0"

      name                                      = local.name
      environment                               = local.environment
      vpc_id                                    = module.vpc.vpc_id
      customer_ip_address                       = "115.160.246.74"
      local_ipv4_network_cidr                   = "0.0.0.0/0"
      remote_ipv4_network_cidr                  = module.vpc.vpc_cidr_block
      vpn_connection_static_routes_destinations = ["10.80.1.0/24"]
  }
```