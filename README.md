# COMP 3810SEF / COMP S381F Group Project

## Project Information

**Project Name:** Cloud Computing Application with Authentication and CRUD Operations

**Group Information:**
- Group Number: Group15
- Members:
  - Chan Hon Fung - 14113306
  - Law Yiu To - 13899626
  - Wong Tsz Hang - 13896600
  - Kwok Yik Hong Henry - 13896568 
  - Li Ze Ming - 13896765

## Project File Introduction

### server.js
This is the main server file that provides the following functionalities:
- Express.js server setup 
- MongoDB connection using Mongoose
- Cookie-session function
- Login/Signup funtion
- Logout function
- Protected routes using authentication middleware
- Dashboard interactive
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
- **passpor-facebook**: (outh) can login through facebook

### views/ (folder)
Contains EJS template files:
- **login.ejs** : for loging the system through the mongoDB account and password
- **signup.ejs** : for sigin the account
- **dashboard.ejs** : the system main page
- **create.ejs** : for create the restaurant new menu
- **home.ejs** : the system first page
- **read.ejs** : for user load and read the system existing menu
- **update.ejs** : for user edit, update or delete the menu

### models/ (folder)
Contains Mongoose schema files:
- **User.js**: User model schema with:
  - username (unique, required)
  - password (hashed using bcrypt)
  - email (unique, required)
  - createdAt timestamp
  - Password comparison method for authentication

## Cloud-Based Server URL

**Testing URL:** https://cloud-demo-rudt.onrender.com/

*Note: Update this section with your actual deployed cloud URL before submission.*

## Operation Guides

### Use of Login/Logout Pages

#### Valid Login Information
After running the application, you can create a new account using the signup page. Alternatively, you can create a test user directly in MongoDB:

```javascript
Username: admin
Password: 000000
```

#### Sign-in Steps:
1. Navigate to the login page: `https://cloud-demo-rudt.onrender.com/login`
2. press staff login
3. Enter your username and password (admin / 000000)
4. Click "Sign In" button
5. Upon successful authentication, you will be redirected to the dashboard

#### Sign-up Steps:
1. Navigate to the signup page: `https://cloud-demo-rudt.onrender.com/signup`
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

### CRUD Web Pages
#### create menu page Steps:
  1. Navigate to the create page: `https://cloud-demo-rudt.onrender.com/create`
  2. fill in the form:
  - menu item Name 
  - choose category 
  - enter price
  - enter Description
  3. press the create item after you fill the form and it will success create the restaurant item.
- **Read**: Search interface with various query conditions
  1. Navigate to the create page: `https://cloud-demo-rudt.onrender.com/read`
  2. you can see all menu item in the results
  3. you can enter Name contains, Filter by category all information and press apply filters to search the specify item.
- **Update**: Edit form for modifying existing data
   1. Navigate to the create page: `https://cloud-demo-rudt.onrender.com/update`
   2. press the edit button / or delete button behide the item you want
   3. fill the update information and press save changes
   4. edit / delete successful.

### Use of RESTful CRUD Services

*Note: RESTful APIs will be implemented in the next phase. Below is the planned structure:*

**Planned RESTful APIs:**

1. **GET** `/api/menus` - Read/List all data objects
   - Query parameters: `menu`
   - Example: `https://cloud-demo-rudt.onrender.com/api/menus`

2. **GET** `/api/menu/id` - Read a specific data object by ID
   - Example: `curl "https://cloud-demo-rudt.onrender.com/api/menus/6920618dfc6605ff924cce30`

3. **POST** `/api/data` - Create a new data object
   - Request body: JSON object with data fields
   - Example: `POST /api/menus` with body `{
  "name": "Green Curry",
  "category": "Main Course",
  "price": 89,
  "description": "Spicy and creamy Thai curry"
}`

4. **PUT** `/api/menus/id` - Update an existing data object
   - Request body: JSON object with fields to update
   - Example: `PUT https://cloud-demo-rudt.onrender.com/api/menus/6920618dfc6605ff924cce30 \
-H "Content-Type: application/json" \
-d` with body `{
  "name": "Pad Thai",
  "category": "Main Course",
  "price": 75,
  "description": "Updated version of Pad Thai"
}`

5. **DELETE** `/api/menus/id` - Delete a data object
   - Example: `DELETE https://cloud-demo-rudt.onrender.com/api/menus/6920618dfc6605ff924cce30`

**CURL Testing Commands**

```bash
# GET - Read all menu item
curl "https://cloud-demo-rudt.onrender.com/api/menus

# GET - Read specific data
curl -X GET curl "https://cloud-demo-rudt.onrender.com/api/menus/6920618dfc6605ff924cce30"
the id must be change to the item id you're finding

# POST - Create data
curl -X POST https://cloud-demo-rudt.onrender.com/api/menus \
-H "Content-Type: application/json" \
-d '{
  "name": "Green Curry",
  "category": "Main Course",
  "price": 89,
  "description": "Spicy and creamy Thai curry"
}'


# PUT - Update data
curl -X PUT https://cloud-demo-rudt.onrender.com/api/menus/6920618dfc6605ff924cce30 \
-H "Content-Type: application/json" \
-d '{
  "name": "Pad Thai",
  "category": "Main Course",
  "price": 75,
  "description": "Updated version of Pad Thai"
}'

# DELETE - Delete data
curl -X DELETE https://cloud-demo-rudt.onrender.com/api/menus/6920618dfc6605ff924cce30
the id must be change to the item id you want to delete
```

*Note: Replace `http://localhost:3000` with your cloud URL when testing on deployed server.*

## Setup Instructions

1. **Install Dependencies:**
   ```bash
   npm install
   ```
2. **Run the Server:**
   ```bash
   npm start
   ```
3. **Access the Application:**
   Open your browser and navigate to `http://localhost:3000`






