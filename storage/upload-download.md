# Use Case: Uploading & Downloading Files with gsutil

**Scenario:** Transfer log files securely between local machine and a GCP bucket.

**Commands:**
```bash
# Upload a file
gsutil cp logs.txt gs://my-bucket/

# Download a file
gsutil cp gs://my-bucket/logs.txt ./logs.txt
