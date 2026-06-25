# QuantDinger + IBKR 连接配置记录

## 已完成的步骤 ✅

- [x] **IB Gateway 10.48 已安装** — `~/Applications/IB Gateway 10.48/`
- [x] **IB Gateway API 已启用** — 端口 `4001`（生产环境）
- [x] **ib_insync 已安装** — Python IBKR API 库
- [x] **QuantDinger 已克隆** — `/Users/macair/Documents/QuantDinger/`
- [x] **.env 已配置** — `ALLOW_LOCAL_DESKTOP_BROKERS=true`, `IBKR_ORDER_CLIENT_ID=7`
- [x] **连接验证通过** — 2 个 IBKR 账户已连接，协议 v176

## 账户信息

| 账户 | 净值 | 购买力 |
|------|------|--------|
| U12813037 | $285.02 | $285.02 |
| U19865561 | $1.50 | $1.50 |

## 启动完整 QuantDinger Web UI

要运行完整量化交易 Web UI，需要安装 Docker Desktop：

### 1. 安装 Docker Desktop

https://docs.docker.com/desktop/setup/install/mac-install/

下载 Apple Silicon 版本。

### 2. 启动服务

```bash
cd /Users/macair/Documents/QuantDinger
docker compose up -d
```

### 3. 访问 Web UI

http://localhost:8888 — 账号: `admin` / `admin123`

### 4. Web UI 中连接 IB Gateway

Settings → Broker Accounts → Add Broker → 选择 Interactive Brokers

| 字段 | 值 |
|------|------|
| Host | `127.0.0.1` |
| Port | `4001` |
| Client ID | `7` |
| Account | 留空自动选择 |

## 注意事项

1. **API 只读模式**: IB Gateway 默认只读，如需下单去 Edit → API → Settings 取消勾选 "Read Only"
2. **行情订阅**: AAPL 等美股实时行情需要向 IBKR 申请市场数据订阅
3. **每天重登录**: IB Gateway 每 24 小时自动断开，需重新登录
