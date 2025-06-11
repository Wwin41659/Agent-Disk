backend/
├── server.js                # 入口文件
├── config/
│   └── db.js                # 数据库连接配置
├── models/
│   ├── User.js              # 用户模型
│   ├── Match.js             # 比赛模型
│   ├── Bet.js               # 竞猜记录模型
├── routes/
│   ├── auth.js              # 注册登录
│   ├── match.js             # 比赛接口
│   ├── bet.js               # 竞猜接口
├── controllers/
│   └── ...                  # 各个业务逻辑
├── middleware/
│   └── auth.js              # JWT 验证中间件
├── .env
└── package.json



mkdir backend
cd backend
npm init -y
npm install express mongoose jsonwebtoken bcryptjs dotenv cors


// backend/server.js
const express = require('express');
const dotenv = require('dotenv');
const cors = require('cors');
const connectDB = require('./config/db');

dotenv.config();
connectDB();

const app = express();
app.use(cors());
app.use(express.json());

// 路由
app.use('/api/auth', require('./routes/auth'));
app.use('/api/match', require('./routes/match'));
app.use('/api/bet', require('./routes/bet'));



// backend/server.js
const express = require('express');
const dotenv = require('dotenv');
const cors = require('cors');
const connectDB = require('./config/db');

dotenv.config();
connectDB();

const app = express();
app.use(cors());
app.use(express.json());

// 路由
app.use('/api/auth', require('./routes/auth'));
app.use('/api/match', require('./routes/match'));
app.use('/api/bet', require('./routes/bet'));

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});



// backend/config/db.js
const mongoose = require('mongoose');

const connectDB = async () => {
  try {
    await mongoose.connect(process.env.MONGO_URI);
    console.log('MongoDB connected');
  } catch (err) {
    console.error(err.message);
    process.exit(1);
  }
};

module.exports = connectDB;



// backend/models/User.js
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  username: { type: String, unique: true },
  password: { type: String },
  points: { type: Number, default: 100 }, // 初始积分
  inviteCode: { type: String, unique: true }, // 系统分配的邀请码
  invitedBy: { type: String }, // 邀请人邀请码
  inviteCount: { type: Number, default: 0 }, // 推荐人数
}, { timestamps: true });

module.exports = mongoose.model('User', userSchema);


MONGO_URI=mongodb+srv://<你的账号>:<密码>@cluster.mongodb.net/yourdb
JWT_SECRET=your_jwt_secret_key




