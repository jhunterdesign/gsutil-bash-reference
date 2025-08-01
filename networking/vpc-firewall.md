# 🔥 Use Case: Managing VPC Firewall Rules

**Scenario:** As a Cloud Security Engineer, you need to control traffic to and from Compute Engine instances in your VPC network for compliance, security, and incident response.

---

## ➕ Create a Firewall Rule (Allow SSH from Trusted IPs)
```bash
# Allow SSH access (TCP port 22) only from a specific IP range
gcloud compute firewall-rules create allow-ssh \
    --allow tcp:22 \
    --source-ranges=203.0.113.0/24 \
    --network=my-vpc \
    --priority=1000
```
### 🔹 List All Firewall Rules
```bash
# List all firewall rules in the project
gcloud compute firewall-rules list
```
### 🔍 Describe a Specific Firewall Rule
```bash
# View details of a specific firewall rule
gcloud compute firewall-rules describe allow-ssh
```
### ✏️ Update a Firewall Rule
```bash
# Update the source IP range for an existing firewall rule
gcloud compute firewall-rules update allow-ssh \
    --source-ranges=198.51.100.0/24
```
### ❌ Delete a Firewall Rule
```bash
# Update the source IP range for an existing firewall rule
gcloud compute firewall-rules update allow-ssh \
    --source-ranges=198.51.100.0/24
```
# ⚡ Best Practice Notes
<ul>
<li>Use the principle of least privilege: only allow traffic that is strictly required.

<li>Restrict SSH/RDP to trusted IP ranges (never 0.0.0.0/0).

<li>Use tags or service accounts to scope firewall rules to specific instances.

<li>Regularly audit firewall rules to identify overly broad or unused entries.

<li>Consider pairing firewall rules with VPC Flow Logs for monitoring.