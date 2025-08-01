# 🖥️ Use Case: Managing VM Access with OS Login

**Scenario:** Manage SSH access to Google Compute Engine VMs using IAM roles instead of manually distributing SSH keys.  
This ensures centralized control and reduces the risk of orphaned SSH keys.

---

## 🔑 Enable OS Login at the Project Level
```bash
# Apply OS Login metadata to all VMs in the project
gcloud compute project-inf
```
### 🧑🏾‍💻 Enable OS Login for a Single VM
```bash
# Apply OS Login metadata to one specific VM
gcloud compute instances add-metadata INSTANCE_NAME \
    --metadata enable-oslogin=TRUE \
    --zone=us-central1-a
```
### 👤 Grant OS Login Role to a User
```bash
# Grant a user standard OS Login access (no sudo privileges)
gcloud projects add-iam-policy-binding my-project-id \
    --member="user:example@gmail.com" \
    --role="roles/compute.osLogin"
```
### 🧑🏾‍💻 Grant OS Admin Login Role (with sudo access)
```bash
# Grant a user OS Login with admin privileges
gcloud projects add-iam-policy-binding my-project-id \
    --member="user:example@gmail.com" \
    --role="roles/compute.osAdminLogin"
```
### 🔎 Verify Login Status
```bash
# Check if OS Login is enabled in project metadata
gcloud compute project-info describe \
    --project my-project-id \
    --format="default(commonInstanceMetadata)"
```
