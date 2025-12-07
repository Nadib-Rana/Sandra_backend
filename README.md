# Sandra_backend
Service-Based Platform
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
