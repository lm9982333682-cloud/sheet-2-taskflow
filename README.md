# TaskFlow – Full Stack Task Management Application

## 1. Project Overview

TaskFlow is a full-stack task management web application developed using React, Node.js, Express.js, and MongoDB.

The main purpose of this project is to help users organize their daily work, manage tasks, set priorities, track progress, and manage deadlines from a single dashboard.

TaskFlow provides a modern dashboard with two main task management views:

- **Kanban Board:** Manage tasks according to their current status.
- **All Tasks:** View, search, filter, select, export, and manage tasks in a table format.

The application uses REST APIs to connect the frontend with the backend and MongoDB database.

## 2. Project Structure

```text
project/
│
├── server/
│   ├── src/
│   │   ├── app/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routers/
│   │   ├── utils/
│   │   └── validator/
│   │
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── taskflow/
│   ├── public/
│   ├── src/
│   │   ├── api/
│   │   ├── components/
│   │   ├── data/
│   │   ├── hooks/
│   │   ├── layout/
│   │   ├── pages/
│   │   ├── routes/
│   │   ├── service/
│   │   └── store/
│   │
│   ├── package.json
│   ├── index.html
│   └── vite.config.js
│
└── README.md
```

## 3. Technologies Used

### Frontend

- React
- Vite
- Tailwind CSS
- React Router DOM
- Redux Toolkit
- React Redux
- Axios
- React Hook Form
- React Toastify
- Lucide React

### Backend

- Node.js
- Express.js
- MongoDB
- Mongoose
- JSON Web Token (JWT)
- bcrypt
- express-validator
- cookie-parser
- CORS
- Google Auth Library

## 4. Main Features

### 4.1 User Authentication

- User registration.
- User login.
- Email and password authentication.
- Google authentication endpoint.
- JWT-based authentication.
- Access token and refresh token handling.
- Secure HTTP-only refresh-token cookie.
- Logout functionality.
- Protected API routes.

### 4.2 Dashboard

- Modern dark dashboard interface.
- Task overview.
- Total task count.
- Pending task count.
- In Progress task count.
- Completed task count.
- Task progress overview.

### 4.3 Kanban Board

The Kanban Board organizes tasks into three status columns:

- Todo (stored as Pending in backend).
- In Progress.
- Completed.

Users can view, create, edit, and delete tasks through the board.

### 4.4 All Tasks

The All Tasks page provides:

- Task directory.
- Search functionality.
- Status filters.
- Priority filters.
- Individual task selection.
- Multiple task selection.
- Batch delete.
- CSV export.
- Create task.
- Edit task.
- Delete task with confirmation modal.

### 4.5 Task Management

Users can manage:

- Task title.
- Task description.
- Due date.
- Task priority.
- Task status.

### 4.6 Responsive UI

- Dark navy dashboard design.
- Indigo primary action buttons.
- Responsive layout.
- Sidebar navigation.
- Navbar with search and filters.
- Task cards and tables.
- Confirmation modals.

## 5. Backend API Documentation

Backend base URL:

```text
http://localhost:4545/api
```

### Authentication APIs

| Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/register` | Register a new user |
| POST | `/auth/login` | Login user |
| POST | `/auth/refresh` | Refresh access token |
| POST | `/auth/logout` | Logout user |
| GET | `/auth/me` | Get logged-in user |
| POST | `/auth/google` | Google authentication |

### Task APIs

| Method | Endpoint | Description |
|---|---|---|
| POST | `/tasks` | Create a task |
| GET | `/tasks` | Get all user tasks |
| GET | `/tasks/:id` | Get a single task |
| PUT | `/tasks/:id` | Update a task |
| DELETE | `/tasks/:id` | Delete a task |

Task APIs require authentication through the access token.

## 6. Database Models

TaskFlow uses MongoDB with Mongoose.

### User Model

The User model manages user account and authentication information, including:

- Name.
- Email.
- Password.
- Authentication-related token information.
- Account information.

### Task Model

The Task model stores:

| Field | Description |
|---|---|
| title | Task title |
| description | Task details |
| dueDate | Task deadline |
| priority | Low, Medium, High |
| status | Pending, In Progress, Completed |
| user | Task owner reference |
| createdAt | Task creation date |
| updatedAt | Last update date |

Each task belongs to a specific user.

## 7. Installation and Setup

You need Node.js and MongoDB to run this project.

### Step 1: Clone the Repository

```bash
git clone YOUR_REPOSITORY_URL
```

### Step 2: Open the Project

```bash
cd project
```

### Step 3: Setup Backend

```bash
cd server
npm install
```

Create a `.env` file inside the server folder:

```env
PORT=4545
DBURL=your_mongodb_connection_string

