# Course Management System

A React-based course management application designed for learning and demonstration. The project provides a simple online course platform where users can sign up, log in, browse available courses, and view course details. Admin users can add, update, and delete courses.

This project is a full-stack-style demo built with a React frontend and a mock backend powered by JSON Server. It uses local storage for user session persistence and JSON data files for storing users and course records.

## Project Overview

The application simulates a small e-learning platform:

- Users can create an account and log in.
- Users can view a list of available courses.
- Users can view detailed information about a specific course.
- Admins can create, edit, and remove courses.
- Role-based access control restricts admin-only actions.

The app is built mainly for learning React routing, context APIs, forms, protected routes, and CRUD operations with JSON Server.

## Main Features

### 1. User Authentication
- Sign up page for new users
- Login page for existing users
- Role-based login system using `admin` and `user`
- Session stored in browser localStorage

### 2. Role-based Access Control
- Admin users can access:
  - Add new course
  - Update course
  - Delete course
- Normal users can access:
  - Course listing
  - Course details
  - Login and signup

### 3. Course Management
- Add a new course with fields such as:
  - course name
  - image URL
  - trainer
  - duration
  - price
  - description
- Edit a course
- Delete a course
- View a course in detail

### 4. Frontend UI
- Clean, modern UI built with Tailwind CSS
- Responsive design for different screen sizes
- Toast notifications for success and error states

### 5. Routing
The application uses `react-router-dom` to manage pages such as:
- `/` – Home / course list
- `/login` – Login page
- `/signup` – Registration page
- `/addcourse` – Admin add course page
- `/course/:id` – Course details page
- `/update/:id` – Admin update page

## Tech Stack

### Frontend
- React 19
- Vite
- React Router DOM
- Axios
- Tailwind CSS
- React Hot Toast
- UUID

### Backend / Mock API
- JSON Server
- `database.json` as data store

## Project Structure

```text
course-management-system/
├── backend/
│   └── database.json
├── course-management-frontend/
│   ├── public/
│   ├── src/
│   ├── package.json
│   ├── vite.config.js
│   ├── eslint.config.js
│   ├── index.html
│   └── README.md
├── group.html
└── README.md
```

## Database and API Design

The app uses a JSON file to simulate a database. The backend file is:

```text
backend/database.json
```

It contains two main collections:

### `users`
Example structure:

```json
{
  "username": "Admin",
  "password": "admin@123",
  "confirmPassword": "admin@123",
  "gender": "male",
  "email": "admin@gmail.com",
  "id": "101",
  "role": "admin"
}
```

### `courses`
Example structure:

```json
{
  "id": "3RX2vlxu894",
  "cName": "Springboot BootCamp Class",
  "cImg": "https://example.com/image.jpg",
  "cDuration": "1",
  "cPrice": "20000",
  "cTrainer": "Sai Charan Sir",
  "cDesc": "this is spring family course"
}
```

## Default Credentials

The sample data includes a default admin account:

- Email: `admin@gmail.com`
- Password: `admin@123`

Other user records are also available in the JSON file for testing.

## How the App Works

### User Flow
1. User opens the app.
2. If not logged in, they are redirected to the login page.
3. User can either sign up or log in.
4. On successful login, the user details are saved in `localStorage`.
5. Protected routes check if the user exists before allowing access.

### Admin Flow
1. Admin logs in with admin credentials.
2. Admin can add new courses using the form.
3. Admin can update an existing course.
4. Admin can delete a course directly from the course card.

### Course Flow
1. Courses are fetched from the backend using Axios.
2. The list is displayed as cards.
3. Clicking a course opens the full details page.
4. Data is managed through app context and React state.

## Frontend Architecture

The frontend uses React Context API for global state:

### `UserContext`
Stores login/logout functionality and current user state.

### `CourseContext`
Stores list of courses and methods to:
- fetch all courses
- add a course
- update a course
- delete a course
- find a course by ID

### Routing Components
- `App.jsx` sets up the application router.
- `ProtectedRoute.jsx` blocks guests from protected pages.
- `PrivateRoute.jsx` blocks non-admin users from admin-only pages.

## Key Pages

### Login Page
- Accepts email and password
- Validates against user records in the JSON server
- Stores user in local storage after successful login

### Signup Page
- Creates a new user
- Checks whether the email already exists
- Stores the user in the JSON database

### Course List Page
- Displays all courses in card layout
- Shows course name, image, trainer, duration, and price
- Admin sees update and delete actions
- Users see view details option

### Course Details Page
- Shows the full course description
- Displays trainer, duration, and price
- Offers an enrollment action button

### Add Course Page
- Accepts all required course information
- Sends a POST request to the JSON Server backend

### Update Course Page
- Fetches existing course data
- Allows editing fields
- Sends a PUT request to update the record

## API Calls Used

The frontend communicates with the mock backend through Axios requests like:

- `GET http://localhost:5000/users`
- `GET http://localhost:5000/courses`
- `POST http://localhost:5000/courses`
- `PUT http://localhost:5000/courses/:id`
- `DELETE http://localhost:5000/courses/:id`

## Setup Instructions

### 1. Install frontend dependencies

```bash
cd course-management-system/course-management-frontend
npm install
```

### 2. Start the backend

```bash
cd course-management-system/backend
npx json-server --watch database.json --port 5000
```

### 3. Start the frontend

Open a new terminal and run:

```bash
cd course-management-system/course-management-frontend
npm run dev
```

### 4. Open the app

After Vite starts, open the local URL shown in the terminal (typically `http://localhost:5173`).

## Important Notes

- This project uses a mock database instead of a real backend or database server.
- It is best suited for learning frontend and API integration concepts.
- Sensitive authentication logic is not production-grade.
- The app stores user session information in the browser, which is fine for demo purposes but not secure for real-world use.
- The Cart page is still a basic placeholder and not a fully implemented shopping cart.

## Learning Outcome

This project is valuable for practicing:

- React component design
- React Router navigation
- Context API state management
- Form handling and validation
- Axios API integration
- Conditional rendering and role based UI
- CRUD operations with JSON Server
- Tailwind CSS styling

## Potential Improvements

If the project were to be extended into a real application, the following improvements would be useful:

- Replace JSON Server with a real backend using Node.js + Express + MongoDB/PostgreSQL
- Add proper JWT authentication
- Add password hashing
- Add full cart and checkout flow
- Add course categories and filters
- Add admin dashboards and analytics
- Add tests for components and API calls
- Add loading and error states

## Summary

This project is a simple but complete learning-oriented course management application. It demonstrates how to build a full web app flow using React, routing, forms, context, and mock API services. It is especially useful for beginners learning full-stack-style frontend development using Vite and JSON Server.

The project is ideal for:
- learning React
- experimenting with protected routes
- exploring CRUD operations
- understanding role-based UI patterns
- building small educational platform apps

## License

This project is intended for educational and learning purposes.
