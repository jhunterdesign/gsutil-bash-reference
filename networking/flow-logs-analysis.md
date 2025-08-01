# 🌐 Use Case: Analyzing VPC Flow Logs

**Scenario:** You need to monitor and analyze traffic to detect unusual patterns, troubleshoot connectivity issues, or investigate suspicious activity in your VPC subnets.

---

## 📊 Enable Flow Logs on a Subnet
```bash
# Enable flow logs for the frontend subnet
gcloud compute networks subnets update frontend-subnet \
    --enable-flow-logs \
    --region=us-central1
```
### 📁 View Flow Logs in Cloud Logging
```bash
# List recent VPC Flow Logs from Cloud Logging
gcloud logging read "resource.type=gce_subnetwork" \
    --limit=20 --format="table(timestamp, jsonPayload.connection, jsonPayload.reporter)"
```
### 📤 Export Flow Logs to BigQuery
```bash
# Create a logging sink to export flow logs to BigQuery for deeper analysis
gcloud logging sinks create flow-logs-sink \
    bigquery.googleapis.com/projects/my-project-id/datasets/flow_logs_dataset \
    --log-filter="resource.type=gce_subnetwork"
```
### 📥 Export Flow Logs to Cloud Storage
```bash
# Create a logging sink to export flow logs to a Cloud Storage bucket
gcloud logging sinks create flow-logs-gcs-sink \
    storage.googleapis.com/my-secure-logs-bucket \
    --log-filter="resource.type=gce_subnetwork"
```
### 🔍 Analyze Flow Logs with Filters
```bash
# Read only denied connections from VPC Flow Logs
gcloud logging read 'jsonPayload.connection.refused=true' \
    --limit=10 --format="table(timestamp, jsonPayload.connection, jsonPayload.reporter)"
```


# ⚡ Best Practice Notes
<ul>
<li>Always export logs to a separate project or BigQuery dataset for forensic integrity.

<li>Filter for denied traffic and suspicious sources as part of threat hunting.

<li>Use IAM to restrict who can query or manage the flow log exports.

<li>Regularly review logs for spikes in unexpected traffic.
</ul>