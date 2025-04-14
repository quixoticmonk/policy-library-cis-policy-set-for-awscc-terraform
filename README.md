# AWSCC Provider Policies for CIS AWS Foundations Benchmark

The repository contains the Sentinel policies for AWSCC provider that implement the CIS AWS Foundations Benchmark controls. 

> [!NOTE]  
> Few of the checks were initially written manually and the rest were auto generated using Q chat on a terminal requiring examples to test agains. Do review the GitHub actions summary to view if any of the policy checks have any issues on testing.

These policies are designed to work with the AWS Cloud Control (AWSCC) provider and follow the same patterns and conventions as the AWS provider policies. They can be used to enforce best practices and security standards across your AWS environment managed with the AWSCC provider.

For more details on how to work with these policies and to understand the Sentinel language and framework, please refer to the [Sentinel documentation](https://developer.hashicorp.com/sentinel/) or the README documentation included with each of the policy libraries.


## Policies Included

### CloudTrail
- Cloudtrail S3 Bucket should have access logging enabled ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/cloudtrail/cloudtrail-bucket-access-logging-enabled.sentinel))
- Cloudtrail Cloudwatch Logs Group Arn is set ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/cloudtrail/cloudtrail-cloudwatch-logs-group-arn-present.sentinel))
- Cloudtrail LogFile Validation is enabled ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/cloudtrail/cloudtrail-log-file-validation-enabled.sentinel))
- Cloudtrail S3 Bucket should not be public ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/cloudtrail/cloudtrail-logs-bucket-not-public.sentinel))
- CloudTrail should have encryption at-rest enabled ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/cloudtrail/cloudtrail-server-side-encryption-enabled.sentinel))

### S3
- S3 general purpose buckets should have block public access settings enabled at a bucket level ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/s3/s3-block-public-access-bucket-level.sentinel))
- Ensure that Object-level logging for events is enabled for S3 buckets ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/s3/s3-enable-object-logging-for-events.sentinel))
- S3 general purpose buckets should require ssl for all requests ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/s3/s3-require-ssl.sentinel))

### EC2
- AWS EBS volumes are encrypted ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/ec2/ec2-ebs-encryption-enabled.sentinel))


### VPC
- Ensure VPC flow logging is enabled in all VPCs ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/vpc/vpc-flow-logging-enabled.sentinel))

### EFS
- Ensure that encryption is enabled for EFS file systems ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/efs/efs-encryption-at-rest-enabled.sentinel))

### KMS
- AWS KMS key rotation should be enabled ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/kms/kms-key-rotation-enabled.sentinel))

### RDS
- Ensure that encryption-at-rest is enabled for RDS Instances ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/rds/rds-encryption-at-rest-enabled.sentinel))
- Ensure Auto Minor Version Upgrade feature is Enabled for RDS Instances ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/rds/rds-minor-version-upgrade-enabled.sentinel))
- Ensure that public access is not given to RDS Instance ([code](https://github.com/hashicorp/policy-library-CIS-Policy-Set-for-AWS-Terraform/blob/main/policies-awscc/rds/rds-public-access-disabled.sentinel))

## Implementation Notes

The policies in this directory are implemented for the AWSCC provider based on the AWS provider policies. Some key points to note:

1. **Resource Structure Differences**: The AWSCC provider has different resource structures compared to the AWS provider for some resources. The policies have been adapted to work with these differences.

2. **Missing Policies**: Some policies from the AWS provider may not be implemented for the AWSCC provider due to resource unavailability or significant differences in resource structure.

## Getting Started

This getting started guide assumes that:

1. You are familiar with core workflows in HCP Terraform and Terraform Enterprise, and you have an existing workspace configured with AWS access credentials.

2. You have a user account that is part of the ["owners"](https://developer.hashicorp.com/terraform/cloud-docs/users-teams-organizations/permissions#organization-owners) team or have ["Manage Policies"](https://developer.hashicorp.com/terraform/cloud-docs/users-teams-organizations/permissions#manage-policies) organization-level permissions to create new policy sets and policies.

3. Ensure you are using HCP Terraform or Terraform Enterprise [v202312-1](https://developer.hashicorp.com/terraform/enterprise/releases/2023/v202312-1) or a later version.

4. You are using Sentinel version 0.26.x or later.

By default, the module will enable all policies within the library, and they will be enforced by the HCP Platform with the `enforcement_level` set to `advisory` only.

**Example:**
```
policy "rds-encryption-at-rest-enabled" {
  source = "./policies-awscc/rds/rds-encryption-at-rest-enabled.sentinel"
  enforcement_level = "advisory"
}
```

If you want to enable only a subset of the policies or change the [enforcement levels](https://developer.hashicorp.com/sentinel/docs/concepts/enforcement-levels) to either `soft-mandatory` or `hard-mandatory`, we recommend updating the contents of the `sentinel.hcl` file in each library before applying the Terraform configuration.

## Resources

- [Get Started - HCP Terraform](https://developer.hashicorp.com/terraform/tutorials/cloud-get-started)
- [Policy Enforcement](https://developer.hashicorp.com/terraform/cloud-docs/policy-enforcement)
- [Managing Policy Sets](https://developer.hashicorp.com/terraform/cloud-docs/policy-enforcement/manage-policy-sets)
- [Introduction to Sentinel](https://developer.hashicorp.com/sentinel/intro/what)
- [Sentinel Documentation](https://developer.hashicorp.com/sentinel/docs)
- [AWSCC Provider Documentation](https://registry.terraform.io/providers/hashicorp/awscc/latest/docs)



