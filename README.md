Project Overview
This Node.js API project is designed to provide user authentication (signup and login) and user profile management functionalities using Express.js and MongoDB. Additionally, it includes a feature to send a confirmation email to users upon successful registration.

Installation and Setup
Install Dependencies:

Ensure Node.js and npm are installed on your machine.
Initialize your project and install required packages:
npm init -y
npm install express mongoose bcryptjs jsonwebtoken nodemailer
run the api node index.js 
project strucher
/app
├── index.js
├── /controllers
│   ├── authController.js
│   └── profileController.js
├── /models
│   └── userModel.js
├── /routes
│   ├── authRoutes.js
│   └── profileRoutes.js
├── /services
│   └── emailService.js
├── /config
│   └── config.js
├── /utils
│   ├── authMiddleware.js
│   ├── passwordUtils.js
│   └── jwtUtils.js
└──
index.js: Entry point that initializes the Express server and connects to MongoDB.
/controllers: Contains logic for handling HTTP requests.
/models: Defines MongoDB schemas using Mongoose.
/routes: Defines API endpoints using Express Router.
/services: Integrates with external services (e.g., Node Mailer for sending emails).
/config: Configuration files (e.g., database configuration).
/utils: Utility functions (e.g., password hashing, JWT handling).
/tests: Optional folder for unit and integration tests.
API Endpoints
User Signup

Endpoint: POST /api/signup
Description: Allows users to register with username, email, and password. Hashes the password before storing it in MongoDB.
Request Body: { "username": "example", "email": "user@example.com", "password": "password123" }
Response: Returns user data with a JWT for authentication.
User Login

Endpoint: POST /api/login
Description: Allows registered users to log in using their email and password. Generates a JWT upon successful login.
Request Body: { "email": "user@example.com", "password": "password123" }
Response: Returns a JWT.
User Profile

Endpoint: GET /api/profile
Description: Retrieves and displays the user's profile information based on the provided JWT.
Authorization: JWT token should be included in the Authorization header as Bearer <token>.
Response: Returns user profile data.
Email Confirmation
Functionality: Upon successful user registration (POST /api/signup), a confirmation email is sent to the user's provided email address.
Email Content: Includes a confirmation link or code to verify the email address.
Integration: Handled by emailService.js using Node Mailer to send emails.
Code Documentation
Inline Comments: Ensure all complex logic and important functions are well-documented with inline comments explaining the purpose and usage.

Descriptive Naming: Use descriptive variable and function names to enhance code readability.

Error Handling: Implemented centralized error handling in index.js  through custom middleware (errorMiddleware.js) for consistent error responses.
