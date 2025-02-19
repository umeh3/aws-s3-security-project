# AWS S3 Security Project 

##  Project Overview  
This project demonstrates **secure AWS S3 bucket configurations** using **IAM policies** and **CloudTrail logging** to enforce security best practices.  

### **Key Goals:**  
- Prevent **unauthorized access** to the bucket.  
- **Enforce HTTPS-only** access for security.  
- Enable **CloudTrail logging** to monitor all access attempts.  

---

## 🛠️ **Step-by-Step Implementation**  

### **1️⃣ Create an S3 Bucket (AWS Console)**  
- Go to **AWS S3** → Click **"Create Bucket"**.  
- **Bucket Name:** `mikeumeh`  
- **Block Public Access:**  **Enabled (Recommended)**  
- **Versioning:**  **Enabled (Optional for recovery)**  
- Click **"Create"**.  

---

### **2️⃣ Apply Secure S3 Bucket Policy (AWS Console)**  
- Open **AWS S3 → mikeumeh → Permissions**.  
- Scroll to **Bucket Policy** → Click **Edit**.  
- Copy and paste this policy **(343218214491)**:  

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::mikeumeh",
                "arn:aws:s3:::mikeumeh/*"
            ],
            "Condition": {
                "Bool": {
                    "aws:SecureTransport": "false"
                }
            }
        }
    ]
}
