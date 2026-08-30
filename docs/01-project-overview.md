# 01 - Project Overview

## Scenario

Foody Woody is a fictional restaurant website used as the workload for this cloud security lab. The site contains static content such as menu information, offers, images, and front-end assets. Although the application itself is simple, the security question is realistic: how should public web content be delivered without making the underlying storage bucket public?

## Objective

I designed the project around a serverless delivery path using Amazon S3, Amazon CloudFront, Origin Access Control (OAC), and AWS WAF.

The goals were to:

- store static website content in S3 without public bucket access;
- make CloudFront the public entry point for website delivery;
- use OAC to authorize CloudFront to retrieve private S3 objects;
- redirect viewer traffic from HTTP to HTTPS;
- use AWS WAF managed rules to inspect suspicious requests;
- validate both normal website delivery and a blocked malicious request; and
- document IAM, monitoring, audit, and compliance controls honestly according to what was and was not implemented in the lab.

## Architecture

`Internet user → AWS WAF → CloudFront → OAC → private S3`

![Architecture](../assets/architecture/foody-woody-architecture-diagram.png)

This creates a useful trust boundary. The public website does not require the S3 origin itself to become a public resource. CloudFront is responsible for public delivery, while the bucket policy limits origin access to the authorized distribution.

## Services used

| Service | Role in the design |
| --- | --- |
| Amazon S3 | Private storage for HTML, CSS, JavaScript, and other static assets |
| Amazon CloudFront | Global content delivery, caching, and HTTPS viewer access |
| CloudFront OAC | Authenticated access from CloudFront to the private S3 origin |
| AWS WAF | Web request inspection and blocking at the CloudFront layer |
| AWS IAM | Administrative access control and least-privilege model |
| CloudWatch | Operational monitoring consideration |
| CloudTrail | API activity and audit logging consideration |
| AWS Config | Configuration/compliance evaluation consideration |

## What was directly validated

The evidence in this repository demonstrates S3 configuration, website file upload, CloudFront configuration, OAC/private-origin configuration, successful website delivery through CloudFront over HTTPS, WAF association, managed WAF rules, and a malicious request receiving HTTP `403 Forbidden`.

IAM and monitoring/compliance services are discussed as security controls and production considerations. They are not presented as separately evidenced implementation work where screenshots or direct validation were not captured.
