# terraform-aviatrix-mc-spoke

### Description
Deploys a VPC/VNET/VCN and Aviatrix Spoke gateways. It is also possible to use an existing VPC/VNET/VCN.
China and government regions are supported in both AWS and Azure and auto detected based on region name.

### Diagram
\<Provide a diagram of the high level constructs thet will be created by this module>
<img src="<IMG URL>"  height="250">

### Compatibility
Module version | Terraform version | Controller version | Terraform provider version
:--- | :--- | :--- | :---
v1.0.0 | 0.13-1.x | >= 6.4 | >= 0.2.19

### Usage Examples
See examples

### Variables
The following variables are required:

key | value
:--- | :---
cloud | Cloud where this is deployed. Valid values: "AWS", "Azure", "ALI", "OCI", "GCP"
name | Name for this spoke VPC/VNET/VCN and it's gateways
region | Cloud region to deploy this VPC/VNET/VCN in
cidr | What ip CIDR to use for this VPC/VNET/VCN (Not required when use_existing_vpc is true)
account | The account name as known by the Aviatrix controller
transit_gw | The name of the transit gateway we want to attach this spoke to. Not required when attached is set to false.

The following variables are optional:

<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> = AWS, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> = Azure, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> = GCP, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> = OCI, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> = Alibaba


Key | Supported_CSP's |  Default value | Description
:-- | --: | :-- | :--
active_mesh | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false to disable active mesh.
attached | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if you don't want to attach spoke to transit_gw.
attached_gw_egress | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if you don't want to attach spoke to transit_gw_egress.
auto_advertise_s2c_cidrs | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Auto Advertise Spoke Site2Cloud CIDRs.
az_support | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | true | Set to false if the region does not support Availability Zones.
az1 | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | a<br>az-1<br>b | Concatenates with region to form az names. e.g. eu-central-1a. Used for insane mode only.
az2 | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | b<br>az-2<br>c | Concatenates with region to form az names. e.g. eu-central-1b. Used for insane mode only.
customer_managed_keys | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> | | Customer managed key ID for EBS Volume encryption.
customized_spoke_vpc_routes | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | A list of comma separated CIDRs to be customized for the spoke VPC routes. When configured, it will replace all learned routes in VPC routing tables, including RFC1918 and non-RFC1918 CIDRs. Example: 10.0.0.0/116,10.2.0.0/16
enable_encrypt_volume | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> | false | Set to true to enable EBS volume encryption for Gateway.
filtered_spoke_vpc_routes | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | |A list of comma separated CIDRs to be filtered from the spoke VPC route table. When configured, filtering CIDR(s) or it’s subnet will be deleted from VPC routing tables as well as from spoke gateway’s routing table. Example: 10.2.0.0/116,10.3.0.0/16
gw_subnet | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | |Subnet CIDR, for using an existing VPC. Required when use_existing_vpc is enabled. Make sure this is a public subnet.
ha_cidr | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | | The IP CIDR to be used to create ha_region spoke subnet. Only required when ha_region is set.
ha_gw |<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if you only want to deploy a single Aviatrix spoke gateway
ha_region | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | | Region for multi region HA. HA is multi-az single region by default, but will become multi region when this is set.
hagw_subnet | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Subnet CIDR, for using an existing VPC. Required when use_existing_vpc is enabled and ha_gw is true. Make sure this is a public subnet.
included_advertised_spoke_routes | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | A list of comma separated CIDRs to be advertised to on-prem as Included CIDR List. When configured, it will replace all advertised routes from this VPC. Example: 10.4.0.0/116,10.5.0.0/16
insane_mode | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> | false | Set to true to enable insane mode encryption
inspection | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Set to true to enable east/west Firenet inspection. Only valid when transit_gw is East/West transit Firenet.
instance_size | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> |  t3.medium<br>Standard_B1ms<br>n1-standard-1<br>VM.Standard2.2<br>ecs.g5ne.large | The size of the Aviatrix spoke gateways
private_vpc_default_route | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Program default route in VPC private route table.
security_domain | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Provide security domain name to which spoke needs to be deployed. Transit gateway must be attached and have segmentation enabled.
single_az_ha | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if Controller managed Gateway HA is desired
single_ip_snat | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Specify whether to enable Source NAT feature in single_ip mode on the gateway or not. Please disable AWS NAT instance before enabling this feature. Currently only supports AWS(1) and AZURE(8)
skip_public_route_table_update | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Skip programming VPC public route table.
subnet_pairs | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | 2 | Number of Public/Private subnet pairs created in the VPC.
subnet_size | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | 28 | Size of the Public/Private subnets in the VPC.
tags |<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | | Map of tags to assign to the gateway.
transit_gw_egress | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | | Add secondary transit to attach spoke to (e.g. for dual transit firenet). When segmentation is used, transit_gw MUST be used for east/west transit.
transit_gw_egress_route_tables | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | [] | A list of route tables to propagate routes to for transit_gw_egress attachment.
transit_gw_route_tables | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | [] | A list of route tables to propagate routes to for transit_gw attachment.
tunnel_detection_time | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | The IPsec tunnel down detection time for the Spoke Gateway in seconds. Must be a number in the range [20-600]. Default is 60.
use_existing_vpc | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Set to true to use an existing VPC in stead of having this module create one.
vpc_id | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | VPC ID, for using an existing VPC.

### Outputs
This module will return the following outputs:

key | description
:---|:---
[vpc](https://registry.terraform.io/providers/AviatrixSystems/aviatrix/latest/docs/resources/aviatrix_vpc) | The created VPC as an object with all of it's attributes (when use_existing_vpc is false). This was created using the aviatrix_vpc resource.
[spoke_gateway](https://registry.terraform.io/providers/AviatrixSystems/aviatrix/latest/docs/resources/aviatrix_spoke_gateway) | The created Aviatrix spoke gateway as an object with all of it's attributes.

