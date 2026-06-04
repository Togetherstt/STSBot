# STSBot

基于 `NoneBot2 + OneBot V11 + NapCatQQ` 的独立《杀戮尖塔 2》猜卡机器人项目，可单独作为 GitHub 仓库开源。

当前支持的命令：

- `@机器人 /猜卡`
- `@机器人 /提示`
- `@机器人 /结束猜卡`
- `@机器人 /猜卡测试 <卡牌名或ID>`
- `/猜卡 help`
- `python scripts/test_sts_card_guess_local.py --card 暴走`

## 项目结构

```text
STSBot/
├─ bot.py
├─ pyproject.toml
├─ requirements.txt
├─ .env.example
├─ README.md
├─ data/
│  └─ sts_card_guess/
│     └─ cards/
├─ scripts/
│  └─ test_sts_card_guess_local.py
├─ src/
│  └─ plugins/
│     └─ sts_card_guess/
└─ tests/
   └─ test_sts_card_guess.py
```

## 环境要求

- `Python 3.10+`

安装依赖：

```powershell
pip install -r requirements.txt
```

## 配置

将 `.env.example` 复制为 `.env` 后至少配置以下字段：

```env
ENVIRONMENT=dev
LOG_LEVEL=DEBUG
HOST=127.0.0.1
PORT=8080
COMMAND_START=["/"]
ONEBOT_ACCESS_TOKEN=your-token
ADMIN_QQ=123456789
STS_CARD_DATA_DIR=data/sts_card_guess/cards
```

字段说明：

- `PORT`：需与 NapCatQQ 的 OneBot V11 正向 WebSocket 端口一致
- `ONEBOT_ACCESS_TOKEN`：需与 NapCatQQ Access Token 一致
- `ADMIN_QQ`：允许使用 `/猜卡测试` 的管理员 QQ 号
- `STS_CARD_DATA_DIR`：卡牌 JSON 目录，默认使用仓库内置卡池

## 启动

```powershell
python bot.py
```

或：

```powershell
nb run --reload
```

## 本地验证

运行单元测试：

```powershell
python -m unittest tests.test_sts_card_guess
```

运行本地交互测试：

```powershell
python scripts/test_sts_card_guess_local.py --card 暴走
```

## 数据说明

仓库内置了一份 `STS2` 卡牌 JSON 数据，位于 `data/sts_card_guess/cards/`。该目录直接从原项目复制而来，仅作为猜卡玩法的数据源。

## GitHub 发布建议

如果你准备推到 GitHub，常用流程如下：

```powershell
git remote add origin <你的仓库地址>
git add .
git commit -m "Initial standalone STSBot release"
git push -u origin main
```
