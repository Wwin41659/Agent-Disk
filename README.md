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
