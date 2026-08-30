# 05 - IAM Security

## Administrative access model

A secure workload is not only about the request path used by website visitors. The identities allowed to change S3, CloudFront, WAF, and logging configuration are part of the security boundary as well.

For this project, AWS administration is treated as non-root activity. The appropriate operating model is a dedicated IAM identity with MFA and only the permissions required for the work being performed.

## Least privilege

A training lab may use AWS-managed policies for convenience, but broad policies such as service-level `FullAccess` are not the end state I would choose for production. A stronger implementation would define permissions around specific resources and actions, use roles where practical, and separate administrative responsibilities.

Examples of the intended permission areas are:

- manage the specific S3 bucket and its policy;
- manage the relevant CloudFront distribution;
- manage the Web ACL and its association;
- read IAM information where operationally necessary; and
- avoid routine use of the AWS account root user.

## MFA

MFA adds another control to console authentication so possession of a password alone is not enough to sign in. For privileged cloud administration, MFA should be considered a baseline control rather than an optional convenience.

## Evidence scope

IAM is included here as part of the project's security design and operating practice. This repository does not present a project-specific IAM-user creation sequence as independently validated screenshot evidence.
