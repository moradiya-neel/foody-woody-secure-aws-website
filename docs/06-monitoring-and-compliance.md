# 06 - Monitoring and Compliance

Preventive controls reduce risk, but they do not remove the need for visibility. A production version of this architecture should make it possible to understand what changed, who changed it, how the service is behaving, and whether important configurations have drifted away from policy.

## CloudWatch - operational visibility

Amazon CloudWatch can centralize service metrics, logs, dashboards, and alarms. For this architecture, useful monitoring could include CloudFront request/error trends, WAF activity, and alarms for unusual request or error spikes.

## CloudTrail - auditability

AWS CloudTrail records AWS API activity and provides the audit trail needed to answer questions such as who changed a bucket policy, modified a CloudFront distribution, or updated a Web ACL.

This becomes especially important during incident investigation and change review because configuration state alone does not explain who performed an action or when it occurred.

## AWS Config - configuration compliance

AWS Config can record resource configuration and evaluate it against desired rules. Relevant examples for this type of workload could include checks around S3 public access, encryption, or other organization-specific cloud controls.

## Supporting security services

A broader production environment could also incorporate services such as AWS Security Hub for consolidated findings, GuardDuty for threat detection, and AWS Artifact for access to AWS compliance documentation.

## Evidence scope

These services are documented because they are relevant to operating this architecture securely, but they were **not independently implemented and validated as part of the captured hands-on evidence for this lab**. They are therefore treated as monitoring and compliance considerations rather than completed controls.
