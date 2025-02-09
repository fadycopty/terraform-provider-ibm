---

subcategory: "VPC infrastructure"
layout: "ibm"
page_title: "IBM : security_group"
description: |-
  Manages IBM security group.
---

# ibm_is_security_group
Create, update, or delete a security group for your VPC. When you want to create a security group and security group rule for a virtual server instance in your VPC, you must create these resources in a specific order to avoid errors during the creation of your virtual server instance. For more information, about security group, see [setting up the security groups for your virtual server instance](https://cloud.ibm.com/docs/vpc?topic=vpc-configuring-the-security-group).

## Example usage

```terraform
resource "ibm_is_vpc" "testacc_vpc" {
  name = "test"
}

resource "ibm_is_security_group" "testacc_security_group" {
  name = "test"
  vpc  = ibm_is_vpc.testacc_vpc.id
}
```


## Argument reference
Review the argument references that you can specify for your resource. 

- `name` - (Optional, String) The security group name.
- `resource_group` - (Optional, String) The resource group ID where the security group to be created.
- `tags`- (Optional, List of Strings) The tags associated with an instance.
- `vpc` - (Required, Forces new resource, String) The VPC ID.

## Attribute reference
In addition to all argument reference list, you can access the following attribute reference after your resource is created.

- `crn` - (String) The CRN of the security group.
- `id` - (String) The ID of the security group.
- `rules` - (List of Objects) A nested block describes the rules of this security group. Nested `rules` blocks have the following structure.

  Nested scheme for `rules`:
  - `code` - (String) The `ICMP` traffic code to allow.
  - `direction`-  (String) The direction of the traffic either `inbound` or `outbound`.
  - `ip_version` - (String) IP version either `ipv4` or `ipv6`.
  - `protocol` - (String) The type of the protocol `all`, `icmp`, `tcp`, `udp`.
  - `port_max`- (Integer) The `TCP/UDP` port range that includes the maximum bound.
  - `port_min`- (Integer) The `TCP/UDP` port range that includes the minimum bound.
  - `remote` - (String) Security group id, an IP address, a `CIDR` block, or a single security group identifier.
  - `type` - (String) The `ICMP` traffic type to allow.

## Import
The `ibm_is_security_group` resource can be imported by using load balancer ID. 

**Example**

```
$ terraform import ibm_is_security_group.example a1aaa111-1111-111a-1a11-a11a1a11a11a
```
