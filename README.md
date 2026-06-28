# 🍽️ Recipe Haven

> A full-stack recipe sharing platform where food lovers can discover, create, and share recipes — with meal planning, grocery lists, real-time notifications, and more.

**Live Demo:** [recipe-haven-egaz.onrender.com](https://recipe-haven-egaz.onrender.com)

---

## Features

- **Recipe Management** — Create, edit, delete recipes with images (Cloudinary)
- **Search & Filter** — Search by title/ingredients; filter by category, diet, cooking time
- **Voice Search** — Speak your query using the mic button (Chrome/Edge)
- **User Authentication** — Register/login with Passport.js (session-based)
- **Ratings & Reviews** — 5-star rating system with comments
- **Like / Dislike** — React to recipes with toggle reactions
- **Bookmarks** — Save recipes to your personal collection
- **User Profiles** — Public profiles with recipe stats, followers, and following
- **Follow System** — Follow other users and get notified
- **Notifications** — Real-time badges for likes, comments, and follows
- **Meal Planner** — Weekly drag-and-drop meal planner (Mon–Sun)
- **Grocery Lists** — Auto-generate shopping lists from recipes
- **Email Notifications** — Gmail SMTP emails for likes, reviews, and follows
- **Newsletter** — Subscription with secure unsubscribe tokens
- **Admin Dashboard** — Analytics: top recipes, user stats, aggregated ratings
- **Pagination** — 12 recipes per page with query-preserving page links

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Runtime | Node.js |
| Framework | Express.js |
| Database | MongoDB + Mongoose |
| Templating | EJS + ejs-mate |
| Auth | Passport.js (Local Strategy) |
| File Upload | Multer + Cloudinary |
| Email | Nodemailer (Gmail SMTP) |
| Validation | Joi |
| Frontend | Bootstrap 5 + Custom CSS |
| Sessions | express-session + connect-mongo |

---

## Project Structure

```
RECIPEHEAVEN/
├── app.js                  # Express app entry point
├── cloudConfig.js          # Cloudinary & multer config
├── middleware.js            # Auth, ownership, validation middleware
├── schema.js               # Joi validation schemas
├── models/
│   ├── listing.js          # Recipe model
│   ├── user.js             # User model (Passport)
│   ├── reviews.js          # Review model
│   ├── notification.js     # Notification model
│   ├── mealplan.js         # Meal plan model
│   ├── grocerylist.js      # Grocery list model
│   └── subscriber.js       # Newsletter subscriber model
├── routes/                 # Express routers
├── controllers/            # Route handler logic
├── views/                  # EJS templates
│   ├── listings/           # Recipe pages
│   ├── user/               # Auth & profile pages
│   ├── mealplan/           # Meal planner UI
│   ├── grocery/            # Grocery list UI
│   ├── notifications/      # Notifications page
│   └── admin/              # Admin dashboard
├── public/
│   ├── css/
│   ├── js/script.js
│   └── images/
└── utils/
    ├── expressError.js
    ├── wrapAsync.js
    └── mailer.js           # Email templates & sender
```

---

## Getting Started

### Prerequisites

- Node.js v18+
- MongoDB Atlas account (or local MongoDB)
- Cloudinary account
- Gmail account with App Password enabled

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/hassan1032/RecipeHaven.git
cd RecipeHaven

# 2. Install dependencies
npm install

# 3. Create .env file (see below)

# 4. Start the server
node app.js
```

Visit `http://localhost:5000`

---

## Environment Variables

Create a `.env` file in the root directory:

```env
PORT=5000
MONGO_URL=your_mongodb_connection_string
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
SECRET=your_session_secret

# Optional — enables email notifications
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASS=your_16_char_app_password
BASE_URL=http://localhost:5000
```

> **Gmail App Password:** Go to Google Account → Security → 2-Step Verification → App passwords → Create one.

---

## Admin Access

To make a user an admin, update their role in MongoDB:

```js
db.users.updateOne({ username: "yourusername" }, { $set: { role: "admin" } })
```

Admin dashboard is available at `/admin/dashboard`.

---

## API Endpoints (Key Routes)

| Method | Route | Description |
|--------|-------|-------------|
| GET | `/listings` | All recipes (search, filter, paginate) |
| POST | `/listings` | Create recipe |
| GET | `/listings/:id` | View single recipe |
| PUT | `/listings/:id` | Edit recipe |
| DELETE | `/listings/:id` | Delete recipe |
| POST | `/listings/:id/like` | Like / unlike |
| POST | `/listings/:id/reviews` | Add review |
| POST | `/listings/:id/save` | Bookmark recipe |
| GET | `/profile/:username` | User profile |
| POST | `/user/:id/follow` | Follow / unfollow user |
| GET | `/mealplan` | Weekly meal planner |
| GET | `/grocery` | Grocery lists |
| GET | `/notifications` | User notifications |
| GET | `/admin/dashboard` | Admin analytics |

---

## Screenshots

> Browse recipes, search by voice, plan your week, and manage your shopping list — all in one place.

![Listings Page](public/images/screenshot-listings.png)

---

## License

This project is for educational purposes.

---

Built with by Hassan khan | Final Year Project
