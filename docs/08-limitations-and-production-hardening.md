# 08 - Limitations and Production Hardening

This repository documents a focused personal lab. It demonstrates a meaningful secure delivery pattern, but it is not presented as a complete production restaurant platform.

## Current limitations

- **No custom domain:** The project used the CloudFront-provided domain rather than a branded DNS name.
- **No custom ACM certificate:** HTTPS was validated through CloudFront, but a custom-domain certificate workflow was outside the captured lab.
- **Static workload only:** There is no API, database, authentication system, payment flow, or server-side review submission feature.
- **Limited WAF validation:** A malicious XSS-style query was observed returning `403`. The project did not exhaustively test SQL injection variants, bot traffic, rate abuse, or DDoS scenarios.
- **No validated rate-based WAF rule:** Rate limiting would be a useful production control for abusive request patterns.
- **Monitoring not implemented as evidence:** CloudWatch alarms/logging, a dedicated CloudTrail trail, AWS Config rules, Security Hub, and GuardDuty were not independently implemented and validated in the captured lab.
- **IAM not separately evidenced:** IAM security practices are documented, but no project-specific IAM-user creation screenshots are used as validation evidence.
- **No infrastructure as code:** The lab was configured through the AWS Console rather than deployed through CloudFormation, CDK, or Terraform.
- **No CI/CD pipeline:** Website deployment and cache invalidation were not automated.
- **No application security testing program:** The single WAF test is a control validation, not a penetration test.

## Production hardening opportunities

A stronger production version could add a custom domain through Route 53 or another DNS provider, an ACM certificate for that domain, WAF rate-based and application-specific rules, WAF/CloudFront logging with alerting, CloudTrail and AWS Config governance, Security Hub/GuardDuty integration, tightly scoped IAM roles and policies, infrastructure as code, automated deployments, and documented incident-response procedures.

The point of listing these limitations is accuracy. A portfolio project is more useful when it clearly separates what was built and validated from what would be added next in a real production environment.
