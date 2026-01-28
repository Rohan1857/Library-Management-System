# 📚 Library Management System

A full-stack Library Management System built with the MERN stack (MongoDB, Express.js, React, Node.js). This application provides a comprehensive solution for managing library operations including book management, borrowing, reservations, fines, donations, and more.

Live Link - https://library-system-rohan.vercel.app/

![License](https://img.shields.io/badge/license-ISC-blue.svg)
![Node](https://img.shields.io/badge/node-%3E%3D18.0.0-green.svg)
![React](https://img.shields.io/badge/react-18.3.1-61dafb.svg)

## 📋 Table of Contents

- [Features](#-features)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [API Endpoints](#-api-endpoints)
- [Demo Account](#-demo-account)
- [Deployment](#-deployment)
- [Screenshots](#-screenshots)

## ✨ Features

### User Features
- **Authentication** - Secure login/signup with email verification
- **Book Browsing** - Search, filter, and view book details
- **Book Borrowing** - Borrow books with due date tracking
- **Reservations** - Reserve books that are currently unavailable
- **Fine Management** - View and pay fines for overdue books
- **Book Donations** - Donate books to the library
- **Book Suggestions** - Suggest new books for the library to acquire
- **Profile Management** - Update personal information and view borrowing history

### Admin Features
- **Dashboard** - Overview of library statistics and activities
- **Book Management** - Add, edit, delete, and manage book inventory
- **User Management** - Manage user accounts and roles
- **Borrowing Management** - Track and manage all borrowings
- **Reservation Management** - Handle book reservations with auto-allocation
- **Fine Management** - Configure and manage fine policies
- **Transaction History** - View all payment transactions
- **Reports** - Generate various library reports
- **Inventory Issues** - Track and resolve inventory problems
- **Archive** - Access archived records
- **Donation Management** - Review and process book donations
- **Suggestion Management** - Review user book suggestions

## 🏗 Architecture

<img width="2624" height="1632" alt="Gemini_Generated_Image_ud74ecud74ecud74" src="https://github.com/user-attachments/assets/43fad5ac-b553-4e31-bbf2-55379b4fb7c5" />


```
┌─────────────────────────────────────────────────────────────────┐
│                         Client (React)                          │
│                    Hosted on Vercel                             │
├─────────────────────────────────────────────────────────────────┤
│  React + Redux Toolkit │ React Router │ Tailwind CSS │ Axios   │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                      Server (Node.js/Express)                    │
│                     Hosted on Render                             │
├─────────────────────────────────────────────────────────────────┤
│  Express.js │ JWT Auth │ Rate Limiting │ Email Service          │
└─────────────────────────────────────────────────────────────────┘
                                │
                    ┌───────────┼───────────┐
                    ▼           ▼           ▼
              ┌──────────┐ ┌──────────┐ ┌──────────┐
              │ MongoDB  │ │Cloudinary│ │ AWS S3   │
              │ Atlas    │ │ (Images) │ │ (Files)  │
              └──────────┘ └──────────┘ └──────────┘
```

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| React 18 | UI Library |
| Redux Toolkit | State Management |
| React Router v7 | Routing |
| Tailwind CSS | Styling |
| Axios | HTTP Client |
| Chart.js | Data Visualization |
| Lucide React | Icons |
| React Toastify | Notifications |
| Vite | Build Tool |

### Backend
| Technology | Purpose |
|------------|---------|
| Node.js | Runtime Environment |
| Express.js | Web Framework |
| MongoDB | Database |
| Mongoose | ODM |
| JWT | Authentication |
| Bcrypt | Password Hashing |
| Nodemailer | Email Service |
| Cloudinary | Image Storage |
| AWS S3 | File Storage |
| Razorpay | Payment Gateway |
| Helmet | Security |
| Express Rate Limit | Rate Limiting |

## 🚀 Getting Started

### Prerequisites

- Node.js >= 18.0.0
- npm or yarn
- MongoDB Atlas account (or local MongoDB)
- Cloudinary account
- AWS S3 bucket (optional)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/Library-Management-System.git
   cd Library-Management-System
   ```

2. **Install server dependencies**
   ```bash
   cd server
   npm install
   ```

3. **Install client dependencies**
   ```bash
   cd ../client
   npm install
   ```

4. **Set up environment variables**
   
   Create a `config.env` file in the `server/config` directory (see [Environment Variables](#-environment-variables))

5. **Run the development servers**

   **Server (from `/server` directory):**
   ```bash
   npm run dev
   ```

   **Client (from `/client` directory):**
   ```bash
   npm run dev
   ```

6. **Access the application**
   - Frontend: `http://localhost:5173`
   - Backend: `http://localhost:5000`

## 🔐 Environment Variables

Create a `config.env` file in the `server/config` directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database
MONGO_URI=your_mongodb_connection_string

# JWT
JWT_SECRET_KEY=your_jwt_secret_key
JWT_EXPIRE=7d
COOKIE_EXPIRE=7

# Frontend URL (for CORS)
FRONTEND_URL=http://localhost:5173

# Email Configuration
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_SERVICE=gmail
SMTP_EMAIL=your_email@gmail.com
SMTP_PASSWORD=your_app_password

# Cloudinary
CLOUDINARY_CLIENT_NAME=your_cloud_name
CLOUDINARY_CLIENT_API=your_api_key
CLOUDINARY_CLIENT_SECRET=your_api_secret

# AWS S3 (Optional)
AWS_BUCKET_NAME=your_bucket_name
AWS_BUCKET_REGION=your_region
AWS_ACCESS_KEY=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key

# Razorpay (Optional)
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_secret
```

## 📡 API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/v1/auth/register` | Register new user |
| POST | `/api/v1/auth/login` | User login |
| GET | `/api/v1/auth/logout` | User logout |
| POST | `/api/v1/auth/password/forgot` | Forgot password |
| PUT | `/api/v1/auth/password/reset/:token` | Reset password |

### Books
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/books` | Get all books |
| GET | `/api/v1/books/:id` | Get book by ID |
| POST | `/api/v1/books` | Add new book (Admin) |
| PUT | `/api/v1/books/:id` | Update book (Admin) |
| DELETE | `/api/v1/books/:id` | Delete book (Admin) |

### Borrowing
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/borrow` | Get all borrowings |
| POST | `/api/v1/borrow` | Create borrowing |
| PUT | `/api/v1/borrow/:id/return` | Return book |

### Reservations
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/reservations` | Get all reservations |
| POST | `/api/v1/reservations` | Create reservation |
| DELETE | `/api/v1/reservations/:id` | Cancel reservation |

### Users
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/users` | Get all users (Admin) |
| GET | `/api/v1/users/:id` | Get user by ID |
| PUT | `/api/v1/users/:id` | Update user |
| DELETE | `/api/v1/users/:id` | Delete user (Admin) |

### Transactions
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/transactions` | Get all transactions |
| POST | `/api/v1/transactions` | Create transaction |

### Donations
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/donations` | Get all donations |
| POST | `/api/v1/donations` | Submit donation |
| PUT | `/api/v1/donations/:id` | Update donation status (Admin) |

### Suggestions
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/suggestions` | Get all suggestions |
| POST | `/api/v1/suggestions` | Submit suggestion |
| PUT | `/api/v1/suggestions/:id` | Update suggestion status (Admin) |

## 🔑 Demo Account

You can use the following test credentials to explore the application:

| Role | Email | Password |
|------|-------|----------|
| User | `user@test.com` | `password123` |



## 🌐 Deployment

### Frontend (Vercel)

1. Connect your GitHub repository to Vercel
2. Set the root directory to `client`
3. Configure build settings:
   - Build Command: `npm run build`
   - Output Directory: `dist`
4. Add environment variables if needed

### Backend (Render)

1. Create a new Web Service on Render
2. Connect your GitHub repository
3. Configure settings:
   - Root Directory: `server`
   - Build Command: `npm install`
   - Start Command: `npm start`
4. Add all environment variables from `config.env`

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 📧 Contact

For any queries or support, please reach out through GitHub issues.

---

## 📸 Screenshots



### Login Page
<img width="1912" height="1058" alt="Screenshot 2026-01-28 222818" src="https://github.com/user-attachments/assets/c7dff7ad-2c4e-4ba1-b71a-07715b1fa37b" />


### Dashboard
<img width="1919" height="1058" alt="image" src="https://github.com/user-attachments/assets/341380d6-a1d8-430b-af03-2be1d67dd661" />


### Book Catalog
<img width="1919" height="1056" alt="Screenshot 2026-01-28 223028" src="https://github.com/user-attachments/assets/bcd2c822-354f-478f-a32b-4e7b6d0b064a" />


### Book Details
<img width="1919" height="1055" alt="image" src="https://github.com/user-attachments/assets/8e9bd7a7-9b9f-4bd9-b22f-3a5ba0630731" />


### Borrowing Management
<img width="1919" height="1058" alt="image" src="https://github.com/user-attachments/assets/f2364a5e-d06f-4b22-b789-1e3987b2e02f" />


### Batch Register
<img width="1919" height="1054" alt="image" src="https://github.com/user-attachments/assets/fddf7fb4-4561-4ea0-bcc4-fc0d7e3a9911" />


### User Management (Admin)
<img width="1919" height="1057" alt="image" src="https://github.com/user-attachments/assets/ec93a949-4823-4b65-8411-4b607a0c7abf" />


### Fine Management
<img width="1919" height="1059" alt="image" src="https://github.com/user-attachments/assets/70576cf8-9bd5-4e39-b110-de07ba3173cc" />


### Reports & Analytics
<img width="1919" height="1058" alt="image" src="https://github.com/user-attachments/assets/a04e3add-955e-4254-ac4f-39e6b2b45fff" />


### Profile Page
<img width="1919" height="1058" alt="image" src="https://github.com/user-attachments/assets/5f54e848-e157-4244-a30c-797278df624e" />

### Suggestions Page
<img width="1919" height="1055" alt="image" src="https://github.com/user-attachments/assets/5439b07c-162c-41a3-95f3-af789dde0237" />

### Archives
<img width="1919" height="1056" alt="image" src="https://github.com/user-attachments/assets/aa529abb-5bed-4977-b3b3-a420ace56f36" />

### Payment Gateway
<img width="1917" height="1061" alt="Screenshot 2026-01-28 222951" src="https://github.com/user-attachments/assets/05342727-1098-45ee-89a1-ec5fe08ef01a" />

### Fines(User)
<img width="1919" height="1055" alt="Screenshot 2026-01-28 223008" src="https://github.com/user-attachments/assets/f2091979-dc79-41b4-b83b-b57309227a6b" />

### Borrowed Books(User)
<img width="1911" height="1063" alt="Screenshot 2026-01-28 223020" src="https://github.com/user-attachments/assets/1dd198d2-e4be-44e4-8890-c693d831c1b5" />






---

<p align="center">Made with ❤️ for libraries everywhere</p>
