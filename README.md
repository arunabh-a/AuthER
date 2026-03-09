# AuthER - Full Stack Authentication App

A modern full-stack application with secure authentication using Node.js/Express backend and React frontend.

## 🚀 Features

- **Secure Authentication**: JWT access tokens + httpOnly refresh cookies
- **User Registration & Login**: Complete auth flow with validation
- **Profile Management**: User profile with editable fields
- **Token Rotation**: Automatic refresh token rotation for security
- **Modern UI**: Clean, responsive design with Shadcn/UI components
- **TypeScript**: Full type safety across frontend and backend

## 🛠️ Tech Stack

### Backend
- **Node.js** with **Express**
- **TypeScript** for type safety
- **Prisma ORM** with **PostgreSQL**
- **JWT** for access tokens
- **Argon2** for password hashing
- **HttpOnly cookies** for refresh tokens

### Frontend
- **React 19** with **TypeScript**
- **Vite** for fast development
- **React Router** for navigation
- **Shadcn/UI** components
- **Tailwind CSS** for styling

## 📦 Installation & Setup

### Prerequisites
- Node.js 18+
- PostgreSQL database
- npm or yarn

### 1. Clone Repository
```bash
git clone https://github.com/arunabh-a/Auth-Bare.git
cd Auth-Bare
```

### 2. Backend Setup

```bash
cd server
npm install
```

Create `.env` file in server directory:
```env
# Database
DATABASE_URL="postgresql://username:password@localhost:5432/AuthER_db"

# JWT
JWT_SECRET="your-super-secret-jwt-key-here"

# Server
PORT=4000
NODE_ENV=development

# Cookies
COOKIE_DOMAIN=localhost
REFRESH_TOKEN_EXP_DAYS=30
```

Setup database:
```bash
npx prisma migrate dev
npm run dev
```

### 3. Frontend Setup

```bash
cd ../client
npm install
npm run dev
```

### 4. Access Application

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:4000
- **Database**: Prisma Studio - `npx prisma studio`

## 🔐 Authentication Flow

1. **Registration/Login** → Sets httpOnly access + refresh cookies
2. **API Requests** → Cookies sent automatically by browser
3. **Token Refresh** → Automatic rotation when access token expires
4. **Logout** → Clears all cookies and revokes refresh tokens

## 📋 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/refresh` - Refresh access token
- `POST /api/auth/logout` - User logout

### User Management
- `GET /api/users/me` - Get current user profile
- `GET /api/users/user?userId=:id` - Get user by ID

## 🧪 Testing

Use the provided Postman collection (`AuthER-API.postman_collection.json`) to test all endpoints.

## 🔒 Security Features

- **HttpOnly Cookies**: Tokens inaccessible to JavaScript (XSS protection)
- **Secure Flags**: Proper cookie security in production
- **Token Rotation**: Refresh tokens are rotated on each use
- **Password Hashing**: Argon2 for secure password storage
- **CORS**: Properly configured for frontend access
- **Input Validation**: Comprehensive request validation

## 📱 Frontend Routes

- `/auth` - Login/Registration page
- `/main` - User profile dashboard (protected)

## 🚧 Development

### Backend Development
```bash
cd server
npm run dev          # Start with hot reload
npm run build        # Build for production
npm run start        # Start production server
```

### Frontend Development
```bash
cd client
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
```

### Database Operations
```bash
cd server
npx prisma studio              # Open database GUI
npx prisma migrate dev         # Create new migration
npx prisma migrate reset       # Reset database
npx prisma generate           # Regenerate Prisma client
```

## 📊 Project Structure

```
AuthER/
├── server/                    # Backend API
│   ├── src/
│   │   ├── middleware/        # Auth middleware
│   │   ├── routes/           # API routes
│   │   ├── utils/            # JWT & password utilities
│   │   └── index.ts          # Server entry point
│   ├── prisma/               # Database schema & migrations
│   └── package.json
├── client/                    # Frontend React app
│   ├── src/
│   │   ├── components/       # UI components
│   │   ├── hooks/            # Custom hooks
│   │   ├── pages/            # Route components
│   │   ├── service/          # API service layer
│   │   └── App.tsx           # App entry point
│   └── package.json
└── README.md
```

## 🎯 Key Implementation Details

### Secure Token Management
- Access tokens: 15-minute expiry, httpOnly cookies
- Refresh tokens: 30-day expiry, automatic rotation
- Both tokens cleared on logout

### API Integration
- Centralized API service with TypeScript interfaces
- Automatic token refresh on 401 responses
- Error handling with user-friendly messages

### UI/UX
- Clean, modern design with dark/light theme support
- Form validation and loading states
- Toast notifications for user feedback

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

---

**Built with ❤️ by [Arunabh](https://github.com/arunabh-a)**