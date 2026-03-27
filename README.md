# MiniMax API Key 管理平台

基于 PHP + MySQL + Vue3 的 MiniMax API Key 管理平台。

## 功能特性

- 🔐 **管理员认证** - Session-based 安全登录
- 🔑 **API Key 管理** - 生成/删除/启用禁用/重置用量
- ⚙️ **主 KEY 配置** - 配置 MiniMax API 主密钥
- 📊 **用量查询** - 实时查询每日/每月/累计用量
- 🌐 **API 代理** - 代理转发请求到 MiniMax API
- 📖 **对接文档** - 用户友好的 API 使用教程

## 技术栈

- **前端**: Vue3 + Axios (SPA)
- **后端**: PHP (原生, 无框架)
- **数据库**: MySQL
- **Web服务器**: Nginx + PHP-FPM

## 快速部署

### 1. 数据库配置

```sql
CREATE DATABASE mini_imoons_cn;
CREATE USER 'mini_imoons_cn'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON mini_imoons_cn.* TO 'mini_imoons_cn'@'localhost';
FLUSH PRIVILEGES;
```

### 2. 导入数据库结构

```bash
mysql -u mini_imoons_cn -p mini_imoons_cn < database.sql
```

### 3. 配置

编辑 `config/config.php` 修改数据库连接信息。

### 4. Nginx 配置

参考站点配置，确保 PHP-FPM 和 MySQL 正常运行。

## 目录结构

```
├── api/                    # API 接口
│   ├── admin/             # 管理接口
│   ├── query/            # 查询接口
│   └── v1_proxy.php     # API 代理
├── core/                  # 核心函数库
├── config/               # 配置文件
├── public/               # 前端页面
│   ├── index.html        # 管理后台
│   ├── query.html        # 用量查询
│   └── docs.html         # 对接教程
└── database.sql           # 数据库结构
```

## 登录信息

- 用户名: `admin`
- 密码: `Pf555b0cee!2026`

## API 接口

| 接口 | 方法 | 说明 |
|------|------|------|
| `/api/login` | POST | 管理员登录 |
| `/api/check` | GET | 检查登录状态 |
| `/api/logout` | POST | 登出 |
| `/api/admin/keys` | GET | 获取 Key 列表 |
| `/api/admin/key_generate` | POST | 生成新 Key |
| `/api/admin/key_toggle` | PUT | 启用/禁用 |
| `/api/admin/key_reset` | PUT | 重置用量 |
| `/api/admin/key_delete` | DELETE | 删除 Key |
| `/api/admin/masterkey` | GET/POST | 主 Key 配置 |
| `/api/query/usage` | GET | 用量查询 |
| `/v1/*` | * | 代理到 MiniMax API |

## 接入示例

```bash
curl -X POST https://your-domain.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-Api-Key: your-api-key" \
  -d '{
    "model": "MiniMax-M2.7",
    "messages": [{"role": "user", "content": "你好"}]
  }'
```

## License

MIT
