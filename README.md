# **Ynov Quiz Auth**

A **React quiz application** using **Firebase Authentication** and **JWT-based API access**.

The application allows users to register, log in, receive a JWT token from an external backend API, access quiz questions, submit answers, and track their progress through the quiz.

---

# **Project Purpose**

The purpose of this project is to demonstrate how to combine **Firebase Authentication** with a custom **JWT-based backend API**.

The app uses Firebase to authenticate users with email and password, then communicates with an external quiz API to:

- **Register users**
- **Generate JWT tokens**
- **Fetch quiz questions**
- **Submit answers**
- **Track quiz progress**
- **Display success or error notifications**

This project can be used as a foundation for:

- **Quiz applications**
- **Authentication demos**
- **Firebase learning projects**
- **JWT authentication examples**
- **React frontend projects**
- **Educational platforms**
- **Student quiz portals**

---

# **Technologies Used**

## **Frontend**

- **React 18**
- **JavaScript**
- **React Scripts**
- **CSS**
- **Axios**

## **Authentication**

- **Firebase Authentication**
- **Email / Password Login**
- **Email / Password Registration**
- **JWT Token**
- **LocalStorage Token Management**

## **Testing**

- **React Testing Library**
- **Jest DOM**
- **User Event Testing Library**

---

# **Main Features**

## **User Authentication**

- **Register with email and password**
- **Login with email and password**
- **Logout**
- **Firebase authentication state tracking**
- **Display connected user email**
- **Show error notification when credentials are incorrect**

---

## **JWT Integration**

After Firebase authentication, the app calls an external backend API to generate a JWT token.

The token is stored in:

```text
localStorage
```

Then it is added to API requests using the `Authorization` header.

---

## **Quiz System**

The application allows authenticated users to:

- **Fetch quiz questions**
- **Answer the current question**
- **Submit answers**
- **Receive feedback**
- **Move to the next question when the answer is correct**
- **Display a completion message when the quiz is finished**

---

## **Notification System**

The app displays notifications for:

- **Wrong answer**
- **Incorrect email or password**
- **Authentication errors**
- **Quiz submission errors**

---

# **Project Structure**

```bash
firbase_auth_jwt/
├── public/
│   └── index.html
│
├── src/
│   ├── App.js
│   ├── App.css
│   ├── Navbar.js
│   ├── index.js
│   └── ...
│
├── package.json
└── README.md
```

---

# **Application Flow**

## **1. Register**

The user enters an email and password.

The app creates the user with Firebase:

```js
firebase.auth().createUserWithEmailAndPassword(email, password)
```

Then it calls the backend API:

```http
POST /register
```

The backend returns a JWT token, which is stored in `localStorage`.

---

## **2. Login**

The user logs in using Firebase:

```js
firebase.auth().signInWithEmailAndPassword(email, password)
```

After authentication, the app calls:

```http
POST /login
```

The backend returns a JWT token.

---

## **3. Store Token**

The JWT token is stored locally:

```js
localStorage.setItem("token", token)
```

---

## **4. Fetch Questions**

The app sends the token in the request headers:

```http
Authorization: <token>
```

Then it fetches the quiz questions from the backend.

---

## **5. Submit Answer**

The user submits an answer to the current question.

If the answer is correct:

- The user progresses to the next question
- The next question is displayed

If the answer is wrong:

- A notification is displayed

---

## **6. Logout**

The user logs out from Firebase and the JWT token is removed from `localStorage`.

---

# **API Endpoints Used**

The frontend communicates with an external backend API.

| Method | Endpoint | Description |
|---|---|---|
| **POST** | `/register` | Register user in backend and generate JWT |
| **POST** | `/login` | Login user and generate JWT |
| **GET** | `/questions` | Fetch quiz questions |
| **POST** | `/submit-answer` | Submit answer for the current question |

---

# **Installation**

## **1. Clone the Repository**

```bash
git clone https://github.com/Noris69/firbase_auth_jwt.git
cd firbase_auth_jwt
```

---

## **2. Install Dependencies**

```bash
npm install
```

---

## **3. Configure Firebase**

Create a `.env` file in the root directory:

```env
REACT_APP_FIREBASE_API_KEY=your_firebase_api_key
REACT_APP_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
REACT_APP_FIREBASE_PROJECT_ID=your_project_id
REACT_APP_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
REACT_APP_FIREBASE_APP_ID=your_app_id

REACT_APP_API_BASE_URL=https://your-backend-api-url.com
```

---

## **4. Recommended Firebase Config**

Instead of hardcoding Firebase credentials in `App.js`, use environment variables:

```js
const firebaseConfig = {
  apiKey: process.env.REACT_APP_FIREBASE_API_KEY,
  authDomain: process.env.REACT_APP_FIREBASE_AUTH_DOMAIN,
  projectId: process.env.REACT_APP_FIREBASE_PROJECT_ID,
  storageBucket: process.env.REACT_APP_FIREBASE_STORAGE_BUCKET,
  messagingSenderId: process.env.REACT_APP_FIREBASE_MESSAGING_SENDER_ID,
  appId: process.env.REACT_APP_FIREBASE_APP_ID,
};
```

---

## **5. Run the Application**

```bash
npm start
```

The application will run on:

```bash
http://localhost:3000
```

---

# **Useful Commands**

## **Start Development Server**

```bash
npm start
```

## **Build for Production**

```bash
npm run build
```

## **Run Tests**

```bash
npm test
```

---

# **Security Recommendations**

- **Do not hardcode Firebase configuration directly in source files**
- **Use environment variables**
- **Do not expose backend secrets**
- **Do not store sensitive data in localStorage**
- **Use HTTPS in production**
- **Validate JWT tokens on the backend**
- **Protect quiz endpoints**
- **Handle token expiration**
- **Add refresh token logic if needed**

---

# **Git Ignore Recommendations**

```gitignore
node_modules/
build/
dist/
.env
.env.local
*.log
.DS_Store
.vscode/
.idea/
```

---


# **Author**

Developed by **Noris69**.
