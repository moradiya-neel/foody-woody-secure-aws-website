# 10 - Evidence Index

This page maps the captured screenshots to the control or validation they support.

## Amazon S3

| Evidence | What it demonstrates |
| --- | --- |
| [`01-create-s3-bucket.png`](../assets/evidence/s3/01-create-s3-bucket.png) | S3 bucket creation/configuration |
| [`02-block-public-access-enabled.png`](../assets/evidence/s3/02-block-public-access-enabled.png) | S3 Block Public Access enabled |
| [`03-website-files-uploaded.png`](../assets/evidence/s3/03-website-files-uploaded.png) | `index.html`, `web.css`, and `web.js` uploaded |

## Amazon CloudFront and OAC

| Evidence | What it demonstrates |
| --- | --- |
| [`01-cloudfront-distribution-setup.png`](../assets/evidence/cloudfront/01-cloudfront-distribution-setup.png) | CloudFront distribution configuration |
| [`02-s3-origin-selected.png`](../assets/evidence/cloudfront/02-s3-origin-selected.png) | S3 bucket selected as the origin |
| [`03-private-origin-oac.png`](../assets/evidence/cloudfront/03-private-origin-oac.png) | Private origin access / OAC configuration |
| [`04-viewer-cache-behavior.png`](../assets/evidence/cloudfront/04-viewer-cache-behavior.png) | Viewer protocol and cache behavior configuration |
| [`05-oac-bucket-policy.png`](../assets/evidence/cloudfront/05-oac-bucket-policy.png) | S3 bucket policy supporting CloudFront OAC access |
| [`06-default-root-object.png`](../assets/evidence/cloudfront/06-default-root-object.png) | `index.html` configured as the default root object |
| [`07-cloudfront-deployed.png`](../assets/evidence/cloudfront/07-cloudfront-deployed.png) | Distribution deployed |
| [`08-website-via-cloudfront-https.jpeg`](../assets/evidence/cloudfront/08-website-via-cloudfront-https.jpeg) | Website successfully loaded through CloudFront over HTTPS |

## AWS WAF

| Evidence | What it demonstrates |
| --- | --- |
| [`01-cloudfront-resource-selected.png`](../assets/evidence/waf/01-cloudfront-resource-selected.png) | CloudFront selected as the protected resource |
| [`02-aws-managed-rule-groups.png`](../assets/evidence/waf/02-aws-managed-rule-groups.png) | AWS managed rule group selection |
| [`03-managed-rules-configured.png`](../assets/evidence/waf/03-managed-rules-configured.png) | Managed rule groups included in the Web ACL |
| [`04-web-acl-created.png`](../assets/evidence/waf/04-web-acl-created.png) | Web ACL created |
| [`05-waf-enabled-cloudfront.png`](../assets/evidence/waf/05-waf-enabled-cloudfront.png) | WAF enabled/associated with CloudFront |
| [`06-malicious-request-blocked-403.png`](../assets/evidence/waf/06-malicious-request-blocked-403.png) | Malicious XSS-style query returned HTTP `403 Forbidden` |

## Architecture

[`foody-woody-architecture-diagram.png`](../assets/architecture/foody-woody-architecture-diagram.png) summarizes the intended security relationship among the user, AWS WAF, CloudFront, OAC, S3, IAM, and monitoring/audit services.

## Evidence boundary

There are no separate IAM, CloudWatch, CloudTrail, or AWS Config screenshots in this repository. Those topics are documented as security practices and production controls, not represented as independently validated implementation evidence.
