# 09 - Cleanup

After the website and security controls were validated, I removed the lab resources to prevent unnecessary ongoing charges and leave the AWS account clean.

## Cleanup sequence performed

1. **Disabled the CloudFront distribution.** CloudFront distributions must reach the disabled state before they can be deleted.
2. **Disassociated WAF while CloudFront was disabling.** The Web ACL was removed from the distribution and the WAF configuration was deleted.
3. **Emptied and deleted the S3 bucket.** Objects were removed before deleting the bucket itself.
4. **Removed the lab IAM user/group where applicable.** Project-specific access objects were cleaned up rather than left behind unnecessarily.
5. **Deleted the CloudFront distribution.** Once the distribution had finished disabling, it was removed.

## Why cleanup is part of the project

Cloud labs should include teardown, not just deployment. Unused distributions, WAF configurations, storage, logs, and identities can create cost, clutter, or unnecessary attack surface. Treating cleanup as a deliberate project phase is part of responsible cloud administration.
