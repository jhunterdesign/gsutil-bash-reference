# Use Case: Managing Service Accounts in Google Cloud

**Scenario:** You need to create and manage service accounts to control how applications and VMs authenticate to Google Cloud resources.

---

## 🔹 Create a New Service Account
```bash
gcloud iam service-accounts create my-service-account \
    --description="Service account for compute engine" \
    --display-name="Compute Engine SA"
