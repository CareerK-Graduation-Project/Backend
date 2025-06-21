# 📌 API Endpoints

## 🔐 Authentication & User Registration

### User Registration
- `POST /api/developer/register` – Register as a developer  
- `POST /api/company/register` – Register as a company  
- `POST /api/customer/register` – Register as a customer  

### Login & Password
- `POST /api/auth/login` – Login  
- `POST /api/password/forgot-password` – request password reset  
- `POST /api/password/verify-otp` – Verify OTP before password reset 
- `POST /api/password/reset-password` – Reset password  

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
- `POST /api/service-application/apply` – Apply to service **(Auth: Developer)**  
- `GET /api/service-application/post/:service_post_id` – View applicants **(Auth: Customer)**  
- `GET /api/service-application/:id` – Get application details **(Auth: Involved parties)**  
- `DELETE /api/service-application/:id` – Delete application **(Auth: Developer)**  

---

## 🎯 Job Recommendations
- `GET /api/recommendations` – Personalized job/service recommendations **(Auth: Logged-in user)**  

---

## 🏠 Homepages 

### Developer
- `GET /api/developer/homepage` – Developer homepage **(Auth: Developer)**  

### Company
- `GET /api/company/homepage` – Company homepage **(Auth: Company)**  
- `GET /api/company/:developerId/cv` – View developer's CV  
- `GET /api/company/application/:applicationId` – View application details  

### Customer
- `GET /api/customer/homepage` – Customer homepage **(Auth: Customer)**  

---

## 📄 CV Generation (AI)

- `POST /api/cv-generation/start` – Start session (form or chat) (Auth: Developer)
- `PUT /api/cv-generation/update/:sessionId` – Update data (form or chat mode) (Auth: Developer)
- `GET /api/cv-generation/session/:sessionId` – Get session data (Auth: Developer)
- `POST /api/cv-generation/chat/:sessionId` – Chatbot input (Auth: Developer)
- `POST /api/cv-generation/generate/:sessionId` – Generate CV (Auth: Developer)

---

## 💬 Private Chat

Chat Rooms
- `POST /api/private-chats/start` – Start a private chat room with another user
- `POST /api/private-chats/:chatRoomId` – Send a message in a private chat room (text or file)
- `GET /api/private-chats/:chatRoomId` – Get messages from a specific private chat room
- `GET /api/private-chats` – Get all private chats for the logged-in user
- `DELETE /api/private-chats/message/:messageId` – Delete a message
- `DELETE /api/private-chats/:chatRoomId` – Delete a private chat room

Socket.IO Events
- `private:send_message` – Send message (text/file/image)
- `private:receive_message` – Receive message

---

## 🌐 Community Chat (Groups)

Group APIs
- `GET /api/community/groups` – Get all available community groups (suggested)
- `GET /api/community/groups/:groupId` – Get specific community group by ID
- `GET /api/community/my-groups` – Get groups joined by current user
- `POST /api/community/join/:groupId` – Join a community group
- `DELETE /api/community/leave/:groupId` – Leave a community group
- `GET /api/community/:groupId/messages?page=1&limit=20` – Get messages from a group (paginated)
- `POST /api/community/upload-media` – Upload file/image/audio message to a community (multipart/form-data), use (key: file) in postman)
- `GET /api/community/groups/by-interest?tag=react` – Discover groups by interest tag
- `GET /api/community/groups/search?q=keyword` – Fuzzy search for groups by name or tag

Socket.IO Events
- `community:join` – Join community group room
- `community:leave` – Leave group room
- `community:send-message` – Send message (text, image, file, or audio)
- `community:typing` – Send typing indicator to others
- `community:receive-message` – Listen for new messages

---

## 🏢 Company Profile

- `GET /api/company/profile` – View company profile
- `DELETE /api/company/profile/jobs/:jobId` – Delete a specific job post

---

📌 Bookmarks

- `POST /api/bookmarks/` – Bookmark a job/service post (Auth: Developer)
- `GET /api/bookmarks/` – Get all bookmarks (Auth: Developer)
- `GET /api/bookmarks/?postType=job/service` – Get all bookmarks (Auth: Developer) (optional)
- `GET /api/bookmarks/bookmark/:postId` – GET one bookmark (Auth: Developer)

---

🔔 Notifications

- `GET /api/notifications/` – Get all notifications (Auth: Logged-in user)
- `PATCH /api/notifications/:id/read` – Mark one notification as read (Auth: Logged-in user)
- `PATCH /api/notifications/read-all` – Mark all notifications as read (Auth: Logged-in user)

---
