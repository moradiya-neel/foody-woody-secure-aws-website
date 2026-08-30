# 07 - Security Architecture

## Trust boundaries

The project uses a simple architecture, but the security boundaries are intentional.

### Viewer path

`Internet user → AWS WAF → CloudFront`

CloudFront is the public-facing delivery service. WAF evaluates viewer requests associated with the distribution.

### Origin path

`CloudFront → OAC → private S3`

The S3 bucket does not need anonymous public-read access. CloudFront is authorized to retrieve the content through the OAC-based origin relationship.

## Why the layers matter

Each control addresses a different part of the risk:

| Layer | Security purpose |
| --- | --- |
| S3 Block Public Access | Reduces accidental/direct public origin exposure |
| CloudFront | Provides the controlled public delivery endpoint and caching |
| OAC | Authenticates/authorizes CloudFront access to the S3 origin |
| HTTPS viewer policy | Protects viewer traffic in transit to CloudFront |
| AWS WAF | Inspects and blocks selected malicious request patterns |
| IAM | Controls who can administer the AWS environment |
| Monitoring/audit services | Provide visibility, accountability, and configuration oversight |

## Defense in depth

No single service makes the site “secure.” For example, WAF does not replace private origin access, and private S3 does not replace request filtering. The value comes from combining controls so that failure or weakness in one area does not automatically expose the entire workload.

For this lab, the strongest architectural improvement is the removal of direct public S3 access from the normal viewer path. WAF then adds request-layer protection on top of that design.

## Serverless characteristics

The site does not require an EC2 web server for static content. S3 stores the objects and CloudFront handles distribution. This reduces the infrastructure that must be patched and administered for the website itself, while still requiring careful configuration of identities, policies, logging, and edge security.
