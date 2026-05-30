# Crash Game 💥

یہ ایک مکمل **Crash Game** ہے جس میں:

## Features ✨

- ✅ User Authentication (Login/Signup)
- ✅ Real-time WebSocket Communication
- ✅ Multiplier-based Betting System
- ✅ Cashout Mechanism
- ✅ Bet History & Statistics
- ✅ Live Game Updates
- ✅ Responsive UI
- ✅ Database Integration (MySQL)

## Project Structure 📁

```
backend/
├── controllers/        # Business logic
├── routes/            # API endpoints
├── services/          # Crash engine, utilities
├── socket/            # WebSocket handlers
├── middleware/        # Auth middleware
├── models/            # Database models
└── server.js          # Main server file

frontend/
├── components/        # React components
├── pages/            # Page components
├── services/         # API & Socket services
└── App.jsx           # Main app component
```

## Setup Instructions 🚀

### Backend Setup

1. **Database Setup**
```bash
mysql -u root -p
CREATE DATABASE crash_game;
USE crash_game;
SOURCE database/schema.sql;
```

2. **Install Dependencies**
```bash
cd backend
npm install
```

3. **Environment Configuration**
```bash
cp .env.example .env
# Edit .env with your database credentials
```

4. **Start Server**
```bash
npm start
# OR for development with auto-reload
npm run dev
```

### Frontend Setup

1. **Install Dependencies**
```bash
cd frontend
npm install
```

2. **Environment Configuration**
```bash
cp .env.example .env
# Update API URLs if needed
```

3. **Start Development Server**
```bash
npm start
```

The app will open at `http://localhost:3000`

## Game Flow 🎮

1. **User Login/Signup** → Creates account with $1000 starting balance
2. **Place Bet** → Select bet amount and place bet
3. **Game Round** → Multiplier increases from 1.00x
4. **Cashout or Lose** → 
   - Cashout before crash → Win profit
   - Don't cashout → Lose bet (if crash)
5. **History** → View all past bets and statistics

## WebSocket Events 📡

### Client → Server
- `PLACE_BET` - Place a bet
- `CASHOUT` - Cash out current bet

### Server → Client
- `ROUND_START` - New round begins
- `MULTIPLIER_UPDATE` - Multiplier changes
- `BET_PLACED` - User places bet
- `CASHOUT` - User cashed out
- `ROUND_CRASH` - Round crashed

## Database Schema 🗄️

### Users Table
- id, username, email, password, balance, created_at

### Rounds Table
- id, crash_multiplier, status, started_at, ended_at

### Bets Table
- id, user_id, round_id, bet_amount, cashout_multiplier, profit, status

### Transactions Table
- id, user_id, bet_id, amount, type, status

## API Endpoints 🔌

### Authentication
- `POST /api/auth/signup` - Create account
- `POST /api/auth/login` - Login
- `GET /api/auth/verify` - Verify token

### Game
- `GET /api/game/current-round` - Get active round
- `GET /api/game/history` - Get round history
- `GET /api/game/stats` - Get user statistics

### Betting
- `POST /api/wallet/bet` - Place bet
- `POST /api/wallet/cashout` - Cash out
- `GET /api/wallet/bet-history` - Get bet history

## Tech Stack 🛠️

**Backend:**
- Node.js + Express.js
- Socket.io
- MySQL2
- JWT Authentication
- Bcryptjs

**Frontend:**
- React 18
- React Router
- Axios
- Socket.io Client
- CSS3

## Security Features 🔒

- JWT Token Authentication
- Password Hashing (Bcryptjs)
- Server-side Validation
- CORS Configuration
- Database Transaction Handling

## Future Enhancements 🚀

- [ ] Admin Dashboard
- [ ] Leaderboard System
- [ ] Deposit/Withdrawal System
- [ ] Email Verification
- [ ] Two-Factor Authentication
- [ ] Mobile App
- [ ] Advanced Statistics
- [ ] Sound Effects & Animations

---

**Made with ❤️ for crash game enthusiasts!**
