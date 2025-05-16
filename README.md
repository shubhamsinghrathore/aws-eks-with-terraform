# terraform-aws-eks-blueprint

A production-ready, modular, and easy-to-use Terraform configuration for deploying an Amazon EKS (Elastic Kubernetes Service) cluster with best practices on AWS. This blueprint provisions a secure VPC, public/private subnets, NAT gateways, and a scalable EKS cluster with managed node groups.

## Features

- **Modular VPC**: Uses the official AWS VPC Terraform module for robust networking.
- **Highly Available**: Spreads resources across multiple Availability Zones.
- **EKS Cluster**: Deploys an EKS cluster with managed node groups and essential addons (CoreDNS, kube-proxy, VPC CNI).
- **Spot Instances**: Supports cost-effective node groups using EC2 Spot Instances.
- **Tagging**: Consistent resource tagging for easy management.


## Folder Structure

```
eks/
├── eks.tf
├── provider.tf
└── vpc.tf
```

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) >= 1.0
- AWS CLI configured with appropriate credentials
- An AWS account with permissions to create EKS, VPC, and related resources

## Usage

1. **Clone the repository:**

   ```sh
   git clone https://github.com/your-username/terraform-aws-eks-blueprint.git
   cd terraform-aws-eks-blueprint/eks
   ```

2. **Initialize Terraform:**

   ```sh
   terraform init
   ```

3. **Review and customize variables in `provider.tf` as needed.**

4. **Plan the deployment:**

   ```sh
   terraform plan
   ```

5. **Apply the configuration:**

   ```sh
   terraform apply
   ```

6. **Access your EKS cluster:**

   After apply, update your kubeconfig:

   ```sh
   aws eks --region us-east-2 update-kubeconfig --name my-eks-cluster
   ```

## Clean Up

To destroy all resources:

```sh
terraform destroy
```

## Notes

- Default region is `us-east-2`. Change in `provider.tf` if needed.
- Subnets, VPC CIDR, and other settings are easily adjustable in `provider.tf`.
- This setup is suitable for dev/test and can be extended for production.

## License

MIT
