A robust RESTful API built to handle user authentication, posts, comments, and notifications for a social networking platform.
Node.js, Express, MongoDB, Mongoose, @clerk/express, @arcjet/node, @arcjet/inspect, cloudinary, multer, cors, dotenv, express-async-handler, nodemon

* 📁 **Project structure / folder overview**
  * `src/config/`: Configuration files for database, environment variables, Arcjet, and Cloudinary.
  * `src/controllers/`: Business logic for API endpoints (users, posts, comments, notifications).
  * `src/middleware/`: Express middleware for auth, uploads, Arcjet, and database connectivity.
  * `src/models/`: Mongoose schemas (User, Post, Comment, Notification).
  * `src/routes/`: Express route definitions.
  * `src/server.js`: Application entry point.
* ⚙️ **Setup & installation instructions**
  * **Prerequisites**: Node.js, MongoDB URI, Clerk API keys, Cloudinary credentials, Arcjet keys.
  * **Dependencies include**: Express 5.2.1, Mongoose 9.9.2, @clerk/express 2.1.55, Cloudinary 2.10.0, multer 2.2.0, cors 2.8.6, dotenv 17.4.2, @arcjet/node 1.10.0.
  * **Install commands**: 
    ```bash
    npm install
    ```
* ▶️ **Running the project**
  * **Development** (using nodemon 3.1.14): 
    ```bash
    npm run dev
    ```
  * **Production**: 
    ```bash
    npm start
    ```
* 🌐 **API endpoints**
  * **Users**
    * `GET /api/users/profile/:username` - Get user profile
    * `POST /api/users/sync` - Sync user from Clerk (protected)
    * `GET /api/users/me` - Get current user (protected)
    * `PUT /api/users/profile` - Update user profile (protected)
    * `POST /api/users/follow/:targetUserId` - Follow/unfollow user (protected)
  * **Posts**
    * `GET /api/posts` - Get all posts
    * `GET /api/posts/:postId` - Get specific post
    * `GET /api/posts/user/:username` - Get posts by user
    * `POST /api/posts` - Create post (protected, supports image upload)
    * `POST /api/posts/:postId/like` - Like/unlike post (protected)
    * `DELETE /api/posts/:postId` - Delete post (protected)
  * **Comments**
    * `GET /api/comments/post/:postId` - Get comments for a post
    * `POST /api/comments/post/:postId` - Create comment (protected)
    * `DELETE /api/comments/:commentId` - Delete comment (protected)
  * **Notifications**
    * `GET /api/notifications` - Get notifications (protected)
    * `DELETE /api/notifications/:notificationId` - Delete notification (protected)
* 🗄️ **Database schema / models overview**
  * **User**: `clerkId`, `email`, `firstName`, `lastName`, `username`, profiles (bio, location, pictures), `followers`, `following`.
  * **Post**: `user` (ref User), `content`, `image`, `likes` (ref User), `comments` (ref Comment).
  * **Comment**: `user` (ref User), `post` (ref Post), `content`, `likes` (ref User).
  * **Notification**: `from` (ref User), `to` (ref User), `type` (enum), `post` (ref Post), `comment` (ref Comment).
* 🚀 **Deployment notes**
  * Configured for serverless deployment with a `vercel.json` file. Ensure environment variables are set in your Vercel project settings.
