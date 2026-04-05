# 🌐 Hosting a Static Website on AWS S3

![AWS](https://img.shields.io/badge/AWS-S3-orange?logo=amazonaws)
![Status](https://img.shields.io/badge/Status-Deployed-brightgreen)
![Type](https://img.shields.io/badge/Type-Cloud%20Project-blue)

A step-by-step documentation of deploying a static website on Amazon S3 — covering bucket creation, file upload, static website hosting configuration, and public access setup. This project was deployed live and tested successfully.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Tools Used](#️-tools-used)
- [Architecture](#️-architecture)
- [Step-by-Step Deployment](#-step-by-step-deployment)
- [Screenshots](#-screenshots)
- [Lessons Learned](#-lessons-learned)
- [What I Would Do Differently (Security Improvements)](#-what-i-would-do-differently-security-improvements)

---

## Overview

This project demonstrates how to host a static website using AWS S3. The site was fully deployed and accessible via the S3 static website hosting endpoint. The steps are documented in detail so the process can be repeated or adapted for future projects.

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **AWS S3** | Stores and serves the static website files |
| **AWS Console** | Used to configure the bucket settings and permissions |
| **HTML/CSS** | The website files that were uploaded and hosted |

---

## 🏗️ Architecture

```
  [User / Browser]
        |
        | HTTP Request
        v
  [AWS S3 Bucket - Static Website Hosting]
        |
        |-- index.html  (main page)
        |-- styles.css  (styling)
        |
        |-- Public Access: Enabled via ACL
        |-- Static Website Hosting: Enabled
        |-- Endpoint: http://[bucket-name].s3-website-[region].amazonaws.com
```

---

## 🚀 Step-by-Step Deployment

### Step 1 — Create an S3 Bucket

- Navigate to the **S3 service** in the AWS Console
- Click **Create Bucket**
- Enter a unique bucket name (e.g. `deborah-maiyaki-website`)
- Leave other settings as default and click **Create**
- Confirm the bucket appears in the S3 dashboard

> 📹 [Video walkthrough at 0:48](https://loom.com/share/65458e4ca6674320a59f01f817955b29?t=48)

---

### Step 2 — Upload Website Files

- Click on the created bucket to open it
- Click **Upload → Add files**
- Select your website files (`index.html`, `styles.css`, etc.)
- Click **Upload** and wait for confirmation

> 📹 [Video walkthrough at 2:36](https://loom.com/share/65458e4ca6674320a59f01f817955b29?t=156)

---

### Step 3 — Enable Static Website Hosting

- In the bucket, go to the **Properties** tab
- Scroll down to **Static website hosting**
- Click **Edit** → select **Enable**
- Set **Index document** to `index.html`
- Save changes

> 📹 [Video walkthrough at 6:03](https://loom.com/share/65458e4ca6674320a59f01f817955b29?t=363)

---

### Step 4 — Configure Bucket Permissions

- Go to the **Permissions** tab
- Click **Edit** under **Block public access**
- Uncheck **Block all public access**
- Save changes and confirm the action

> 📹 [Video walkthrough at 8:07](https://loom.com/share/65458e4ca6674320a59f01f817955b29?t=487)

---

### Step 5 — Set Object Ownership and Access Control

- Still in the **Permissions** tab, go to **Object Ownership**
- Edit settings to enable **ACLs**
- Acknowledge the changes and save

> 📹 [Video walkthrough at 10:08](https://loom.com/share/65458e4ca6674320a59f01f817955b29?t=608)

---

### Step 6 — Make Uploaded Files Public

- Select the uploaded files inside the bucket
- Click **Actions → Make public using ACL**
- Confirm that public read access is enabled

> 📹 [Video walkthrough at 11:11](https://loom.com/share/65458e4ca6674320a59f01f817955b29?t=671)

---

### Step 7 — Test Website Accessibility

- Go to **Properties → Static website hosting**
- Copy the **Bucket website endpoint** URL
- Paste the URL into a browser and confirm the website loads

> 📹 [Video walkthrough at 12:48](https://loom.com/share/65458e4ca6674320a59f01f817955b29?t=768)

---

## 📸 Screenshots

> *(Add your own screenshots to the `screenshots/` folder and update these links)*

| Step | Description |
|---|---|
| `screenshots/01-bucket-created.png` | S3 bucket successfully created |
| `screenshots/02-files-uploaded.png` | Website files uploaded to the bucket |
| `screenshots/03-static-hosting-enabled.png` | Static website hosting turned on |
| `screenshots/04-permissions-configured.png` | Block public access unchecked |
| `screenshots/05-website-live.png` | Website accessible in browser |

---

## 📚 Lessons Learned

- How to create and configure an AWS S3 bucket from scratch
- How static website hosting works on S3 — S3 serves files directly over HTTP without needing a web server
- The difference between bucket-level and object-level permissions in AWS
- How AWS ACLs (Access Control Lists) work to make objects publicly readable
- The importance of setting the correct **index document** so the browser knows which file to load first

---

## 🔐 What I Would Do Differently (Security Improvements)

This project deployed the site by making the bucket fully public using ACLs — which works, but is not the most secure approach. In a real production environment, I would improve it by:

- **Keeping Block Public Access ON** and using a bucket policy instead of ACLs for more controlled access
- **Enforcing HTTPS only** using a bucket policy condition on `aws:SecureTransport`
- **Enabling versioning** so files can be recovered if accidentally deleted or overwritten
- **Enabling server access logging** to keep an audit trail of all requests
- **Using CloudFront** in front of S3 for HTTPS support, caching, and DDoS protection

> See my related project: [Secure S3 Website with IAM Hardening](https://github.com/YOUR_USERNAME/secure-s3-website) — which implements all of these improvements.

---

## 🎥 Full Video Walkthrough

Watch the complete step-by-step deployment:
👉 [Loom Video Guide](https://loom.com/share/65458e4ca6674320a59f01f817955b29)

---

## 📁 Project Structure

```
s3-static-website/
├── README.md          # This file
├── index.html         # Main website file
├── styles.css         # Website styling
└── screenshots/       # Add your screenshots here
```

---

## 🙋 Author

**Deborah Maiyaki**
Cloud Security & DevOps Learner | Open to entry-level roles

- LinkedIn: [your-linkedin-url]
- GitHub: [your-github-url]

---

> *This project is part of my Cloud Security & DevOps portfolio. Documented to demonstrate hands-on AWS experience.*
