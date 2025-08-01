# 🕵️ Use Case: Taking Forensic Snapshots of VM Disks

**Scenario:** During an incident response investigation, you need to preserve a point-in-time copy of a VM’s disk for forensic analysis without altering the original evidence.

---

## 📸 Create a Snapshot of a VM Disk
```bash
# Create a snapshot of the victim's disk for evidence preservation
gcloud compute disks snapshot victim-disk \
    --snapshot-names=victim-disk-snapshot \
    --zone=us-central1-a
```
### 🔒 Copy Snapshot to a Secure Forensics Project
```bash
# Copy the snapshot to a dedicated forensics project
gcloud compute snapshots create forensic-copy \
    --source-snapshot=victim-disk-snapshot \
    --project=forensics-project
```
### 🧾 Verify Snapshot Integrity
```bash
# List snapshots and verify details
gcloud compute snapshots list --filter="name=victim-disk-snapshot"
```
```bash
# View metadata about the snapshot
gcloud compute snapshots describe victim-disk-snapshot
```
### 🛡️ Apply IAM Restrictions to Snapshot
```bash
# Restrict access to the forensic snapshot to a specific group
gcloud compute snapshots set-iam-policy forensic-copy policy.json
```

# 🚨 Best Practice Notes
<ul>
<li>Always snapshot <b>before powering off</b> or altering a VM during incident response.

<li>Store forensic copies in a separate project to reduce risk of tampering.

<li>Document hash values (e.g., using sha256sum) if exporting the snapshot for offline analysis.

<li>Treat snapshot keys and IAM bindings as sensitive evidence-handling artifacts.</ul>