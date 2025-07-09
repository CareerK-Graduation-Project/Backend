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
- `GET /api/job-post/:id` – Get job post details  
- `PUT /api/job-post/:id` – Update job post **(Auth: Owner)**  
- `DELETE /api/job-post/:id` – Delete job post **(Auth: Owner)**  
- `GET /api/job-post/filter/recently-posted` – Get recently posted jobs  

### Job Applications
- `POST /api/job-application/apply/:jobId` – Apply to job **(Auth: Developer)**  
- `GET /api/job-application/:jobId/applications` – View applicants **(Auth: Company)**  
- `DELETE /api/job-application/:application_id` – Withdraw application **(Auth: Owner)**  
- `PUT /api/job-application/:applicationId/status` – Update application status **(Auth: Company)**  

---

## 🛠️ Service Board

### Service Posts
- `POST /api/service-post/create` – Create a service post **(Auth: Customer)**  
- `GET /api/service-post/:id` – Get service post details  
- `PUT /api/service-post/:id` – Update service post **(Auth: Owner)**  
- `DELETE /api/service-post/:id` – Delete service post **(Auth: Owner)**
- `GET /api/service-post/filter/recently-posted` – Get recently posted services 

### Service Applications
- `POST /api/service-application/apply` – Apply to service **(Auth: Developer)**  
- `GET /api/service-application/post/:service_post_id` – View applicants **(Auth: Customer)**  
- `GET /api/service-application/:id` – Get application details **(Auth: Involved parties)**  
- `DELETE /api/service-application/:id` – Delete application **(Auth: Developer)**  
- `PATCH /api/service-application/:id/status` – Update application status **(Auth: Developer)**  

---

## 🎯 Job Recommendations
- `GET /api/recommendations` – Personalized job/service recommendations **(Auth: Logged-in user)**  

---

## 🏠 Homepages 

### Developer
- `GET /api/developer/name` – Developer homepage name **(Auth: Developer)**  
- `GET /api/developer/courses` – Developer homepage courses **(Auth: Developer)**
- `GET /api/developer/courses?limit=6 or any number` – the same as above but with limited courses **(Auth: Developer)**
- `GET /api/developer/tracks` – Developer homepage tracks **(Auth: Developer)** 
- `GET /api/developer/:trackId/courses` – Developer homepage tracks based on tags **(Auth: Developer)**  **(For mobile only)**

### Company
- `GET /api/company/homepage` – Company homepage **(Auth: Company)**  
- `GET /api/company/:developerId/cv` – View developer's CV  
- `GET /api/company/application/:applicationId` – View application details  

### Customer
- `GET /api/customer/homepage` – Customer homepage **(Auth: Customer)**  

---

## 📄 CV Generation (AI)

- `POST /api/cv-generation/session` – Start session (form) (Auth: Developer)
- `PUT /api/cv-generation/:sessionId/data` – Update data (form) (Auth: Developer) 
- `PUT /api/cv-generation/:sessionId/data?replace=true` – to fully overwrite old data (Auth: Developer) 
- `GET /api/cv-generation/session/:sessionId` – Get data of session (Auth: Developer) (For Web Only)
- `GET /api/cv-generation/active-session` – Get last/active session ID (Auth: Developer) (For Web Only)
- `POST /api/cv-generation/:sessionId/generate` – Generate CV (Auth: Developer)

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

## Developer Profile

- `GET /api/developer/profile` – View developer profile (Auth: Developer)
- `PATCH /api/developer/edit-profile` – Update/edit developer profile (Auth: Developer)
- `GET /api/developer/my-applications` – Get developer applications (Auth: Developer)
- `GET /api/developer/my-cv` – Get developer cv (Auth: Developer)
- `PUT /api/developer/my-cv` – Update developer cv (Auth: Developer)
- `DELETE /api/developer/my-cv` – Delete developer cv (Auth: Developer)

## 🏢 Company Profile

- `GET /api/company/profile` – View company profile
- `GET /api/company/job-posts` – Get job posts
- `GET /api/company/applicants` – Get applicants
- `GET /api/company/job-posts-with-applicants` – Get job posts with applicants number
- `GET /api/company/job-posts-with-applicant-details` – Get job posts with applicant details
- `DELETE /api/company/job-posts/:jobId` – Delete a specific job post
- `PATCH /api/company/edit-profile` – edit a company profile

