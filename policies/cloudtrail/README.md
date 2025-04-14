# CloudTrail Policies for AWSCC Provider

This directory contains Sentinel policies for AWS CloudTrail resources using the AWSCC provider.

## Available Policies

The following policies are available for the AWSCC provider:

- [cloudtrail-bucket-access-logging-enabled](./cloudtrail-bucket-access-logging-enabled.sentinel): Ensures that CloudTrail S3 buckets have access logging enabled
- [cloudtrail-cloudwatch-logs-group-arn-present](./cloudtrail-cloudwatch-logs-group-arn-present.sentinel): Ensures that CloudTrail trails have CloudWatch logs group ARN set
- [cloudtrail-log-file-validation-enabled](./cloudtrail-log-file-validation-enabled.sentinel): Ensures that CloudTrail trails have log file validation enabled
- [cloudtrail-logs-bucket-not-public](./cloudtrail-logs-bucket-not-public.sentinel): Ensures that CloudTrail S3 buckets are not publicly accessible
- [cloudtrail-server-side-encryption-enabled](./cloudtrail-server-side-encryption-enabled.sentinel): Ensures that CloudTrail trails have server-side encryption enabled

## Policy Details

### cloudtrail-bucket-access-logging-enabled
This policy ensures that the S3 buckets used by CloudTrail have access logging enabled. This is important for security auditing and compliance with CIS AWS Foundations Benchmark.

### cloudtrail-cloudwatch-logs-group-arn-present
This policy checks that CloudTrail trails have a CloudWatch logs group ARN configured, which ensures that CloudTrail logs are being monitored and can trigger alerts.

### cloudtrail-log-file-validation-enabled
This policy verifies that log file validation is enabled for CloudTrail trails, which helps ensure the integrity of log files.

### cloudtrail-logs-bucket-not-public
This policy ensures that S3 buckets used to store CloudTrail logs are not publicly accessible, which is a critical security requirement.

### cloudtrail-server-side-encryption-enabled
This policy checks that CloudTrail trails have server-side encryption enabled using KMS keys, which protects the confidentiality of log data.

## Usage

These policies can be used with Terraform Cloud or Terraform Enterprise to enforce compliance with CIS AWS Foundations Benchmark requirements for CloudTrail resources created using the AWSCC provider.
