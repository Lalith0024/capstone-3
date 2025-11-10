# Capstone 3 - MERN Stack Application

A full-stack web application built with MongoDB, Express.js, React, and Node.js featuring user authentication and product management.

## Features

- User Authentication (Sign Up & Login)
- JWT-based token authentication
- Protected routes
- Product listing
- Responsive design with modern UI
- Toast notifications for user feedback

## Tech Stack

### Backend
- Node.js
- Express.js
- MongoDB (Mongoose)
- JWT (JSON Web Tokens)
- bcrypt (Password hashing)
- Joi (Validation)

### Frontend
- React
- React Router DOM
- React Toastify
- Fetch API

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or MongoDB Atlas)
- npm or yarn

## Setup Instructions

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the backend directory:
```env
PORT=8080
MONGODB_URI=mongodb://localhost:27017/your-database-name
JWT_SECRET=your-secret-jwt-key-change-this-in-production
```

4. Start the backend server:
```bash
npm start
```

The server will run on `http://localhost:8080`

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the frontend directory (optional, defaults to localhost:8080):
```env
REACT_APP_API_URL=http://localhost:8080
```

4. Start the frontend development server:
```bash
npm start
```

The application will open in your browser at `http://localhost:3000`

## Project Structure

```
capstone-3/
├── backend/
│   ├── controller/
│   │   └── authController.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── authvalidation.js
│   ├── models/
│   │   ├── db.js
│   │   └── user.js
│   ├── routes/
│   │   ├── authRouter.js
│   │   └── productroute.js
│   ├── index.js
│   └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── home.js
│   │   │   ├── login.js
│   │   │   └── signup.js
│   │   ├── config.js
│   │   ├── utils.js
│   │   ├── App.js
│   │   └── index.js
│   └── package.json
└── README.md
```

## API Endpoints

### Authentication
- `POST /auth/signup` - Register a new user
- `POST /auth/login` - Login user

### Products
- `GET /products` - Get all products (Protected route, requires JWT token)

## Environment Variables

### Backend (.env)
- `PORT` - Server port (default: 8080)
- `MONGODB_URI` - MongoDB connection string
- `JWT_SECRET` - Secret key for JWT token signing

### Frontend (.env)
- `REACT_APP_API_URL` - Backend API URL (default: http://localhost:8080)

## Deployment

### Backend Deployment
1. Set up environment variables on your hosting platform
2. Ensure MongoDB is accessible (use MongoDB Atlas for cloud hosting)
3. Deploy to platforms like Heroku, Vercel, or Railway

### Frontend Deployment
1. Update `REACT_APP_API_URL` in `.env` to point to your deployed backend
2. Build the React app:
```bash
npm run build
```
3. Deploy the `build` folder to platforms like Vercel, Netlify, or GitHub Pages

## Usage

1. Start both backend and frontend servers
2. Open the application in your browser
3. Register a new account or login with existing credentials
4. View products on the home page
5. Logout when done

## Notes

- Make sure MongoDB is running before starting the backend server
- For production, use a strong JWT_SECRET
- Update CORS settings if deploying to different domains
- Ensure environment variables are set correctly for deployment

## License

ISC

