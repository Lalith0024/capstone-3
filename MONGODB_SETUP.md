# MongoDB Setup Guide

## The Problem
Your MongoDB server is **NOT running**. You have MongoDB Compass (GUI) installed, but the actual MongoDB server process is not running.

## Solution Options

### Option 1: Use MongoDB Atlas (Cloud) - RECOMMENDED ✅
This is the easiest option - no installation needed!

1. Go to https://www.mongodb.com/cloud/atlas
2. Sign up for free account
3. Create a free cluster
4. Get your connection string
5. Update your `.env` file:

```env
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/capstone3?retryWrites=true&w=majority
```

Replace `username`, `password`, and `cluster` with your actual values.

### Option 2: Install MongoDB Locally

#### On macOS (using Homebrew):
```bash
# Install MongoDB
brew tap mongodb/brew
brew install mongodb-community

# Start MongoDB
brew services start mongodb-community

# Verify it's running
brew services list | grep mongodb
```

#### On macOS (Manual Installation):
1. Download from: https://www.mongodb.com/try/download/community
2. Install the .pkg file
3. Start MongoDB:
```bash
mongod --config /usr/local/etc/mongod.conf
```

### Option 3: Use Docker
```bash
docker run -d -p 27017:27017 --name mongodb mongo:latest
```

## Verify MongoDB is Running

After starting MongoDB, check if it's running:
```bash
# Check if MongoDB is running
ps aux | grep mongod | grep -v grep

# Or test connection
mongosh
# Should connect successfully
```

## Update Your .env File

Make sure your `.env` file in the `backend` directory has the correct `MONGODB_URI`:

**For Local MongoDB:**
```env
MONGODB_URI=mongodb://localhost:27017/capstone3
```

**For MongoDB Atlas:**
```env
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/capstone3?retryWrites=true&w=majority
```

## Restart Your Server

After starting MongoDB, restart your backend server:
```bash
cd backend
npm start
```

You should see:
```
✓ Connected to MongoDB successfully
  Database: capstone3
```

## Quick Test

Test if MongoDB is working:
```bash
cd backend
node -e "require('dotenv').config(); const mongoose = require('mongoose'); mongoose.connect(process.env.MONGODB_URI).then(() => { console.log('✓ MongoDB connected!'); process.exit(0); }).catch(err => { console.error('✗ Error:', err.message); process.exit(1); });"
```

