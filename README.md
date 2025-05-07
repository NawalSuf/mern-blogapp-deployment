# 🌐 MERN Stack Blog Application Deployment on AWS – Week-10 Project

Welcome to the deployment project for a fully functional MERN Stack Blog App on AWS!  
This assignment demonstrates practical DevOps skills including cloud provisioning, environment configuration, deployment, and security best practices using AWS Free Tier services.

---

## 📚 Project Overview

- **Frontend**: React + Vite
- **Backend**: Express.js + Node.js
- **Database**: MongoDB Atlas (NoSQL cloud DB)
- **Cloud Platform**: Amazon Web Services (AWS)
- **Hosting Services**: EC2, S3, IAM

---

## 🛠️ Architecture Summary

[ MongoDB Atlas ]
│
▼
[ EC2 Instance ]
└── Backend (Express)
│
▼
[ S3 Bucket ]
└── Frontend (React)
└── Media Uploads


## 🚀 Deployment Summary

### ✅ Backend

- EC2 instance (`t3.micro`) launched in **eu-north-1**
- Installed `Node.js`, `pm2`, `AWS CLI`, `mongosh`
- Deployed backend with environment variables
- Started server with `pm2`

### ✅ Frontend

- Built React app using `pnpm`
- Configured `.env` with EC2 DNS and media bucket
- Uploaded `dist/` directory to S3 static hosting

### ✅ Database

- Used default connection string provided in assignment
- Connected via `MONGODB_URI` in backend `.env`

---

## 🔐 IAM & S3 Configuration

### Frontend Bucket: `nawal-blogapp-frontend`
- Static website hosting enabled
- Bucket policy allows `s3:GetObject` for public access

### Media Bucket: `nawal-blogapp-media`
- Public access disabled
- Custom IAM user created with limited permissions (`PUT`, `GET`, `DELETE`, `LIST`)
- CORS configuration set for browser support

### IAM User: `blogapp-user`
- Access key & secret key stored in `.env` (never exposed)
- Deleted after deployment

---

## 📦 Environment Files

### backend/.env

```env
PORT=5000
HOST=0.0.0.0
MODE=production
MONGODB=***REMOVED***test:***REMOVED***@mongodb.txkjsso.mongodb.net/blog-app
JWT_SECRET=...
JWT_EXPIRE=30min
JWT_REFRESH=...
JWT_REFRESH_EXPIRE=3d
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
AWS_REGION=eu-north-1
S3_BUCKET=nawal-blogapp-media
MEDIA_BASE_URL=https://nawal-blogapp-media.s3.eu-north-1.amazonaws.com
DEFAULT_PAGINATION=20
frontend/.env

VITE_BASE_URL=http://ec2-16-16-91-238.eu-north-1.compute.amazonaws.com:5000/api
VITE_MEDIA_BASE_URL=https://nawal-blogapp-media.s3.eu-north-1.amazonaws.com
📸 Screenshots
Backend running on EC2 via pm2
Frontend live on S3 Static Website
HTTP 200 OK via curl
Media uploaded to S3 bucket successfully

🔍 Key Learnings
Deploying full-stack applications on cloud platforms

Managing secure environment variables

Using AWS services with IAM-based permissions

Hosting static websites via S3

Automation with pm2 for backend services

✅ Success Checklist
 Frontend loads via public S3 URL

 Backend online with valid EC2 DNS

 MongoDB Atlas connection is active

 Media uploads successfully to S3

 All AWS credentials are secured & cleaned up

🧼 Cleanup Summary
 EC2 instance stopped

 IAM credentials removed

 All deployed resources ready for teardown post-evaluation

📎 Project URL
🔗 Live App:
http://nawal-blogapp-frontend.s3-website.eu-north-1.amazonaws.com

Submitted by: Nawal AlSufyani
Bootcamp: Clarusway – Infrastructure Track
Week: 10
Date: May 2025