# Host a Static Website on AWS S3

This repository provides a **template** and a **step-by-step guide** for hosting a simple static website (HTML, CSS, JS) on **Amazon S3**.

---

## 🚀 Advantages

- **Low Cost:** Pay only for S3 storage and data transfer.  
- **High Scalability:** S3 scales automatically to handle any amount of traffic.  
- **High Availability:** S3 is designed for 99.999999999% (11 9's) of durability and high availability.  
- **Serverless:** No web servers to manage, patch, or maintain.  

---

## 🧩 Prerequisites

- An active **AWS Account**

---

## 🛠️ Deployment Steps

Follow these steps to deploy the sample website in the `/Website` folder or your own static site.

---

### **Step 1: Create an S3 Bucket**

1. Sign in to the **AWS Management Console** and navigate to the **S3 service**.  
2. Click **Create bucket**.  
3. Enter a globally unique bucket name (e.g., `my-unique-static-site`).  
4. Select your desired **AWS Region** (e.g., `us-east-1`).  
5. Click **Create bucket** at the bottom of the page.  

---

### **Step 2: Upload Your Website Files**

1. Open the bucket you just created.  
2. Upload your static website files.  
   - You can drag and drop the contents of the `/Website` folder from this repository (`index.html`, `error.html`, and the `css` folder) directly into the bucket.  

---

### **Step 3: Configure Public Access**

To allow S3 to serve your files as a website, you must enable public read access.

1. In your bucket, go to the **Permissions** tab.  
2. Under **Block public access (bucket settings)**, click **Edit**.  
3. Uncheck **"Block all public access"**.  
4. Click **Save changes** and confirm your choice.  
5. Scroll down to **Bucket policy** and click **Edit**.  
6. Paste the following JSON policy, replacing `[YOUR_BUCKET_NAME]` with your actual bucket name:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::[YOUR_BUCKET_NAME]/*"
        }
    ]
}
````

7. Click **Save changes**.

---

### **Step 4: Enable Static Website Hosting**

1. Go to your bucket’s **Properties** tab.
2. Scroll down to the bottom to find **Static website hosting** and click **Edit**.
3. Select **Enable**.
4. In the **Index document** field, enter `index.html`.
5. (Optional but recommended) In the **Error document** field, enter `error.html`.
6. Click **Save changes**.

---

### **Step 5: Test Your Website**

1. Return to the **Properties** tab and scroll down to the **Static website hosting** section.
2. Your website is now live!
3. Access it using the **Bucket website endpoint URL** shown in this section.

It will look something like this:

```
http://[YOUR_BUCKET_NAME].s3-website-[YOUR_REGION].amazonaws.com
```

---

✅ **Your static website is now successfully hosted on AWS S3!**


Would you like me to include an example folder structure (like `/Website/index.html`, `/Website/css/style.css`) at the top too? It makes the README more complete for GitHub.
```
