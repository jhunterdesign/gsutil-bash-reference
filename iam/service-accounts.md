# Use Case: Managing Service Accounts in Google Cloud

**Scenario:** You need to create and manage service accounts to control how applications and VMs authenticate to Google Cloud resources.

---

## 🔹 Create a New Service Account
```bash
gcloud iam service-accounts create my-service-account \
    --description="Service account for compute engine" \
    --display-name="Compute Engine SA"


gcloud iam service-accounts list


gcloud projects add-iam-policy-binding my-project-id \
    --member="serviceAccount:my-service-account@my-project-id.iam.gserviceaccount.com" \
    --role="roles/storage.admin"


gcloud iam service-accounts keys create ~/key.json \
    --iam-account=my-service-account@my-project-id.iam.gserviceaccount.com

gcloud auth activate-service-account \
    my-service-account@my-project-id.iam.gserviceaccount.com \
    --key-file=~/key.json


gcloud projects remove-iam-policy-binding my-project-id \
    --member="serviceAccount:my-service-account@my-project-id.iam.gserviceaccount.com" \
    --role="roles/storage.admin"
