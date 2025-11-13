# COMP 3810SEF / COMP S381F Group Project

## Project Information

**Project Name:** Cloud Computing Application with Authentication and CRUD Operations

**Group Information:**
- Group Number: [Your Group Number]
- Members:
  - [Student Name 1] - [SID]
  - [Student Name 2] - [SID]
  - [Student Name 3] - [SID]
  - [Student Name 4] - [SID] (if applicable)
  - [Student Name 5] - [SID] (if applicable)

## Project File Introduction

### server.js
This is the main server file that provides the following functionalities:
- Express.js server setup and configuration
- MongoDB connection using Mongoose
- Cookie-session middleware for authentication
- Login/Signup routes with password hashing (bcryptjs)
- Logout functionality
- Protected routes using authentication middleware
- Dashboard route (protected, requires login)
- EJS view engine configuration
- Static file serving

### package.json
Lists all project dependencies:
- **express**: Web framework for Node.js
- **mongoose**: MongoDB object modeling tool
- **ejs**: Embedded JavaScript templating engine
- **cookie-session**: Session management using cookies
- **bcryptjs**: Password hashing library
- **body-parser**: Middleware for parsing request bodies
- **nodemon**: Development tool for auto-restarting server (dev dependency)

### public/ (folder)
This folder is optional and can contain static files such as:
- CSS files
- JavaScript files
- Images
- Other static resources

Currently, this folder is empty but can be used for additional static assets.

### views/ (folder)
Contains EJS template files:
- **login.ejs**: Login page template with username and password fields
- **signup.ejs**: User registration page template with username, email, and password fields
- **dashboard.ejs**: Protected dashboard page that displays after successful login, includes logout button

### models/ (folder)
Contains Mongoose schema files:
- **User.js**: User model schema with:
  - username (unique, required)
  - password (hashed using bcrypt)
  - email (unique, required)
  - createdAt timestamp
  - Password comparison method for authentication

## Cloud-Based Server URL

**Testing URL:** [Your Cloud URL - e.g., https://comp3810sef-group1.render.com/]

*Note: Update this section with your actual deployed cloud URL before submission.*

## Operation Guides

### Use of Login/Logout Pages

#### Valid Login Information
After running the application, you can create a new account using the signup page. Alternatively, you can create a test user directly in MongoDB:

```javascript
// Example test user (password will be hashed automatically)
Username: testuser
Email: test@example.com
Password: test123
```

#### Sign-in Steps:
1. Navigate to the login page: `http://localhost:3000/login` (or your cloud URL)
2. Enter your username and password
3. Click "Sign In" button
4. Upon successful authentication, you will be redirected to the dashboard

#### Sign-up Steps:
1. Navigate to the signup page: `http://localhost:3000/signup`
2. Fill in the form:
   - Username (minimum 3 characters)
   - Email (valid email format)
   - Password (minimum 6 characters)
3. Click "Sign Up" button
4. You will be automatically logged in and redirected to the dashboard

#### Logout Steps:
1. From the dashboard page, click the "Logout" button in the top-right corner
2. You will be logged out and redirected to the login page
3. Alternatively, you can access `/logout` directly via GET or POST request

### Use of CRUD Web Pages

*Note: CRUD web pages will be implemented in the next phase. The current implementation includes:*
- ✅ Login/Logout functionality
- ✅ Protected routes (authentication middleware)
- ✅ Dashboard page with logout button

**Future CRUD Implementation:**
- **Create**: Button/UI to add new data objects
- **Read**: Search interface with various query conditions
- **Update**: Edit form for modifying existing data
- **Delete**: Delete button with confirmation

### Use of RESTful CRUD Services

*Note: RESTful APIs will be implemented in the next phase. Below is the planned structure:*

**Planned RESTful APIs:**

1. **GET** `/api/data` - Read/List all data objects
   - Query parameters: `?field=value&sort=field&limit=10`
   - Example: `GET /api/data?status=active&limit=5`

2. **GET** `/api/data/:id` - Read a specific data object by ID
   - Example: `GET /api/data/507f1f77bcf86cd799439011`

3. **POST** `/api/data` - Create a new data object
   - Request body: JSON object with data fields
   - Example: `POST /api/data` with body `{"name": "Item", "status": "active"}`

4. **PUT** `/api/data/:id` - Update an existing data object
   - Request body: JSON object with fields to update
   - Example: `PUT /api/data/507f1f77bcf86cd799439011` with body `{"status": "inactive"}`

5. **DELETE** `/api/data/:id` - Delete a data object
   - Example: `DELETE /api/data/507f1f77bcf86cd799439011`

**CURL Testing Commands (to be used after implementation):**

```bash
# GET - Read all data
curl -X GET http://localhost:3000/api/data

# GET - Read specific data
curl -X GET http://localhost:3000/api/data/507f1f77bcf86cd799439011

# POST - Create data
curl -X POST http://localhost:3000/api/data \
  -H "Content-Type: application/json" \
  -d '{"name":"Test Item","status":"active"}'

# PUT - Update data
curl -X PUT http://localhost:3000/api/data/507f1f77bcf86cd799439011 \
  -H "Content-Type: application/json" \
  -d '{"status":"inactive"}'

# DELETE - Delete data
curl -X DELETE http://localhost:3000/api/data/507f1f77bcf86cd799439011
```

*Note: Replace `http://localhost:3000` with your cloud URL when testing on deployed server.*

## Setup Instructions

1. **Install Dependencies:**
   ```bash
   npm install
   ```

2. **Set Environment Variables (optional):**
   Create a `.env` file or set environment variables:
   - `MONGODB_URI`: MongoDB connection string (default: `mongodb://localhost:27017/comp3810sef_db`)
   - `PORT`: Server port (default: 3000)
   - `SESSION_SECRET`: Secret key for sessions (default: 'your-secret-key-change-in-production')

3. **Start MongoDB:**
   Ensure MongoDB is running on your system or use MongoDB Atlas (cloud).

4. **Run the Server:**
   ```bash
   npm start
   ```
   Or for development with auto-reload:
   ```bash
   npm run dev
   ```

5. **Access the Application:**
   Open your browser and navigate to `http://localhost:3000`

## Notes

- The application uses cookie-session for authentication
- Passwords are hashed using bcryptjs before storing in the database
- All protected routes require authentication (session must be active)
- The logout functionality clears the session and redirects to login page
- Make sure to update the cloud URL and group information before submission


