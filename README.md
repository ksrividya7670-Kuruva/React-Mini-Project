# Workout Buddy - MERN Stack Application

A full-stack CRUD application built with MongoDB, Express, React, and Node.js. Track your workouts with a clean, responsive UI using React Context API for state management.

## Features

✅ **Create workouts** - Add workout title, load (Kgs), and reps  
✅ **Read workouts** - View all workouts with timestamps  
✅ **Delete workouts** - Remove workouts from the list  
✅ **Real-time updates** - Instant UI updates after CRUD operations  
✅ **Error handling** - Backend validation and frontend error display  
✅ **Responsive design** - Desktop (2 columns) and mobile (stacked) layouts  
✅ **State management** - React Context API + useReducer  

## Tech Stack

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB Atlas** - Cloud database
- **Mongoose** - MongoDB ODM
- **CORS** - Cross-origin resource sharing
- **Dotenv** - Environment variables

### Frontend
- **React** - UI library
- **React Context API** - Global state management
- **React Hooks** - useReducer, useState, useEffect, useContext
- **CSS3** - Responsive styling

## Project Structure

```
workout-buddy/
├── backend/
│   ├── models/
│   │   └── Workout.js          # Mongoose schema
│   ├── routes/
│   │   └── workouts.js         # API routes
│   ├── controllers/
│   │   └── workoutController.js # Route handlers
│   ├── server.js               # Express server entry point
│   ├── package.json
│   ├── .env.example
│   └── .gitignore
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── WorkoutsList.js
│   │   │   ├── WorkoutsList.css
│   │   │   ├── WorkoutCard.js
│   │   │   ├── WorkoutCard.css
│   │   │   ├── WorkoutForm.js
│   │   │   └── WorkoutForm.css
│   │   ├── context/
│   │   │   ├── WorkoutsContext.js   # Context provider
│   │   │   └── workoutReducer.js    # Reducer logic
│   │   ├── App.js
│   │   ├── App.css
│   │   ├── index.js
│   │   └── index.css
│   ├── package.json
│   ├── .gitignore
│   └── public/
│       └── index.html
│
└── README.md
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/workouts` | Fetch all workouts (latest first) |
| POST | `/api/workouts` | Create a new workout |
| DELETE | `/api/workouts/:id` | Delete a workout by ID |

### Request/Response Examples

**GET /api/workouts**
```json
[
  {
    "_id": "507f1f77bcf86cd799439011",
    "title": "Chest",
    "load": 50,
    "reps": 10,
    "createdAt": "2024-01-15T10:30:00Z",
    "updatedAt": "2024-01-15T10:30:00Z"
  }
]
```

**POST /api/workouts**
```json
{
  "title": "Chest",
  "load": 50,
  "reps": 10
}
```

## Setup & Installation

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- MongoDB Atlas account (free tier available)

### Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file (copy from `.env.example`):
```bash
MONGO_URI=mongodb+srv://your-username:your-password@cluster.mongodb.net/workout-buddy?retryWrites=true&w=majority
PORT=4000
```

4. Start the server:
```bash
# Development mode with auto-reload
npm run dev

# Or production mode
npm start
```

The backend will run on `http://localhost:4000`

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm start
```

The frontend will run on `http://localhost:3000` and automatically opens in your browser.

## Running Both Servers

**Option 1: Two Terminal Windows**

Terminal 1 (Backend):
```bash
cd backend
npm run dev
```

Terminal 2 (Frontend):
```bash
cd frontend
npm start
```

**Option 2: Concurrently (from root)**
```bash
# Install concurrently globally or add to root package.json
npm install -g concurrently

# Run from project root
concurrently "cd backend && npm run dev" "cd frontend && npm start"
```

## Error Handling

### Backend Validation
- **400 Bad Request**: Missing required fields or invalid data types
- **404 Not Found**: Workout ID doesn't exist
- **500 Internal Server Error**: Server-side issues

### Frontend Error Display
- Error messages appear in a red banner above the form
- Form validation prevents invalid submissions
- Loading state prevents double submissions

## Responsive Design

**Desktop (> 768px)**
- 2-column layout: Workouts list on left, form on right
- Form is sticky (stays visible while scrolling)

**Mobile (≤ 768px)**
- Single column stacked layout
- Form appears below workouts list

## State Management (Context API)

### WorkoutsContext
Provides global state and actions:
- `workouts` - Array of workout objects
- `error` - Error message string
- `fetchWorkouts()` - Fetch all workouts from backend
- `addWorkout(data)` - Add new workout
- `deleteWorkout(id)` - Delete workout by ID

### workoutReducer
Handles state updates:
- `SET_WORKOUTS` - Initialize workouts list
- `ADD_WORKOUT` - Add workout to state
- `DELETE_WORKOUT` - Remove workout from state
- `SET_ERROR` - Set error message

## Future Enhancements

- User authentication & authorization
- Edit/update workouts
- Filter and sort workouts
- Workout categories/exercises
- Progress tracking & analytics
- Mobile app (React Native)
- Dark mode

## Troubleshooting

**"Cannot POST /api/workouts"**
- Check backend is running on port 4000
- Verify CORS is enabled in backend

**"MongoDB connection error"**
- Check MongoDB Atlas connection string in `.env`
- Ensure IP address is whitelisted in MongoDB Atlas

**Frontend shows "Failed to fetch"**
- Check backend server is running
- Verify proxy setting in frontend `package.json` matches backend port

**Validation errors not showing**
- Check browser console for error messages
- Verify error state is being set in WorkoutsContext

## License

MIT

## Author

Your Name

---

Happy coding! 💪