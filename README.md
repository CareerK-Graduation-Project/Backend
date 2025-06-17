# 📌 API Endpoints

## 🔐 Authentication & User Registration

### User Registration
- `POST /api/developer/register` – Register as a developer  
- `POST /api/company/register` – Register as a company  
- `POST /api/customer/register` – Register as a customer  

### Login & Password
- `POST /api/auth/login` – Login  
- `POST /api/password/reset` – Reset password  

---

## 💼 Job Board

### Job Posts
- `POST /api/job-post/create` – Create a job post **(Auth: Logged-in user)**  
- `GET /api/job-post/get-job-posts` – Browse all job posts *(Public)*  
- `GET /api/job-post/:id` – Get job post details  
- `PUT /api/job-post/:id` – Update job post **(Auth: Owner)**  
- `DELETE /api/job-post/:id` – Delete job post **(Auth: Owner)**  
- `GET /api/job-post/filter/most-relevant` – Get recommended jobs  
- `GET /api/job-post/filter/recently-posted` – Get recently posted jobs  

### Job Applications
- `POST /api/job-application/apply/:jobId` – Apply to job **(Auth: Developer)**  
- `GET /api/job-application/:jobId/applications` – View applicants **(Auth: Company)**  
- `GET /api/job-application/my-applications` – View my applications **(Auth: Developer)**  
- `DELETE /api/job-application/:application_id` – Withdraw application **(Auth: Owner)**  
- `PUT /api/job-application/:applicationId/status` – Update application status **(Auth: Company)**  

---

## 🛠️ Service Board

### Service Posts
- `POST /api/service-post/create` – Create a service post **(Auth: Customer)**  
- `GET /api/service-post/get-service-posts` – Browse service posts *(Public)*  
- `GET /api/service-post/:id` – Get service post details  
- `PUT /api/service-post/:id` – Update service post **(Auth: Owner)**  
- `DELETE /api/service-post/:id` – Delete service post **(Auth: Owner)**  

### Service Applications
- `POST /api/service-application/` – Apply to service **(Auth: Developer)**  
- `GET /api/service-application/post/:service_post_id` – View applicants **(Auth: Customer)**  
- `GET /api/service-application/:id` – Get application details **(Auth: Involved parties)**  
- `DELETE /api/service-application/:id` – Delete application **(Auth: Developer)**  

---

## 🎯 Recommendations
- `GET /api/recommendations` – Personalized job/service recommendations **(Auth: Logged-in user)**  

---

## 🏠 Homepages & Dashboards

### Developer
- `GET /api/developer/homepage` – Developer dashboard **(Auth: Developer)**  

### Company
- `GET /api/company/homepage` – Company dashboard **(Auth: Company)**  
- `GET /api/company/:developerId/cv` – View developer's CV  
- `GET /api/company/application/:applicationId` – View application details  

### Customer
- `GET /api/customer/homepage` – Customer dashboard **(Auth: Customer)**  
