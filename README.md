# Sandra_backend
Service-Based Platform


# Requerments:

---

# 📘 Service-Based Platform — Structural Document (Final Formatted)

---

# **1. User Roles**

## **1.1 Admin**

* Manage consumers & contractors
* Approve / monitor jobs
* Handle disputes
* View system analytics
* Manage platform settings

---

## **1.2 Consumer**

* Post jobs
* View & manage dashboard:

  * Active Jobs
  * Quotes
  * In Progress
  * Completed
* Accept/reject contractor quotes
* Communicate with contractors
* Mark job as done
* Rate & review contractors
* Manage profile & notifications

---

## **1.3 Contractor**

* Browse & search jobs
* Filter by service type, budget, and nearest location
* Submit quotes (price + details + portfolio images) , Contractors need credit to apply for jobs. Every application minus some credit (ex: minus $3 from the total credit (ex: $50)). 
* Communicate with consumers
* Update job progress
* Build reputation through ratings & completed jobs
* Manage subscription plan & profile
 By plan:
## **(Admin can change the plan (dynamic):
*  Basic plan: Limited job application, no job alerts ,pay-per-application.
*  Premium: All pro features, verified badge, free monthly credits, and highlighted listing.
*  Pro: Priority in search results, Instant job alerts, unlimited job applications, Lower lead cost
 
---

# **2. Consumer Dashboard**

## **2.1 Post a Job**

Fields:

* Service type
* Address / location
* Budget
* Description
* Upload images

---

## **2.2 Dashboard Summary**

* **Active Jobs** (e.g., 10)
* **Quotes Received** (e.g., 45)
* **Jobs In Progress** (e.g., 39)
* **Jobs Completed** (e.g., 10)

---

# **3. Consumer Job Management**

## **3.1 Active Jobs**

* Job Title
* Contractor (if assigned)
* Number of bids
* Last activity
* Action: **View Quotes**

---

## **3.2 In Progress**

* Job Title
* Contractor (name + photo)
* Expected completion date
* Actions:

  * **Message Contractor**
  * **Mark as Done**

---

## **3.3 Completed Jobs**

* Job Title
* Contractor (name + photo)
* Rating (1–5 stars)
* Completed date
* Actions:

  * **Rate & Review**
  * **Rehire Contractor**

---

# **4. Consumer – My Jobs Section**

## **4.1 Ongoing**

* Job Title
* Location
* Posted time (ex: “Posted 2 days ago”)
* Budget
* Work type
* Vehicle type
* Posted date
* Action: **See Quotes (5)**

---

## **4.2 Quotes List**

Contractor details:

* First & last name
* Profile image
* Rating (1–5)
* Bid price
* Portfolio work images
* Contractor description

Also displays:

* Consumer’s posted budget

Actions:

* **Accept**
* **Reject**

---

## **4.3 In Progress**

* Job Title
* Location
* Posted time
* Budget
* Work type
* Vehicle type
* Posted date
* Actions:

  * **Mark as Done**
  * **Message**

---

## **4.4 Completed**

* Job Title
* Location
* Posted time
* Budget
* Work type
* Vehicle type
* Contractor profile image
* Posted date
* Status: *Completed*
* Actions:

  * **Review**
  * **Rehire**

---

# **5. Messaging System**

* Real-time chat between **Consumer ↔ Contractor**
* Push notifications for new messages
* Supports text + images

---

# **6. Consumer Settings**

## **6.1 Account**

* First name
* Last name
* Email
* Phone number
* Profile URL
* Service location
* Service type
* Password management

## **6.2 Notification Settings**

* Quote Alerts
* Message Alerts
* Enable/Disable push notifications

---

# **7. Contractor Dashboard**

## **7.1 Job Search**

* Filter by:

  * Service type
  * Budget
  * Location (closest first)
* View full job details
* Submit bid

---

## **7.2 Dashboard Summary**

* **Active Bids** (ex: 10)
* **Available Credit** (ex: $45)
* **Average Rating** (ex: 4.9)
* **Jobs Completed** (ex: 150)

### **Active Jobs Section**

Tabs:

1. **Post Jobs**

   * Job title
   * Status (pending / accepted / rejected)
   * Budget
   * Last activity
   * Actions:

     * **View Details** (for pending/rejected)
     * **Message** (if accepted)

