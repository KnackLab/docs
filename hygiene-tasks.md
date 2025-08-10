# Knack Infrastructure — Hygiene and Follow-up Tasks

- MongoDB
  - Define backup cadence (e.g., nightly mongodump to `mongo-backup-knack`) and quarterly restore test.
  - Plan upgrade (4.4.21 → 5/6) or evaluate Atlas migration later.
  - Plan encrypted EBS volumes at next maintenance/migration.

- S3
  - Enable versioning on `knacklab-assets`, `knacklab-programs`, `mongo-backup-knack`.
  - Add lifecycle: transition older objects to IA/Glacier; retain backups per policy.

- CI/CD
  - Add ECR lifecycle policy (e.g., keep last 20 tags per repo).
  - Optional: use GitHub OIDC to assume AWS roles (avoid long-lived keys).

- Observability
  - Add HTTPS certificate expiry monitor in Uptime for all domains.
  - Add basic CloudWatch alarms (EC2 status checks, CPU, disk).

- Access & security groups (when you review)
  - Confirm SSH/admin ports scope; prefer SSM Session Manager over public SSH.
  - Ensure least-privilege IAM for deploy and runtime.

- Legacy cleanup (when ready)
  - Remove staging DNS pointing to inactive IP.
  - Remove unused containers (e.g., `mongodb-change-streams`).
  - Prune unused ECR repos/tags.


