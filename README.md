# STSBot

独立的《杀戮尖塔 2》猜卡机器人项目，基于 `NoneBot2 + OneBot V11 + NapCatQQ`。

这个仓库从[更大的机器人项目](https://github.com/Togetherstt/nailoong-bot)中拆分而来，只保留《杀戮尖塔 2》猜卡玩法所需的最小代码、数据和测试，方便单独维护与开源。

## 功能概览

当前支持的命令：

- `@机器人 /猜卡`
- `@机器人 /提示`
- `@机器人 /结束猜卡`
- `@机器人 /猜卡测试 <卡牌名或ID>`
- `/猜卡 help`
- `python scripts/test_sts_card_guess_local.py --card 暴走`

玩法规则摘要：

- 开局随机给出 3 条基础提示
- 10 秒后补齐第 4 条基础提示
- 之后每 60 秒揭示一部分卡牌描述
- 同一群同一时间只允许进行一局

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
- 推荐配合 `NapCatQQ + OneBot V11 正向 WebSocket`

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

## 接入 NapCatQQ

在 NapCatQQ 中启用 `OneBot V11` 的正向 WebSocket，并确保以下配置与 `.env` 一致：

- 地址：`127.0.0.1:8080`
- Access Token：与你的 `ONEBOT_ACCESS_TOKEN` 一致

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

## 开源边界

本仓库只包含《杀戮尖塔 2》猜卡功能本身，不包含原机器人项目中的其它插件、私有配置或运行数据。

## License

本项目使用 [MIT License](https://github.com/Togetherstt/STSBot/edit/main/LICENSE)