2. **In Progress**

   * Job Title
   * Consumer (name + image)
   * Budget
   * Last activity
   * Action:

     * **Mark as Done**

3. **Completed**

   * Job Title
   * Consumer details
   * Budget
   * Status: Completed
   * Action:

     * **View Review**

---

# **8. Contractor — My Bids**

## **8.1 Ongoing**

* Job Title
* Location
* Posted time (e.g., “Posted 2 days ago”)
* Budget
* Work type
* Vehicle type
* Posted date
* Actions:

  * **Message**
  * **See Details**

### **Bid Details View**

* Job title
* Budget
* Consumer’s description
* Bid information

---

## **8.2 Completed Bids**

* Job Title
* Location
* Posted time
* Budget
* Work type
* Vehicle type
* Contractor profile image
* Posted date
* Status: Completed
* Action:

  * **View Review**

---

# **9. Contractor Messaging**

* Chat with consumers
* Real-time updates
* Push notifications

---

# **10. Contractor Profile**

## **10.1 Subscription Plan**

* Current plan (Basic / Premium / Pro)
* Price (e.g., $75)
* Billing cycle (monthly)
* Next billing date (e.g., December 12, 2025)
 
---

## **10.2 Profile Information**

* First name
* Last name
* Profile URL
* Location
* Service types
* Completed jobs (ex: 250)
* Verification badge
* Member services (e.g., car repairing, restoring)

---

## **10.3 Recent Reviews**

For each review:

* Consumer name
* Image
* Date
* Rating (1–5)
* Short comment (Great, low, awesome, etc.)
* Full description
* Contractor reply

---

# **11. Contractor Settings**

## **11.1 Account**

* Edit profile:

  * First name
  * Last name
  * Email
  * Phone number
  * Profile URL
  * Service location
  * Service type
  * Password

## **11.2 Notifications**
*Notification dealy based on the subecriptions.
* consumer new post alerts
* Message alerts
* Enable push notifications

---




# **Project Database (ER):Link for DB: https://dbdiagram.io/d/6935b9323c4ea889c6e06be4**
```

Table users {
  id int [pk, increment]
  role enum('admin','consumer','contractor')
  first_name varchar
  last_name varchar
  email varchar [unique]
  phone varchar
  profile_url varchar
  password varchar
  location varchar
  service_type varchar
  created_at datetime
}

Table contractors {
  id int [pk, increment]
  user_id int [unique]
  subscription_plan_id int
  available_credit decimal
  average_rating decimal
  completed_jobs int
  verified boolean
}

Table subscription_plans {
  id int [pk, increment]
  name enum('Basic','Premium','Pro')
  price decimal
  cycle enum('monthly')
  monthly_credit decimal
  highlighted_listing boolean
  priority_search boolean
  unlimited_applications boolean
  instant_job_alerts boolean
  lower_lead_cost boolean
}

Table contractor_reviews {
  id int [pk, increment]
  contractor_id int
  consumer_id int
  rating decimal
  short_comment varchar
  full_comment text
  contractor_reply text
  created_at datetime
}

Table jobs {
  id int [pk, increment]
  consumer_id int
  service_type varchar
  post_image_url varchar
  address varchar
  budget decimal
  description text
  vehicle_type varchar
  location varchar
  status enum('active','quoted','in_progress','completed','cancelled')
  posted_at datetime
}


Table bids {
  id int [pk, increment]
  job_id int
  contractor_id int
  bid_price decimal
  description text
  prev_img_url varchar
  status enum('pending','accepted','rejected')
  created_at datetime
}



Table job_progress {
  id int [pk, increment]
  job_id int
  contractor_id int
  status enum('started','in_progress','waiting','completed')
  updated_at datetime
}

Table messages {
  id int [pk, increment]
  sender_id int
  receiver_id int
  job_id int
  message text
  image_url varchar
  created_at datetime
}

Table consumer_notifications {
  id int [pk, increment]
  consumer_id int
  quote_alerts boolean
  message_alerts boolean
  push_notifications boolean
}

Table contractor_notifications {
  id int [pk, increment]
  contractor_id int
  new_post_alert boolean
  message_alerts boolean
  push_notifications boolean
}

Table contractor_subscription_history {
  id int [pk, increment]
  contractor_id int
  subscription_plan_id int
  next_billing_date datetime
  created_at datetime
}

Table contractor_credit_history {
  id int [pk, increment]
  contractor_id int
  change_amount decimal
  description varchar
  created_at datetime
}

Ref: contractors.user_id > users.id
Ref: contractors.subscription_plan_id > subscription_plans.id
Ref: contractor_reviews.contractor_id > contractors.id
Ref: contractor_reviews.consumer_id > users.id
Ref: jobs.consumer_id > users.id

Ref: bids.job_id > jobs.id
Ref: bids.contractor_id > contractors.id
Ref: job_progress.job_id > jobs.id
Ref: job_progress.contractor_id > contractors.id
Ref: messages.sender_id > users.id
Ref: messages.receiver_id > users.id
Ref: messages.job_id > jobs.id
Ref: consumer_notifications.consumer_id > users.id
Ref: contractor_notifications.contractor_id > contractors.id
Ref: contractor_subscription_history.contractor_id > contractors.id
Ref: contractor_subscription_history.subscription_plan_id > subscription_plans.id
Ref: contractor_credit_history.contractor_id > contractors.id


```


