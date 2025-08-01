# 🪣 Use Case: Auditing Cloud Storage Bucket Access

**Scenario:** As part of an incident response or security audit, you need to review who has access to sensitive Cloud Storage buckets and whether access logging is enabled.

---

## 🔍 View IAM Policy for a Bucket
```bash
# Display the IAM policy for a specific bucket
gsutil iam get gs://sensitive-bucket
```
### 📜 Enable Bucket Access Logs
```bash
# Enable logging for a bucket and direct logs to a logs bucket
gsutil logging set on -b gs://my-logs-bucket gs://sensitive-bucket
```
### 🚫 Disable Bucket Access Logs
```bash
# Turn off access logging for a bucket
gsutil logging set off gs://sensitive-bucket
```
### 👀 Review Bucket Permissions in Detail
```bash
# List all objects with their permissions (ACLs) in the bucket
gsutil ls -L -b gs://sensitive-bucket
```
### 🧾 Export Audit Logs to BigQuery (Optional)
```bash
# Create a sink to export Cloud Storage access logs to BigQuery
gcloud logging sinks create bucket-audit-sink \
    bigquery.googleapis.com/projects/my-project-id/datasets/bucket_audit_dataset \
    --log-filter="resource.type=gcs_bucket AND logName:cloudaudit.googleapis.com"
```