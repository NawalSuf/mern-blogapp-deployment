# 🌐 MERN Stack Blog App Deployment on AWS – Week-10 Project

Welcome to the deployment project for a fully functional MERN Stack Blog App on AWS!  
This project demonstrates practical DevOps skills including cloud provisioning, environment configuration, deployment, and security best practices using **AWS Free Tier services**.

---

## 📚 Project Overview

- **Frontend**: React + Vite  
- **Backend**: Express.js + Node.js  
- **Database**: MongoDB Atlas (NoSQL cloud DB)  
- **Cloud Platform**: Amazon Web Services (AWS)  
- **Hosting Services**: EC2, S3, IAM

---

## 🛠️ Architecture Summary

```
[ MongoDB Atlas ]
       │
       ▼
[ EC2 Instance ] ──► Backend (Express)
       │
       ▼
[ S3 Bucket ] ──► Frontend (React)
       │
       └──► Media Uploads
```

---

## 🚀 Deployment Summary

### ✅ Backend (EC2)

- EC2 instance type: `t3.medium` (Ubuntu 22.04, eu-north-1)
- Installed: Node.js (via nvm), pm2, AWS CLI, mongosh
- Configured backend using `.env` with environment variables
- Started server with `pm2` and ensured persistence on reboot

📸 PM2 Backend Running:  
<p align="center">
  <img src="https://raw.githubusercontent.com/NawalSuf/mern-blogapp-deployment/main/screenshot/pm2-backend-running.png" width="600" />
</p>

---

### ✅ Frontend (S3 Static Website Hosting)

- Built React app using `pnpm`
- Uploaded build directory `dist/` to S3
- Configured public access and website hosting

📸 Frontend on S3:  
<p align="center">
  <img src="https://raw.githubusercontent.com/NawalSuf/mern-blogapp-deployment/main/screenshot/s3-frontend-website.png" width="600" />
</p>

📸 HTTP 200 OK via curl:  
<p align="center">
  <img src="https://raw.githubusercontent.com/NawalSuf/mern-blogapp-deployment/main/screenshot/curl-frontend-status.png" width="600" />
</p>

---

### ✅ Database (MongoDB Atlas)

- Used provided connection string (or user-created cluster)
- Configured access from EC2 IP
- Connected successfully using `MONGODB_URI` in backend `.env`

---

### ✅ S3 Media Upload Configuration

- Created media bucket: `nawal-blogapp-media`
- Disabled public access
- Applied CORS policy for browser uploads
- Created IAM user with limited permissions (PUT, GET, DELETE, LIST)

📸 Successful Media Upload:  
<p align="center">
  <img src="https://raw.githubusercontent.com/NawalSuf/mern-blogapp-deployment/main/screenshot/media-upload-success.png" width="600" />
</p>

---

## 🔐 IAM & Environment Security

- IAM user: `blogapp-user` created for media uploads
- Access key and secret stored in `.env` only (never committed)
- Secrets fully deleted from Git history using **BFG Repo-Cleaner**
- `.env` excluded via `.gitignore`

Example `.env` values (sanitized):
```env
PORT=5000
HOST=0.0.0.0
MODE=production
MONGODB=your-mongodb-uri
JWT_SECRET=your-jwt-secret
JWT_EXPIRE=30min
JWT_REFRESH=your-jwt-refresh
JWT_REFRESH_EXPIRE=3d
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=eu-north-1
S3_BUCKET=nawal-blogapp-media
MEDIA_BASE_URL=https://nawal-blogapp-media.s3.eu-north-1.amazonaws.com
DEFAULT_PAGINATION=20
```

---

## ✅ Success Checklist

- [x] Frontend loads via public S3 URL
- [x] Backend online with valid EC2 DNS
- [x] MongoDB Atlas connection is active
- [x] Media uploads successfully to S3
- [x] AWS credentials cleaned from Git history

---

## 🧹 Post-deployment Cleanup

- EC2 instance stopped ✅  
- IAM credentials deleted ✅  
- GitHub history cleaned ✅  
- Final `.env` secrets excluded from repo ✅

---

## 📎 Project Details

- 🔗 Live App:  
  http://nawal-blogapp-frontend.s3-website.eu-north-1.amazonaws.com

- 🧑‍💻 Submitted by: **Nawal AlSufyani**  
- 📆 Week: **10**  
- 📅 Date: **May 2025**

---

## 🙌 Thanks!

This deployment was a great opportunity to practice real-world DevOps concepts including environment setup, IAM permissions, static hosting, EC2 provisioning, and Git security hygiene.