# **Project folder stracture:**
```
project-root/
├── package.json
├── tsconfig.json
├── lib
├── prisma
├── generated
├── nodemon.json
├── .env
├── dist/                   # (auto-generated after build)
│
├── src/
│   ├── app.ts
│   ├── server.ts
│
│   ├── config/
│   │   ├── db.ts
│   │   
│
│   ├── routes/
│   │   └── index.ts
│
│   ├── middleware/
│   │   ├── auth.ts
│   │   ├── errorHandler.ts
│   │   └── validate.ts
│
│   ├── utils/
│   │   ├── password.ts
│   │   ├── jwt.ts
│   │   └── helpers.ts
│
│   ├── modules/
│   │   ├── users/
│   │   │   ├── user.routes.ts
│   │   │   ├── user.controller.ts
│   │   │   ├── user.service.ts
│   │   │   └── user.validation.ts
│   │   │
│   │   ├── contractors/
│   │   │   ├── contractor.routes.ts
│   │   │   ├── contractor.controller.ts
│   │   │   ├── contractor.service.ts
│   │   │   └── contractor.validation.ts
│   │   │
│   │   ├── subscription_plans/
│   │   │   ├── subscription.routes.ts
│   │   │   ├── subscription.controller.ts
│   │   │   ├── subscription.service.ts
│   │   │   └── subscription.validation.ts
│   │   │
│   │   ├── jobs/
│   │   │   ├── job.routes.ts
│   │   │   ├── job.controller.ts
│   │   │   ├── job.service.ts
│   │   │   └── job.validation.ts
│   │   │
│   │   ├── bids/
│   │   │   ├── bid.routes.ts
│   │   │   ├── bid.controller.ts
│   │   │   ├── bid.service.ts
│   │   │   └── bid.validation.ts
│   │   │
│   │   ├── reviews/
│   │   │   ├── review.routes.ts
│   │   │   ├── review.controller.ts
│   │   │   ├── review.service.ts
│   │   │   └── review.validation.ts
│   │   │
│   │   ├── messages/
│   │   │   ├── message.routes.ts
│   │   │   ├── message.controller.ts
│   │   │   ├── message.service.ts
│   │   │   └── message.validation.ts
│   │   │
│   │   ├── notifications/
│   │   │   ├── consumer_notifications/
│   │   │   │   ├── consumerNot.routes.ts
│   │   │   │   ├── consumerNot.controller.ts
│   │   │   │   ├── consumerNot.service.ts
│   │   │   │
│   │   │   └── contractor_notifications/
│   │   │       ├── contractorNot.routes.ts
│   │   │       ├── contractorNot.controller.ts
│   │   │       |__ contractorNot.service.ts
│   │   │
│   │   ├── subscription_history/
│   │   │   ├── subHistory.routes.ts
│   │   │   ├── subHistory.controller.ts
│   │   │   ├── subHistory.service.ts
│   │   │
│   │   ├── credit_history/
│   │       ├── creditHistory.routes.ts
│   │       ├── creditHistory.controller.ts
│   │       ├── creditHistory.service.ts
│
│
├── README.md
```
