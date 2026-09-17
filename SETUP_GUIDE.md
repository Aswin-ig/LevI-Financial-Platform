# LevI Financial Platform Setup Guide

## 1. Prerequisites

Install the following:

- Node.js 18+
- npm
- Expo CLI (for frontend)
- A MongoDB database (local or Atlas)

## 2. Clone / Download

```bash
git clone https://github.com/Aswin-ig/LevI-Financial-Platform.git
cd LevI-Financial-Platform
```

## 3. Backend setup

```bash
cd backend
npm install
cp .env.example .env
```

Update `.env` with your MongoDB connection string:

```env
PORT=5000
MONGODB_URI=mongodb+srv://your-user:your-password@cluster.mongodb.net/levi_db
JWT_SECRET=your_super_secret_key
JWT_EXPIRE=30d
NODE_ENV=development
```

Then start the backend:

```bash
npm start
```

Expected output:

```bash
MongoDB connected
Server running on http://localhost:5000
```

## 4. Frontend setup

Open a new terminal and run:

```bash
cd frontend
npm install
```

Update API URLs in the mobile screens before running the app. Replace this value:

```javascript
const API_URL = 'http://192.168.1.100:5000/api';
```

with your actual machine IP, for example:

```javascript
const API_URL = 'http://192.168.0.12:5000/api';
```

Then start the app:

```bash
npm start
```

You can run it on a real device using Expo Go or in a simulator.

## 5. Login flow

Use this test login flow:

- First name: `John`
- Phone: `9876543210`
- OTP: check the backend console output

Example console output:

```bash
OTP for +919876543210: 123456
```

Enter `123456` in the app.

## 6. Optional profile setup

After login, the app asks for profile details. You can fill them or skip.

## 7. Recommender & calculator

The app includes:

- government scheme recommendation
- EMI calculation
- nearest partner listing
- profile management

## 8. Build APK (optional)

To build an Android APK:

```bash
cd frontend
npx expo export --platform android
```

Or use EAS build if configured:

```bash
eas build --platform android
```

## 9. Troubleshooting

### MongoDB not connecting
- verify your MONGODB_URI value
- ensure your IP is whitelisted in MongoDB Atlas

### Frontend cannot connect to backend
- make sure the backend is running
- use the correct local IP in `API_URL`
- do not use `localhost` when testing on a phone

### OTP not working
- check the backend console for OTP output
- this app is in development mode and prints OTPs to the console

## 10. Project structure

```bash
LevI-Financial-Platform/
├── backend/
│   ├── .env.example
│   ├── package.json
│   ├── server.js
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   └── routes/
├── frontend/
│   ├── App.js
│   ├── app.json
│   ├── package.json
│   ├── index.js
│   └── screens/
├── .gitignore
├── README.md
└── SETUP_GUIDE.md
```

## 11. Notes

This is a starter implementation for the LevI application and is intended to be used as a functional project scaffold with OTP login and financial features.