ACCESS_TOKEN_SECRET=your_access_token_secret
REFRESH_TOKEN_SECRET=your_refresh_token_secret

NODE_ENV=development

GOOGLE_CLIENT_ID=your_google_client_id
```

Start the backend:

```bash
npm run dev
```

Backend URL:

```text
http://localhost:4545
```

API URL:

```text
http://localhost:4545/api
```

### Step 4: Setup Frontend

Open another terminal:

```bash
cd taskflow
npm install
```

Start the frontend:

```bash
npm run dev
```

Frontend URL:

```text
http://localhost:5173
```

### Step 5: Production Build

To create the frontend production build:

```bash
npm run build
```

The production files will be generated inside the `dist` folder.

## 8. Frontend and Backend Communication

The frontend communicates with the backend using Axios.

The API configuration is located at:

```text
taskflow/src/api/axiosInstance.js
```

The task API service is located at:

```text
taskflow/src/service/taskService.js
```

The general application workflow:

1. User opens the TaskFlow frontend.
2. User registers or logs in.
3. Frontend sends authentication requests to the backend.
4. Backend validates the user and generates authentication tokens.
5. Authenticated requests use the access token.
6. User creates, updates, or deletes tasks.
7. Backend validates and processes the requests.
8. MongoDB stores the task information.
9. Frontend displays the updated task data.

## 9. Task Management Workflow

### Create Task

User opens the Add Task form, enters task information, and submits it. The frontend sends a POST request to the backend. The backend saves the task in MongoDB.

### Update Task

User selects a task to edit. The frontend fetches its details and submits the updated information through a PUT request.

### Delete Task

User clicks the delete button. A confirmation modal appears. After confirmation, the frontend sends a DELETE request to the backend.

### Search and Filter

Users can search tasks and filter them by status and priority from the task management interface.

## 10. Task Status and Priority

### Task Status

| Backend Value | Frontend Display |
|---|---|
| Pending | Todo |
| In Progress | In Progress |
| Completed | Completed |

### Task Priority

- Low
- Medium
- High

## 11. Project Purpose – Why TaskFlow?

TaskFlow is designed to make task management simple, organized, and efficient.

It helps users:

- Organize daily activities.
- Manage personal and professional tasks.
- Set task deadlines.
- Prioritize important work.
- Track task progress.
- View tasks in a Kanban Board.
- Search and filter tasks.
- Export task records as CSV.
- Manage tasks from one dashboard.

## 12. Future Improvements

Possible future improvements include:

- Task reminders and notifications.
- Team collaboration.
- Task assignment.
- Comments and activity history.
- Advanced analytics.
- Calendar integration.
- File attachments.
- Improved user profile settings.

These are potential future enhancements, not claims about currently implemented features.

## 13. Deployment

### Frontend Deployment

The React + Vite frontend can be deployed on Vercel.

Recommended settings:

| Setting | Value |
|---|---|
| Framework | Vite |
| Root Directory | `taskflow` |
| Build Command | `npm run build` |
| Output Directory | `dist` |

The frontend also uses a `vercel.json` rewrite configuration to support React Router routes.

### Backend Deployment

The Node.js + Express backend can be deployed on a Node.js-compatible hosting platform.

Production environment variables must be configured on the hosting platform.

Update the frontend API base URL to the deployed backend URL before production deployment.

## 14. Security Notes

- Never commit `.env` files.
- Keep JWT secrets private.
- Never expose database credentials.
- Use HTTPS in production.
- Configure CORS for the deployed frontend domain.
- Use secure cookie settings in production.

## 15. Conclusion

TaskFlow is a full-stack task management application that combines a React-based dashboard with a Node.js and Express backend.

It provides authentication, task management, Kanban organization, search, filtering, and CSV export.

The project demonstrates frontend development, backend API development, database integration, authentication, and full-stack application architecture.