---

## 🏢 Customer Profile

- `GET /api/customer/profile` – View customer profile
- `GET /api/customer/service-posts` – Get service posts
- `GET /api/customer/applicants` – Get applicants
- `GET /api/customer/service-posts-with-applicants` – Get service posts with applicants number
- `GET /api/customer/service-posts-with-applicant-details` – Get service posts with applicant details
- `DELETE /api/customer/service-posts/:postId` – Delete a specific service post
- `PATCH /api/customer/edit-profile` – Edit a customer profile

---

## 📌 Bookmarks

- `POST /api/bookmarks/` – Bookmark a job/service post (Auth: Developer)
- `GET /api/bookmarks/` – Get all bookmarks (Auth: Developer)
- `GET /api/bookmarks/?postType=job/service` – Get all bookmarks (Auth: Developer) (optional)
- `GET /api/bookmarks/bookmark/:postId` – GET one bookmark (Auth: Developer)

---

## 🔔 Notifications

- `GET /api/notifications/` – Get all notifications (Auth: Logged-in user)
- `PATCH /api/notifications/:id/read` – Mark one notification as read (Auth: Logged-in user)
- `PATCH /api/notifications/read-all` – Mark all notifications as read (Auth: Logged-in user)

---

## 📚 Courses & Tracks & Roadmaps

### 📚 Courses Page 

- `GET /api/courses-page/developer-name` – Retrieve developer profile (Auth: Logged-in user)
- `GET /api/courses-page/search-courses` – Search for courses (Auth: None)
- `GET /api/courses-page/roadmaps/preview` – Get preview of tracks/roadmaps (Auth: None)
- `GET /api/courses-page/courses/ongoing` – Get ongoing courses for developer (Auth: Logged-in user)
- `GET /api/courses-page/courses/ongoing?status=completed` – Get completed courses for developer (Auth: Logged-in user)
- `GET /api/courses-page/courses/related` – Get related courses for developer (Auth: Logged-in user)

---

### 📚 Course Enrollment and Progress 

- `POST /api/course-enrollment/enroll/:courseId` – Enroll in a course (Auth: Logged-in user)
- `POST /api/course-enrollment/lessons/complete` – Mark a lesson as complete (Auth: Logged-in user)

---

### 📚 Tracks and Courses

- `GET /api/tracks-page/tracks` – Retrieve all tracks (Auth: Logged-in user)
- `GET /api/tracks-page/tracks/:trackId/courses` – Get courses for a specific track (Auth: Logged-in user)

---

### 📚 Course Details 

- `GET /api/course-details/:courseId/header` – Retrieve course header information (Auth: Logged-in user)
- `GET /api/course-details/:courseId/overview` – Get course overview (Auth: Logged-in user)
- `GET /api/course-details/:courseId/contents` – Get course contents (Auth: Logged-in user)
- `GET /api/course-details/:courseId/reviews` – Get course reviews (Auth: Logged-in user)

---

### 📚 Course Bookmarks

- ` POST /api/course-bookmarks/bookmark` – Bookmark/unbookmark a course (body: { courseId }) (Auth: Logged-in user)
- ` GET /api/course-bookmarks/bookmarks` – Get all course bookmarked (Auth: Logged-in user)
- ` GET /api/course-bookmarks/:courseId/is-bookmarked` – Check if course is bookmarked (Auth: Logged-in user)

### 🗺️ Roadmaps Steps and Progress

- `GET /api/roadmaps/:roadmapId/progress` – Get roadmap progress (Auth: Logged-in user)
- `GET /api/roadmaps/:trackId/:level` – Get roadmaps for specific track (Auth: Logged-in user)
- `POST /api/roadmaps/progress` – mark/unmark steps as done (Auth: Logged-in user)

---

## Cv Download

- ` GET /api/cv/download?type=job_application&id=<job_application_id>` – job application cv-download
- ` GET /api/cv/download?type=service_application&id=<service_application_id>` – service application cv download
- ` GET /api/cv/download?type=developer&id=<developer_id>&subtype=uploaded` – developer uploaded cv download
- ` GET /api/cv/download?type=developer&id=<developer_id>&subtype=generated` – developer generated cv download

---

## Chatbot

- ` POST /api/chatbot/ask` – Talk with chatbot
