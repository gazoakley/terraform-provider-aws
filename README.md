# Terraform AWS Provider Custom Builds

This repository stores custom builds of the Terraform AWS provider along with build scripts. See [Releases](https://github.com/gazoakley/terraform-provider-aws/releases) for downloads.

## Criteria

* Should not have the proposal label:        `-label:proposal`
* Should not have the breaking-change label: `-label:breaking-change`
* Should have tests:                         `label:tests`
* Should have checks passing:                `status:success`
* Should not be [WIP]:                       `NOT [WIP] in:title`

[Filtered pull requests](https://github.com/terraform-providers/terraform-provider-aws/pulls?q=is%3Apr+is%3Aopen+-label%3Aproposal+-label%3Abreaking-change+label%3Atests+status%3Asuccess+NOT+%5BWIP%5D+in%3Atitle+sort%3Areactions-%2B1-desc+)

## Current Inclusions

| PR | Release Notes | Source |
|-----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| [#11162](https://www.github.com/terraform-providers/terraform-providers-aws/pulls/11162) | **New Data Source:** `aws_ec2_transit_gateway_peering_attachment`<br>**New Resource:** `aws_ec2_transit_gateway_peering_attachment` | [j-nix/add_transit_gw_peering](https://github.com/j-nix/terraform-provider-aws/tree/add_transit_gw_peering) |
| [#10256](https://www.github.com/terraform-providers/terraform-providers-aws/pulls/10256) | **New Resource:** `aws_cloudwatch_event_bus` | [alexanderkalach/aws-cloudwatch-event-bus](https://github.com/alexanderkalach/terraform-provider-aws/tree/aws-cloudwatch-event-bus) |
| [#12183](https://www.github.com/terraform-providers/terraform-providers-aws/pulls/12183) | resource/aws_elasticsearch_domain: Add advanced_security_options block for fine grained access control | [JustinSchuyler/master](https://github.com/JustinSchuyler/terraform-provider-aws/tree/master) |
| [#10560](https://www.github.com/terraform-providers/terraform-providers-aws/pulls/10560) | **New Resource:** `aws_ec2_client_vpn_route` | [angelabad/master](https://github.com/angelabad/terraform-provider-aws/tree/master) |
| [#8876](https://www.github.com/terraform-providers/terraform-providers-aws/pulls/8876) | resource/aws_eip: Add support for EIPs with a specified BYOIP address | [arwilczek90/8004_eip_byoip_address](https://github.com/arwilczek90/terraform-provider-aws/tree/8004_eip_byoip_address) |
| [#12574](https://www.github.com/terraform-providers/terraform-providers-aws/pulls/12574) | resource/aws_lb_listener_rule: Add support for multiple, weighted target groups in forward rules<br>resource/aws_lb_listener: Add support for multiple, weighted target groups in default actions | [rdelcampog/f/aws_lb_listener_rule-weighted-tg](https://github.com/rdelcampog/terraform-provider-aws/tree/f/aws_lb_listener_rule-weighted-tg) |
| [#12218](https://www.github.com/terraform-providers/terraform-providers-aws/pulls/12218) | resource/aws_vpn_connection: Accelerated Site-to-Site VPN support | [sjones-and/f-vpn-acceleration](https://github.com/sjones-and/terraform-provider-aws/tree/f-vpn-acceleration) |

## Build Method

* Fetch tags:
  `git fetch origin --tags`
* Create remotes for feature branches:
  `git remote add <username> git@github.com:<username>/terraform-provider-aws.git`
* Fetch remotes:
  `git fetch <username>`
* Create a new branch from an existing tagged version:
  `git checkout tags/v<version> -b v<version>-custom`
* Merge each branch:
  `git merge -m "Merge remote-tracking branch '<username>/<remotebranch>' into v<version>-custom" <username>/<remotebranch>`
* Run acceptance tests
* Create release file (append all release notes)
* Tag release:
  `git tag v<version>-custom`
* Push release tag:
  `git push origin tags/v<version>-custom`
