# Vercel Deployment Guide for Quick-Chat

## Prerequisites Setup

Before deploying, you need to obtain the following credentials:

### 1. MongoDB Atlas (Database)
- Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- Create a free account
- Create a new cluster
- In "Database Access", add a new user with a password
- In "Network Access", add your IP (or 0.0.0.0/0 for all)
- Click "Connect" and copy the connection string
- Replace `<username>`, `<password>`, and `<dbname>` with your values
- Example: `mongodb+srv://user:pass@cluster.mongodb.net/chat-app`

### 2. JWT Secret
- Generate a random secret (minimum 32 characters)
- You can use: `openssl rand -base64 32` or any random string
- Example: `your_super_secret_jwt_key_here_minimum_32_characters_long`

### 3. Cloudinary (Image Upload)
- Go to [Cloudinary](https://cloudinary.com)
- Create a free account
- Go to Dashboard
- Copy these values:
  - `Cloud Name`
  - `API Key`
  - `API Secret`

## Deployment Steps

### Step 1: Push to GitHub
```bash
git add .
git commit -m "Setup for Vercel deployment"
git push origin main
```

### Step 2: Create Vercel Account
- Go to [Vercel.com](https://vercel.com)
- Sign up with your GitHub account
- Authorize Vercel to access your repositories

### Step 3: Import Project
- Click "Add New..." → "Project"
- Select your `Quick-chat` repository
- Click "Import"

### Step 4: Set Environment Variables
In the Vercel dashboard, go to **Settings** → **Environment Variables** and add:

```
MONGODB_URI = mongodb+srv://your_username:your_password@cluster.mongodb.net/chat-app
JWT_SECRET = your_random_jwt_secret_here
CLOUDINARY_CLOUD_NAME = your_cloudinary_name
CLOUDINARY_API_KEY = your_cloudinary_api_key
CLOUDINARY_API_SECRET = your_cloudinary_api_secret
NODE_ENV = production
```

### Step 5: Deploy
- Click "Deploy"
- Wait for the build to complete
- Your app will be available at `https://your-app-name.vercel.app`

## Getting the Required Credentials

### MongoDB Atlas
1. Create account at https://www.mongodb.com/cloud/atlas
2. Create Free cluster
3. Create Database User (remember username and password)
4. Add IP to Network Access (0.0.0.0/0 for development)
5. Click Connect → Connect your application
6. Copy connection string and replace credentials

### JWT Secret
Generate using any of these:
- `node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"`
- `openssl rand -base64 32`
- Or any random 32+ character string

### Cloudinary
1. Create free account at https://cloudinary.com
2. Go to Dashboard
3. Copy Cloud Name, API Key, API Secret

## Important Notes

⚠️ **Never commit `.env` files to GitHub** - Only use Vercel's dashboard for secrets

✅ Use the production MongoDB URI (not localhost)

✅ Make sure Socket.io CORS is configured correctly for your domain

## Verify Deployment

After deployment:
1. Visit your Vercel URL
2. Try to register a new account
3. Test real-time messaging
4. Check browser console for any errors
5. Check Vercel logs if something breaks

## Troubleshooting

**App shows 404?**
- Check that vercel.json is in the root directory
- Ensure both client and server builds are working

**MongoDB connection error?**
- Verify connection string in environment variables
- Check IP whitelist in MongoDB Atlas
- Ensure username and password are correct

**Cloudinary upload failing?**
- Check API credentials in Vercel environment variables
- Verify Cloudinary account has upload enabled

**Socket.io not connecting?**
- Update Socket.io client configuration with your Vercel domain
- Check CORS settings in server.js

Need help? Check the logs in Vercel dashboard!
