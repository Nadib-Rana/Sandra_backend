# Sandra_backend
Service-Based Platform

# **Project Database (ER):Link for View: https://dbdiagram.io/d/6935b9323c4ea889c6e06be4**
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
│   │   └── env.ts
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
│   │   │   ├── user.model.ts
│   │   │   └── user.validation.ts
│   │   │
│   │   ├── contractors/
│   │   │   ├── contractor.routes.ts
│   │   │   ├── contractor.controller.ts
│   │   │   ├── contractor.service.ts
│   │   │   ├── contractor.model.ts
│   │   │   └── contractor.validation.ts
│   │   │
│   │   ├── subscription_plans/
│   │   │   ├── subscription.routes.ts
│   │   │   ├── subscription.controller.ts
│   │   │   ├── subscription.service.ts
│   │   │   ├── subscription.model.ts
│   │   │   └── subscription.validation.ts
│   │   │
│   │   ├── jobs/
│   │   │   ├── job.routes.ts
│   │   │   ├── job.controller.ts
│   │   │   ├── job.service.ts
│   │   │   ├── job.model.ts
│   │   │   └── job.validation.ts
│   │   │
│   │   ├── bids/
│   │   │   ├── bid.routes.ts
│   │   │   ├── bid.controller.ts
│   │   │   ├── bid.service.ts
│   │   │   ├── bid.model.ts
│   │   │   └── bid.validation.ts
│   │   │
│   │   ├── reviews/
│   │   │   ├── review.routes.ts
│   │   │   ├── review.controller.ts
│   │   │   ├── review.service.ts
│   │   │   ├── review.model.ts
│   │   │   └── review.validation.ts
│   │   │
│   │   ├── messages/
│   │   │   ├── message.routes.ts
│   │   │   ├── message.controller.ts
│   │   │   ├── message.service.ts
│   │   │   ├── message.model.ts
│   │   │   └── message.validation.ts
│   │   │
│   │   ├── notifications/
│   │   │   ├── consumer_notifications/
│   │   │   │   ├── consumerNot.routes.ts
│   │   │   │   ├── consumerNot.controller.ts
│   │   │   │   ├── consumerNot.service.ts
│   │   │   │   └── consumerNot.model.ts
│   │   │   │
│   │   │   └── contractor_notifications/
│   │   │       ├── contractorNot.routes.ts
│   │   │       ├── contractorNot.controller.ts
│   │   │       ├── contractorNot.service.ts
│   │   │       └── contractorNot.model.ts
│   │   │
│   │   ├── subscription_history/
│   │   │   ├── subHistory.routes.ts
│   │   │   ├── subHistory.controller.ts
│   │   │   ├── subHistory.service.ts
│   │   │   └── subHistory.model.ts
│   │   │
│   │   ├── credit_history/
│   │       ├── creditHistory.routes.ts
│   │       ├── creditHistory.controller.ts
│   │       ├── creditHistory.service.ts
│   │       └── creditHistory.model.ts
│
│
├── README.md
```
