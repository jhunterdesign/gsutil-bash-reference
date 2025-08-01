# 📘 gsutil Basics Cheat She

**Scenario:** A quick reference for the most common `gsutil` commands used in cloud security and daily operations.

---

## 🪣 Bucket Management
```bash
# Create a new bucket
gsutil mb gs://my-bucket/
```

```bash
# Remove an existing bucket
gsutil rb gs://my-bucket/
```
```bash
# List all buckets in the current project
gsutil ls
```

### 🗄️File Operations

```bash
# Upload a file to a bucket
gsutil cp file.txt gs://my-bucket/
```
```bash
# Download a file from a bucket
gsutil cp gs://my-bucket/file.txt ./file.txt
```
```bash
# Upload a folder recursively
gsutil cp -r ./local-folder gs://my-bucket/
```
```bash
# Download a folder recursively
gsutil cp -r gs://my-bucket/folder ./local-folder
```

### 🗝️ Permissions and IAM
```bash
# View the IAM policy for a bucket
gsutil iam get gs://my-bucket/
```
```bash
# Add an objectViewer role to a user
gsutil iam ch user:example@gmail.com:objectViewer gs://my-bucket/
```
```bash
# Remove permissions for a user
gsutil iam ch -d user:example@gmail.com gs://my-bucket/
```
### 🔎 Object Listing & Info
```bash
# List objects in a bucket
gsutil ls gs://my-bucket/
```
```bash
# List objects with details
gsutil ls -l gs://my-bucket/
```
```bash
# Get metadata for a specific object
gsutil stat gs://my-bucket/file.txt
```
### 🔐 Versioning & Lifecycle
```bash
# Enable versioning on a bucket
gsutil versioning set on gs://my-bucket/
```
```bash
# Disable versioning on a bucket
gsutil versioning set off gs://my-bucket/
```
```bash
# Get current versioning status
gsutil versioning get gs://my-bucket/
```
### 🚮 Deleting Objects
```bash
# Delete a single object
gsutil rm gs://my-bucket/oldfile.txt
```
```bash
# Delete a folder (recursively)
gsutil rm -r gs://my-bucket/old-folder/
```