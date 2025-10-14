# Quick Chat - Full Stack Chat Application

A real-time chat application built with React, Node.js, Express, Socket.io, and MongoDB.

## Features

- 🔐 User authentication and registration
- 💬 Real-time messaging with Socket.io
- 👥 User profiles and avatars
- 📱 Responsive design with Tailwind CSS
- 🚀 Fast development with Vite

## Tech Stack

### Frontend
- React 19
- Vite
- Tailwind CSS
- Socket.io Client
- React Router DOM

### Backend
- Node.js
- Express.js
- Socket.io
- MongoDB with Mongoose
- JWT Authentication
- Cloudinary for image uploads

## Local Development

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or MongoDB Atlas)

### Installation

1. Clone the repository
```bash
git clone https://github.com/pathaksatyam0103-art/Quick-chat.git
cd Quick-chat
```

2. Install dependencies
```bash
# Install server dependencies
cd server
npm install

# Install client dependencies
cd ../client
npm install
```

3. Set up environment variables
Create a `.env` file in the server directory:
```env
MONGODB_URI=mongodb://localhost:27017/chat-app
PORT=5000
JWT_SECRET=your_jwt_secret_here
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_key
CLOUDINARY_API_SECRET=your_cloudinary_secret
```

4. Start the development servers
```bash
# Start the server (from server directory)
npm run server

# Start the client (from client directory)
npm run dev
```

The application will be available at:
- Frontend: http://localhost:5173
- Backend API: http://localhost:5000

## Deployment on Vercel

### Prerequisites
- Vercel account
- MongoDB Atlas account (for cloud database)

### Steps

1. **Set up MongoDB Atlas**
   - Create a free MongoDB Atlas account
   - Create a new cluster
   - Get your connection string

2. **Deploy to Vercel**
   - Connect your GitHub repository to Vercel
   - Add environment variables in Vercel dashboard:
     - `MONGODB_URI`: Your MongoDB Atlas connection string
     - `JWT_SECRET`: A random secret string
     - `CLOUDINARY_CLOUD_NAME`: Your Cloudinary cloud name
     - `CLOUDINARY_API_KEY`: Your Cloudinary API key
     - `CLOUDINARY_API_SECRET`: Your Cloudinary API secret

3. **Deploy**
   - Vercel will automatically build and deploy your application
   - Your app will be available at `https://your-app-name.vercel.app`

## Project Structure

```
Quick-chat/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # React components
│   │   ├── pages/         # Page components
│   │   ├── context/       # React context providers
│   │   └── assets/        # Static assets
│   └── package.json
├── server/                # Node.js backend
│   ├── controllers/       # Route controllers
│   ├── models/           # MongoDB models
│   ├── routes/           # API routes
│   ├── middleware/       # Custom middleware
│   └── lib/              # Utility functions
└── vercel.json           # Vercel configuration
```

## API Endpoints

- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/messages/:chatId` - Get messages for a chat
- `POST /api/messages` - Send a new message

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).
