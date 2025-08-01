# 🔐 Use Case: Encrypting Data with Customer-Supplied Encryption Keys (CSEK)

**Scenario:** By default, Google Cloud encrypts all data at rest using Google-managed keys.  
For additional control, you can provide your own AES‑256 key when uploading and managing Cloud Storage objects.

---

## 🗝️ Upload an Object with a CSEK
```bash
# Upload a file to Cloud Storage using a customer-supplied AES-256 key
gsutil -o "GSUtil:encryption_key=$(cat my-key.txt)" \
    cp sensitive-data.txt gs://secure-bucket/
```
### 📥 Download an Object with a CSEK
```bash
# Download a file that was uploaded with a CSEK
gsutil -o "GSUtil:decryption_key=$(cat my-key.txt)" \
    cp gs://secure-bucket/sensitive-data.txt ./sensitive-data.txt
```
### 🔄 Rotate a CSEK
```bash
# Rotate the encryption key for an existing object
gsutil -o "GSUtil:encryption_key=$(cat new-key.txt)" \
    cp gs://secure-bucket/sensitive-data.txt \
       gs://secure-bucket/sensitive-data.txt
```
### 🔍 Verify Encryption Metadata
```bash
# Check the encryption type of an object
gsutil stat gs://secure-bucket/sensitive-data.txt
```

# ⚡ Best Practice Notes
<ul>
<li>Store AES‑256 keys securely — never commit them to GitHub or scripts.

<li>Rotate keys regularly to reduce risk exposure.

<li>Use Customer-Managed Encryption Keys (CMEK) in Cloud KMS if you need stronger key lifecycle management.

<li>Restrict who can access the bucket and the encryption key file.
</ul>