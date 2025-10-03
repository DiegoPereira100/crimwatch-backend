# CrimWatch - Backend

[![Node.js](https://img.shields.io/badge/Node.js-20.x-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-4.x-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-4.x-47A248?logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![JWT](https://img.shields.io/badge/JWT-Authentication-black?logo=jsonwebtokens&logoColor=white)](https://jwt.io/)
[![Status](https://img.shields.io/badge/Status-Complete-green)](https://github.com/DiegoPereira100/crimwatch)
[![License](https://img.shields.io/badge/License-MIT-green)](./LICENSE)

> A robust RESTful API for the CrimWatch system, designed to securely and efficiently manage and serve data on criminal occurrences.

## 📖 Overview

The **CrimWatch Backend** is the server for the CrimWatch platform, built with Node.js, Express, and MongoDB. It is responsible for all business logic, including user authentication, occurrence management (create, read, update, delete), and the secure storage of data.

This API serves as the backbone for the [CrimWatch Frontend](https://github.com/DiegoPereira100/crimwatch), providing the necessary endpoints for the client application to interact with the database.

## Problem Statement

The lack of access to centralized and easily visualizable public safety data makes decision-making difficult for both citizens and authorities. The main challenges are:

- **Fragmented Data**: Information about occurrences is often scattered and not accessible to the public.
- **Difficulty in Reporting**: Citizens lack a direct and simplified channel to report incidents.
- **Lack of Visual Analysis**: The absence of heatmaps and analytical dashboards prevents the identification of critical areas.
- **Information Security**: The need for a system that ensures user anonymity and data security.

## Solution

Our RESTful API is designed to solve these challenges by offering:

- **🔒 Secure Authentication**: Login and registration system with hashed passwords (Bcrypt) and token-based authorization (JWT Access and Refresh Tokens).
- **📝 Occurrence CRUD Operations**: Complete endpoints to create, read, update, and delete criminal occurrence records.
- **📸 Media Upload Support**: Ability to handle image uploads to enrich the details of occurrences (using Multer).
- **🌐 Centralized Access**: Provides a single, reliable source of data for any client (web, mobile).
- **🚀 Scalability**: A service-based architecture that allows for the easy expansion of new features.

## Tech Stack

| Technology | Purpose |
|------------|-----------|
| [Node.js](https://nodejs.org/) | Runtime Environment |
| [Express.js](https://expressjs.com/) | Web Framework |
| [MongoDB](https://www.mongodb.com/) | NoSQL Database |
| [Mongoose](https://mongoosejs.com/) | ODM for MongoDB |
| [JSON Web Token](https://jwt.io/) | Authentication & Authorization |
| [Bcrypt](https://www.npmjs.com/package/bcrypt) | Password Hashing |
| [Multer](https://www.npmjs.com/package/multer) | File Upload Middleware |
| [Dotenv](https://www.npmjs.com/package/dotenv) | Environment Variable Management |
| [Nodemon](https://nodemon.io/) | Development Live-Reload |

## 📁 Project Structure

```
├── backend/
│   ├── src/
│   │   ├── config/
│   │   │   ├── db.js          # MongoDB connection setup
│   │   ├── controllers/
│   │   │   ├── ocorrenciaController.js # Logic for occurrence routes
│   │   │   └── usuarioController.js    # Logic for user routes (auth)
│   │   ├── models/
│   │   │   ├── Ocorrencia.js    # Mongoose schema for occurrences
│   │   │   └── Usuario.js       # Mongoose schema for users
│   │   ├── routes/
│   │   │   ├── ocorrenciaRoutes.js # Definition of occurrence endpoints
│   │   │   └── usuarioRoutes.js    # Definition of user endpoints
│   │   └── server.js          # Express application entry point
│   ├── .env.example           # Example environment variables file
│   ├── .gitignore             # Files ignored by Git
│   └── package.json           # Project dependencies and scripts
```

## 🚀 Quick Start Guide

### Prerequisites

-   Node.js (v18 or higher)
-   npm or yarn
-   A MongoDB instance (local or on a service like [MongoDB Atlas](https://www.mongodb.com/cloud/atlas))

### Installation

1.  **Clone the repository**
    ```bash
    git clone [https://github.com/DiegoPereira100/crimwatch-backend](https://github.com/DiegoPereira100/crimwatch-backend)
    cd crimwatch_dsw/backend
    ```

2.  **Install dependencies**
    ```bash
    npm install
    # or
    yarn install
    ```

3.  **Configure Environment Variables**

    Create a `.env` file in the `backend` root folder, using the template below.

    ```env
    # Server Configuration
    PORT=4000

    # Database Configuration
    MONGO_URI=mongodb+srv://<user>:<password>@<cluster-url>/<database-name>?retryWrites=true&w=majority

    # Security & JWT
    JWT_SECRET=your_secret_key_for_access_token
    JWT_REFRESH_SECRET=your_secret_key_for_refresh_token
    JWT_ACCESS_EXPIRES_IN=15m
    JWT_REFRESH_EXPIRES_IN=7d
    ```

    **Environment Variables Explained:**

| Variable | Description | Example | Required |
| :--- | :--- | :--- | :--- |
| `PORT` | The port where the server will run. | `4000` | ❌ No |
| `MONGO_URI` | Connection string for your MongoDB database. | `mongodb://localhost:27017/crimwatch` | ✅ Yes |
| `JWT_SECRET` | Secret key for signing **Access Tokens**. | `random_key_1` | ✅ Yes |
| `JWT_REFRESH_SECRET`| Secret key for signing **Refresh Tokens**. | `random_key_2` | ✅ Yes |
| `JWT_ACCESS_EXPIRES_IN`| Access Token expiration time. | `15m` | ❌ No |
| `JWT_REFRESH_EXPIRES_IN`| Refresh Token expiration time. | `7d` | ❌ No |

> **Note**: Replace the values in `MONGO_URI` with your actual MongoDB credentials. JWT keys should be long, random strings.

4.  **Start the development server**

    This command uses `nodemon` to automatically restart the server on code changes.
    ```bash
    npm run dev
    ```

    The server will be running on `http://localhost:4000` (or the port you defined).

5.  **Start the production server**
    ```bash
    npm start
    ```

## 🔗 Related Projects

-   **Web Frontend**: [CrimWatch Frontend](https://github.com/DiegoPereira100/crimwatch)
