# Use Case: Uploading & Downloading Files with gsutil

**Scenario:** Transfer log files securely between local machine and a GCP bucket.

**Commands:**

## Upload a file
```bash
# Upload a file

gsutil cp logs.txt gs://my-bucket/
```

## Download a file
```bash
gsutil cp gs://my-bucket/logs.txt ./logs.txt
```

## 🗝️ Rotate Your Encryption Key
```bash
# Copy an object to itself with a new key

gsutil cp -o "GSUtil:encryption_key=$(cat new-key.txt)" \
    gs://secure-bucket/secure.log gs://secure-bucket/secure.log
```

## 🔎 List Firewall Rules
```bash
# List firewall rules for your project

gcloud compute firewall-rules list
```

## ❌ Delete a Firewall Rule
```bash
# Remove the allow-ssh rule

gcloud compute firewall-rules delete allow-ssh
```

## 🔹 Export Flow Logs to BigQuery
```bash
# Create a sink to export flow logs to BigQuery

gcloud logging sinks create flow-logs-sink bigquery.googleapis.com/projects/my-project-id/datasets/flow_logs_dataset \
    --log-filter="resource.type=gce_subnetwork"
```

## 🖥️ Enable OS Login for a Single VM
```bash
# Apply OS Login metadata to one VM

gcloud compute instances add-metadata INSTANCE_NAME \
    --metadata enable-oslogin=TRUE \
    --zone=us-central1-a
```

## 👨🏾‍💻 Grant OS Login Role
```bash
# Grant a user OS Login access

gcloud projects add-iam-policy-binding my-project-id \
    --member="user:example@gmail.com" \
    --role="roles/compute.osLogin"
```

## 🔎 Verify OS Login
```bash
# Check OS Login status in project metadata

gcloud compute project-info describe \
    --project my-project-id \
    --format="default(commonInstanceMetadata)"
```

## 📸 Copy Snapshot to a Secure Project
```bash
# Copy snapshot for forensic analysis

gcloud compute snapshots create forensic-copy \
    --source-snapshot=victim-disk-snapshot \
    --project=forensics-project
```

## 📜 Enable Bucket Access Logs
```bash
# Enable logging to a dedicated logs bucket

gsutil logging set on -b gs://my-logs-bucket gs://sensitive-bucket
```

## 🗑️ Disable Bucket Access Logs
```bash
# Turn off logging

gsutil logging set off gs://sensitive-bucket
```

## 📥 File Operations
```bash
# Upload a file

gsutil cp file.txt gs://my-bucket/     
```

```bash
# Download a file

gsutil cp gs://my-bucket/file.txt ./      
```

```bash
# Rename/move a file

gsutil mv gs://my-bucket/file1 gs://my-bucket/file2  
```

## 🔑 Permissions
```bash
gsutil iam get gs://my-bucket/            # View bucket IAM policy
```
```bash
gsutil iam ch user:me@example.com:objectViewer gs://my-bucket/  # Add a viewer
```
```bash
gsutil iam ch -d user:me@example.com gs://my-bucket/            # Remove a viewer            
```
## 🗑️ Deleting Files
```bash
gsutil rm gs://my-bucket/oldfile.txt      # Delete a single file
```
```bash
gsutil rm -r gs://my-bucket/oldfolder/    # Delete a folder recursively
```

