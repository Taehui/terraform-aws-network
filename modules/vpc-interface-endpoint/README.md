# vpc-interface-endpoint

This module creates following resources.

- `aws_vpc_endpoint`
- `aws_vpc_endpoint_connection_notification` (optional)

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.15 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 3.45 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 3.50.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_security_group"></a> [security\_group](#module\_security\_group) | ../security-group | n/a |

## Resources

| Name | Type |
|------|------|
| [aws_resourcegroups_group.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/resourcegroups_group) | resource |
| [aws_vpc_endpoint.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_endpoint) | resource |
| [aws_vpc_endpoint_connection_notification.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_endpoint_connection_notification) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_name"></a> [name](#input\_name) | (Required) Desired name for the VPC Interface Endpoint. | `string` | n/a | yes |
| <a name="input_service_name"></a> [service\_name](#input\_service\_name) | (Required) The service name. For AWS services the service name is usually in the form `com.amazonaws.<region>.<service>`. | `string` | n/a | yes |
| <a name="input_subnets"></a> [subnets](#input\_subnets) | (Required) The ID of one or more subnets in which to create a network interface for the endpoint. | `list(string)` | n/a | yes |
| <a name="input_vpc_id"></a> [vpc\_id](#input\_vpc\_id) | (Required) The ID of the VPC in which the endpoint will be used. | `string` | n/a | yes |
| <a name="input_auto_accept"></a> [auto\_accept](#input\_auto\_accept) | (Optional) Accept the VPC endpoint (the VPC endpoint and service need to be in the same AWS account). | `bool` | `true` | no |
| <a name="input_default_security_group"></a> [default\_security\_group](#input\_default\_security\_group) | (Optional) The configuration of the default security group for the interface endpoint. `default_security_group` block as defined below.<br>    (Optional) `name` - The name of the default security group.<br>    (Optional) `description` - The description of the default security group.<br>    (Optional) `ingress_cidrs` - A list of IPv4 CIDR blocks to allow inbound traffic from.<br>    (Optional) `ingress_ipv6_cidrs` - A list of IPv6 CIDR blocks to allow inbound traffic from.<br>    (Optional) `ingress_prefix_lists` - A list of Prefix List IDs to allow inbound traffic from.<br>    (Optional) `ingress_security_groups` - A list of source Security Group IDs to allow inbound traffic from. | `any` | `{}` | no |
| <a name="input_module_tags_enabled"></a> [module\_tags\_enabled](#input\_module\_tags\_enabled) | (Optional) Whether to create AWS Resource Tags for the module informations. | `bool` | `true` | no |
| <a name="input_notification_configurations"></a> [notification\_configurations](#input\_notification\_configurations) | (Optional) A list of configurations of Endpoint Connection Notifications for VPC Endpoint events. | <pre>list(object({<br>    sns_arn = string<br>    events  = list(string)<br>  }))</pre> | `[]` | no |
| <a name="input_policy"></a> [policy](#input\_policy) | (Optional) A policy to attach to the endpoint that controls access to the service. This is a JSON formatted string. Defaults to full access. All Gateway and some Interface endpoints support policies. | `string` | `null` | no |
| <a name="input_private_dns_enabled"></a> [private\_dns\_enabled](#input\_private\_dns\_enabled) | (Optional) Whether or not to associate a private hosted zone with the specified VPC. | `bool` | `false` | no |
| <a name="input_resource_group_description"></a> [resource\_group\_description](#input\_resource\_group\_description) | (Optional) The description of Resource Group. | `string` | `"Managed by Terraform."` | no |
| <a name="input_resource_group_enabled"></a> [resource\_group\_enabled](#input\_resource\_group\_enabled) | (Optional) Whether to create Resource Group to find and group AWS resources which are created by this module. | `bool` | `true` | no |
| <a name="input_resource_group_name"></a> [resource\_group\_name](#input\_resource\_group\_name) | (Optional) The name of Resource Group. A Resource Group name can have a maximum of 127 characters, including letters, numbers, hyphens, dots, and underscores. The name cannot start with `AWS` or `aws`. | `string` | `""` | no |
| <a name="input_security_groups"></a> [security\_groups](#input\_security\_groups) | (Optional) A set of security group IDs to associate with the network interface. | `set(string)` | `[]` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | (Optional) A map of tags to add to all resources. | `map(string)` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_arn"></a> [arn](#output\_arn) | The Amazon Resource Name (ARN) of the VPC endpoint. |
| <a name="output_default_security_group"></a> [default\_security\_group](#output\_default\_security\_group) | The default security group of the VPC endpoint. |
| <a name="output_dns_configurations"></a> [dns\_configurations](#output\_dns\_configurations) | The DNS entries for the VPC Endpoint. |
| <a name="output_id"></a> [id](#output\_id) | The ID of the VPC endpoint. |
| <a name="output_managed"></a> [managed](#output\_managed) | Whether or not the VPC Endpoint is being managed by its service. |
| <a name="output_name"></a> [name](#output\_name) | The VPC Interface Endpoint name. |
| <a name="output_network_interface_ids"></a> [network\_interface\_ids](#output\_network\_interface\_ids) | One or more network interfaces for the VPC Endpoint. |
| <a name="output_notification_configurations"></a> [notification\_configurations](#output\_notification\_configurations) | A list of Endpoint Connection Notifications for VPC Endpoint events. |
| <a name="output_owner_id"></a> [owner\_id](#output\_owner\_id) | The Owner ID of the VPC endpoint. |
| <a name="output_policy"></a> [policy](#output\_policy) | The policy which is attached to the endpoint that controls access to the service. |
| <a name="output_security_groups"></a> [security\_groups](#output\_security\_groups) | A set of security group IDs which is assigned to the VPC endpoint. |
| <a name="output_service_name"></a> [service\_name](#output\_service\_name) | The service name of the VPC Interface Endpoint. |
| <a name="output_state"></a> [state](#output\_state) | The state of the VPC endpoint. |
| <a name="output_subnet_ids"></a> [subnet\_ids](#output\_subnet\_ids) | A list of Subnet IDs of the VPC endpoint. |
| <a name="output_vpc_id"></a> [vpc\_id](#output\_vpc\_id) | The VPC ID of the VPC endpoint. |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
