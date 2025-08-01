# Use Case: Managing Service Accounts in Google Cloud

**Scenario:** You need to create and manage service accounts to control how applications and VMs authenticate to Google Cloud resources.

---

## 🔹 Create a New Service Account
```bash
gcloud iam service-accounts create my-service-account \
    --description="Service account for compute engine" \
    --display-name="Compute Engine SA"
```
## 🔹 List service accounts
```bash
# List all service accounts in the current project
gcloud iam service-accounts list
```

## 👍🏾 Assign a Role to a **Service Account**
```bash
# Assign the Storage Admin role to the service account
gcloud projects add-iam-policy-binding my-project-id \
    --member="serviceAccount:my-service-account@my-project-id.iam.gserviceaccount.com" \
    --role="roles/storage.admin"
```

## 🗝️ Generate a key file (Use with caution ⚠️)
```bash
# Generate a JSON key for the service account (store securely)
gcloud iam service-accounts keys create ~/key.json \
    --iam-account=my-service-account@my-project-id.iam.gserviceaccount.com
```

## 🗝️ Authenticate with the Key File
```bash
# Authenticate gcloud using the service account key
gcloud auth activate-service-account \
    my-service-account@my-project-id.iam.gserviceaccount.com \
    --key-file=~/key.json
```

## 🔹Remove a Role Binding
```bash
# Remove the Storage Admin role from the service account
gcloud projects remove-iam-policy-binding my-project-id \
    --member="serviceAccount:my-service-account@my-project-id.iam.gserviceaccount.com" \
    --role="roles/storage.admin"
