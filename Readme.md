# 🚪 智能校园门禁管理系统
> Campus Access Control System Based on Face Recognition

![Vue](https://img.shields.io/badge/Vue-3.2-green)
![Node.js](https://img.shields.io/badge/Node.js-16.x-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8-blue)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange)
![Docker](https://img.shields.io/badge/Docker-Support-blueviolet)
![License](https://img.shields.io/badge/License-MIT-yellow)

> 🎓 毕业设计项目 | 基于人脸识别的校园通行管理系统 | 前后端分离架构

---

## 📋 目录

- [项目简介](#-项目简介)
- [系统预览](#-系统预览)
- [功能模块](#-功能模块)
- [技术栈](#-技术栈)
- [系统架构](#-系统架构)
- [数据库设计](#-数据库设计)
- [快速开始](#-快速开始)
- [接口文档](#-接口文档)
- [部署指南](#-部署指南)
- [项目结构](#-项目结构)
- [开发规范](#-开发规范)
- [参考文献](#-参考文献)

---

## 📖 项目简介

本系统是为智慧校园场景设计的**人脸识别门禁管理系统**，采用前后端分离架构，集成微信小程序、Web管理后台、人脸识别服务三大核心模块。系统支持学生人脸录入、通行申请、教师审批、实时人脸验证等完整业务流程，旨在提升校园安全管理的智能化水平。

### 🔑 核心特性
- ✅ 微信小程序端：便捷的人脸采集与通行申请
- ✅ 教师管理端：申请审批、班级权限管理
- ✅ Web验证端：摄像头实时人脸识别通行
- ✅ 后台管理系统：用户/班级/日志统一管理
- ✅ Docker一键部署：支持容器化快速上线

---

## 🖼️ 系统预览

### Web 管理后台
![管理员后台动图](./images/Video_2024-03-08_200357.gif "管理员后台演示")
![管理员后台动图](./images/Video_2024-03-08_200527.gif "管理员后台演示")
![管理员后台动图](./images/Video_2024-03-08_200607.gif "管理员后台演示")
![管理员后台动图](./images/Video_2024-03-08_200725.gif "管理员后台演示")
![管理员后台动图](./images/Video_2024-03-08_200806.gif "管理员后台演示")
![管理员后台动图](./images/Video_2024-03-08_200925.gif "管理员后台演示")

### 微信小程序端
<img src="./images/Video_2024-03-08_201902.gif" alt="小程序演示" title="小程序演示" width="45%"/>
<img src="./images/Video_2024-03-08_203223.gif" alt="小程序演示" title="小程序演示" width="45%"/>

> 💡 完整演示流程：![Flow](docs/images/demo-flow.gif)

---

## 🧩 功能模块

### 👤 学生端（微信小程序）
| 功能 | 说明 |
|------|------|
| 🔐 用户登录 | 学号+密码认证，支持记住登录状态 |
| 📷 人脸录入 | 调用小程序摄像头采集人脸，自动上传并提取特征 |
| 📝 通行申请 | 填写通行理由、有效期、次数，提交教师审批 |
| 📊 申请记录 | 查看历史申请状态（待审/通过/拒绝/撤销） |
| 👤 个人信息 | 修改密码、查看绑定班级、更新头像 |

### 👨‍🏫 教师端（微信小程序 + Web）
| 功能 | 说明 |
|------|------|
| 🔐 教师登录 | 工号+密码认证，权限隔离 |
| 📋 申请审批 | 查看所带班级学生的通行申请，支持批量审批 |
| 👥 班级管理 | 查看班级学生列表、导出名单 |
| 📈 通行统计 | 按日期/班级查看通行记录统计 |

### 🌐 Web验证端（门禁终端）
| 功能 | 说明 |
|------|------|
| 📷 实时识别 | 调用摄像头捕获人脸，与数据库特征比对 |
| ✅ 通行反馈 | 识别成功显示姓名+班级+通行权限，失败提示原因 |
| 📝 通行日志 | 自动记录每次验证结果（时间、人员、结果） |

### ⚙️ 后台管理系统（Web）
| 功能 | 说明 |
|------|------|
| 👥 用户管理 | 管理员/教师/学生账号的增删改查 |
| 🏫 班级管理 | 班级信息维护、教师-班级关联配置 |
| 📊 日志审计 | 通行记录、操作日志查询与导出 |
| ⚙️ 系统配置 | 人脸识别阈值、有效期规则等参数设置 |

---

## 🛠️ 技术栈

### 前端
| 模块 | 技术 | 版本 | 说明 |
|------|------|------|------|
| 小程序端 | uni-app + Vue3 | 3.4+ | 跨端开发，一套代码多端发布 |
| 管理后台 | Vue3 + Element Plus | 3.2+ | 响应式后台管理界面 |
| 验证终端 | Vue3 + WebRTC | 3.2+ | 浏览器端摄像头调用 |

### 后端
| 服务 | 技术 | 版本 | 职责 |
|------|------|------|------|
| Node服务 | Express + JWT | 4.x | 业务接口、用户认证、权限控制 |
| Python服务 | Flask + OpenCV | 3.8+ | 人脸特征提取、1:1/1:N比对 |
| 数据库 | MySQL + Redis | 8.0+ | 结构化数据存储 + 缓存加速 |

### 运维
| 工具 | 用途 |
|------|------|
| Docker + docker-compose | 多服务容器编排，一键部署 |
| Nginx | 反向代理、静态资源服务 |
| PM2 | Node进程守护与日志管理 |

---

## 🏗️ 系统架构

```
┌─────────────────────────────────────────┐
│              客户端层                    │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐   │
│  │ 微信小程序│ │ Web管理端│ │ 验证终端│   │
│  └────┬────┘ └────┬────┘ └────┬────┘   │
└───────┼───────────┼───────────┼────────┘
        │           │           │
        ▼           ▼           ▼
┌─────────────────────────────────────────┐
│              网关层 (Nginx)              │
│  • 反向代理  • 静态资源  • 负载均衡      │
└────────────────┬────────────────────────┘
                 │
        ┌────────┴────────┐
        ▼                 ▼
┌─────────────┐ ┌─────────────────┐
│ Node.js服务  │ │ Python人脸服务   │
│ • 用户认证   │ │ • 特征提取      │
│ • 业务逻辑   │ │ • 1:1/1:N比对   │
│ • 数据转发   │ │ • 活体检测(扩展)│
└──────┬──────┘ └────────┬────────┘
       │                 │
       ▼                 ▼
┌─────────────────────────────────┐
│           数据层                 │
│  ┌─────────┐  ┌─────────┐       │
│  │ MySQL   │  │ Redis   │       │
│  │ 业务数据│  │ 缓存/会话│       │
│  └─────────┘  └─────────┘       │
└─────────────────────────────────┘
```

---

## 🗄️ 数据库设计

### 核心表结构

| 表名 | 说明 | 关键字段 |
|------|------|----------|
| `admin` | 管理员账号 | id, account, password, name, email |
| `teachers` | 教师账号 | id, account(工号), password, name, classID |
| `students` | 学生账号 | id, account(学号), password, name, classID |
| `class` | 班级信息 | id(班级号), name, create_time |
| `face` | 人脸特征 | id(学号/工号), features(特征向量), facepic |
| `application_logs` | 通行申请 | id, stuID, reason, state, validityDate |
| `teacher_class_map` | 教师-班级关联 | teacher_id, class_id, is_master |

### ER关系图
```
students ──┬── class (N:1)
           ├── face (1:1)
           └── application_logs (1:N)

teachers ──┬── teacher_class_map (1:N)
           └── class (N:M via map)

application_logs ── students (N:1)
```

> 📄 完整SQL脚本见：`/sqlfile/camp.sql`

---

## 🚀 快速开始

### 环境要求
```bash
- Node.js >= 16.x
- Python >= 3.8
- MySQL >= 8.0
- Docker & docker-compose (推荐)
```

### 方式一：Docker 一键部署（推荐）
```bash
# 1. 克隆项目
git clone https://github.com/CR-YZ/campusAccessControl_server.git
cd campusAccessControl_server

# 2. 配置环境变量（可选）
cp .env.example .env
# 修改 .env 中的数据库密码、端口等配置

# 3. 启动服务
docker-compose up -d

# 4. 初始化数据库
docker exec -i adminmysql mysql -uroot -p123456 < sqlfile/camp.sql

# 5. 访问服务
- 管理后台：http://localhost:80
- 接口文档：http://localhost:8082/api-docs
```

### 方式二：本地开发部署
```bash
# ========== Node服务 ==========
cd admin_server
npm install
# 配置 config/db.js 中的数据库连接
npm run serve  # 启动端口: 8082

# ========== Python人脸服务 ==========
cd face_server
pip install -r requirements.txt
python app.py  # 启动端口: 5000

# ========== 前端项目 ==========
# 管理后台
cd admin_ui
npm install
npm run serve  # http://localhost:8080

# 微信小程序（需微信开发者工具）
cd uniapp_ordinaryUsers_ui
# 使用HBuilderX导入项目，运行到微信小程序
```

---

## 📡 接口文档

### 认证相关
| 方法 | 路径 | 说明 | 参数 |
|------|------|------|------|
| POST | `/api/auth/login` | 用户登录 | `{account, password, type}` |
| POST | `/api/auth/register` | 学生注册 | `{account, password, name, classID}` |
| GET | `/api/auth/info` | 获取用户信息 | Header: `Authorization: Bearer token` |

### 人脸相关
| 方法 | 路径 | 说明 | 参数 |
|------|------|------|------|
| POST | `/api/face/upload` | 上传人脸照片 | FormData: `file`, `userId` |
| POST | `/api/face/verify` | 人脸验证 | FormData: `image` |
| GET | `/api/face/status` | 查询人脸录入状态 | `?userId=xxx` |

### 通行申请
| 方法 | 路径 | 说明 | 参数 |
|------|------|------|------|
| POST | `/api/application/submit` | 提交申请 | `{reason, time, validityDate}` |
| GET | `/api/application/list` | 申请列表 | `?page=1&state=0` |
| PUT | `/api/application/review` | 审批申请 | `{id, state, remark}` |

> 🔍 完整接口文档可使用 [Apifox](https://apifox.com/) 导入 `/docs/api.json` 查看

---

## 🐳 部署指南

### 生产环境配置建议
```yaml
# docker-compose.prod.yml 示例
version: '3.8'
services:
  mysql:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: ${DB_PASSWORD}  # 使用环境变量
    volumes:
      - ./data/mysql:/var/lib/mysql
      - ./conf/mysql.cnf:/etc/mysql/conf.d/custom.cnf
  
  node-api:
    build: ./admin_server
    environment:
      - NODE_ENV=production
      - JWT_SECRET=${JWT_SECRET}
    deploy:
      replicas: 2  # 多实例部署
  
  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
      - "443:443"  # HTTPS
    volumes:
      - ./conf/nginx.conf:/etc/nginx/nginx.conf
      - ./ssl:/etc/nginx/ssl  # SSL证书
```

### 安全加固建议
1. 🔐 所有接口启用 HTTPS
2. 🔑 JWT Token 设置合理过期时间（建议2小时）
3. 🛡️ 人脸特征数据加密存储（AES-256）
4. 🚫 接口增加频率限制（express-rate-limit）
5. 📝 关键操作记录审计日志

---

## 📁 项目结构

```
campusAccessControl_server/
├── admin_server/              # Node.js 后端服务
│   ├── config/               # 配置文件 (db, jwt)
│   ├── controller/           # 业务逻辑层
│   ├── router/               # 路由定义 (admin.js, user.js)
│   ├── middleware/           # 中间件 (auth, validate)
│   ├── utils/                # 工具函数
│   ├── main.js               # 入口文件
│   └── package.json
│
├── face_server/              # Python 人脸识别服务
│   ├── app.py                # Flask入口
│   ├── face_recognizer.py    # 特征提取/比对核心
│   ├── requirements.txt
│   └── models/               # 预训练模型
│
├── admin_ui/                 # Web管理后台 (Vue3)
│   ├── src/
│   │   ├── api/              # 接口封装
│   │   ├── views/            # 页面组件
│   │   ├── store/            # Pinia状态管理
│   │   └── router/           # 路由配置
│   └── vite.config.js
│
├── uniapp_ordinaryUsers_ui/  # 微信小程序 (uni-app)
│   ├── pages/                # 页面文件
│   ├── api/                  # 请求封装
│   └── manifest.json         # 小程序配置
│
├── sqlfile/                  # 数据库脚本
│   └── camp.sql              # 完整建表+初始化数据
│
├── docs/                     # 文档目录
│   ├── api.json              # Apifox接口定义
│   └── deployment.md         # 详细部署手册
│
├── Dockerfile                # Node服务镜像构建
├── docker-compose.yml        # 多服务编排
└── README.md                 # 项目说明
```

---

## 📏 开发规范

### Git提交规范
```bash
# 格式: <type>(<scope>): <subject>
git commit -m "feat(user): 添加学生批量导入功能"
git commit -m "fix(auth): 修复JWT token过期校验逻辑"
git commit -m "docs: 更新接口文档"

# type类型:
#   feat: 新功能  |  fix: 修复问题  |  docs: 文档
#   style: 格式调整 | refactor: 重构 | test: 测试
```

### 代码风格
- 前端：ESLint + Prettier（`.eslintrc.js` 统一配置）
- 后端：遵循 Airbnb JavaScript Style Guide
- Python：遵循 PEP8，使用 `flake8` 检查

### 分支管理
```
main          # 生产分支（保护）
develop       # 开发集成分支
feature/xxx   # 功能开发分支
hotfix/xxx    # 紧急修复分支
```

---

## 📚 参考文献

### 技术参考
1. 微信小程序开发文档: https://developers.weixin.qq.com/miniprogram/dev/framework/
2. Express官方指南: https://expressjs.com/zh-cn/guide/routing.html
3. OpenCV人脸识别教程: https://docs.opencv.org/4.x/d2/d99/tutorial_js_face_recognition.html
4. Vue3最佳实践: https://v3.cn.vuejs.org/guide/introduction.html

### 开源依赖
- [face_recognition](https://github.com/ageitgey/face_recognition) - Python人脸库
- [element-plus](https://element-plus.org/) - Vue3组件库
- [uni-app](https://uniapp.dcloud.io/) - 跨端开发框架

---

## 📬 联系作者

- 👤 作者：[CR-YZ]
- 📧 邮箱：[xiaoraotest@outlook.com]

> ⚠️ 本项目仅用于毕业设计学习研究，如需商用请联系作者获取授权。
