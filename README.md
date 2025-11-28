# Telegram Multi-Bot Hosting Platform — One-Click Install/Uninstall

(Automatically runs in the background with auto-start enabled after installation)
Telegram Multi-Bot Hosting Platform — One-Click Install/Uninstall

(Automatically runs in the background with auto-start enabled after installation)
```bash
bash <(curl -Ls https://raw.githubusercontent.com/alexzhang1433/VPS-TGbot/refs/heads/main/setup.sh)
```

> One-click deployment, easily manage multiple Telegram customer-service bots
> Project Operation Center

## 📖 Introduction

This is a complete Telegram bot hosting solution that lets you create and manage multiple customer-service bots through a single management bot. It supports Direct Forwarding mode and Forum Topic Group mode, with a built-in verification system to prevent abuse.

## ✨ Key Features

- 🤖 Multi-Bot Management – Manage unlimited customer-service bots in one platform

- 💬 Two Working Modes – Direct Forwarding / Forum Topic Group

- 🔐 Smart Verification – 5 types of verification codes to prevent spam

- 📣 Custom Welcome Message – Stored in SQLite with automatic backup (New)

- 📊 User Management – View, block, unblock users

- 💾 Data Persistence – SQLite storage with automatic backup

- 🔄 Auto Sync – GitHub auto-backup for data security

- 👥 Admin Features – User list, broadcast, clean invalid bots

- 🚀 Quick Start

The installation script automatically performs:

1.✅ Check/Install Python 3.11+

2.✅ Install required dependencies

3.✅ Create virtual environment

4.✅ Configure systemd service

5.✅ Optional GitHub auto-backup setup

## 📱 Usage Guide
### User Workflow
#### 1️⃣ Add a Bot

1. Send /start to the management bot

2. Tap ➕ Add Bot

3. Enter your Bot Token

4. Select working mode:

   - **Direct Forwarding** — Messages go directly to you

   - **orum Topic Mode** — Messages go to a specific topic in a group

#### 2️⃣ Manage Bots

Tap 🤖 My Bots to:

- 📊 View bot status

- 👥 View verified users

- 🗑️ Delete a bot

- ⚙️ Modify bot configuration

#### 3️⃣ User Management

Inside bot details:

- ✅ View user list

- 🚫 Block user

- 🔄 Unblock user

- ❌ Remove verification

### Working Modes
#### Mode 1: Direct Forwarding (Recommended for beginners)
```
User → Bot → Your private chat
Your private chat → Bot → User
```

**Pros**: Simple and easy, no group configuration
**Best for**: Personal support, small-scale business

#### Mode 2: Forum Topic Group (Recommended for teams)
```
User → Bot → Group Topic
Group Topic → Bot → User
```

**Pros**: Multi-agent collaboration, categorized messages
**Best for**: Teams, larger business operations

**Setup**:

1.Create a group and enable Topics

2.Add your bot as Administrator

3.Set the topic ID inside the management bot

### User Management Commands
| Command|Function|Usage 1: Reply to message|Usage 2: Direct input|Topic Mode| 
|------|------|-------------------|-------------------|-------------------|
|/id	View user| info|Reply + /id|/id 123456789|/id|
|/b or /block|Block user|Reply + /b|/b 123456789|/b|
|/ub or /unblock|Unblock user|Reply + /ub|/ub 123456789|/ub|
|/bl or /blocklist|Show |blacklist	–	/bl	|/bl|
|/uv or /unverify|Remove verification|	Reply + /uv|	/uv 123456789|	/uv|

### Command Examples

**Scenario 1: Block a spammer**
```
User: sends spam
You: [reply to user message] /b
Bot: 🚫 User 123456789 has been blocked
```

**Scenario 2: View user information**
```
You: [reply to user message] /id
Bot: User Info:
     • ID: 123456789
     • Username: @example
     • Name: Example User
     • Verified: ✅ Yes
```

**Scenario 3: Batch management**
```
You: /bl
Bot: 📋 Blacklist:
     1. @user1 (ID: 111111)
     2. @user2 (ID: 222222)

You: /ub 111111
Bot: ✅ User 111111 unblocked
```

## 👑 Admin Features

Admins (configured in ADMIN_CHANNEL) have:

| Feature| 	Icon| 	Description| 	Notes| 
|------|------|------|---------|
| User List	| 👥	| View all users across all bots	Supports|  pagination (15 per page)
| Broadcast	| 📢	| Send announcement to all users	Ideal for|  maintenance or updates
| Clean Invalid Bots| 	🗑️| 	Remove bots with invalid tokens| 	Requires confirmation
## 🔒 Verification System

To prevent abuse, users must pass verification on first use. Five types supported:

|Type|	Icon|	Description|	Example|
|------|------|------|---------|
|Math	|🔢|	Mixed arithmetic|	12 + 5 × 3 = ?
|Number Sequence	|📊|	Arithmetic/geometric/square sequence|	`2, 4, 8, 16, ?`|
|Chinese Q&A	|🇨🇳|	Basic|` Chinese knowledge	Capital of China?`|
|Logic	|🧩|	Simple reasoning|	`If A>B and B>C, then?`|
|Time Q&A	|⏰|	Basic time knowledge|	`How many days in a week?`|

✅ Once verified, users don’t need to verify again.

## 🛠️ Common Commands
### Service Management
|Action	|Command|
|------|------|
|Start|	`systemctl start tg_multi_bot` |
|Stop|	`systemctl stop tg_multi_bot` |
|Restart|	`systemctl restart tg_multi_bot` |
|Status|	`systemctl status tg_multi_bot` |
|Disable auto-start|	`systemctl disable tg_multi_bot` |

## 📂 File Structure
```
/opt/tg_multi_bot/
├── host_bot.py          # Main program
├── database.py          # Database module
├── bot_data.db          # SQLite database
├── .env                 # Environment variables
├── backup.sh            # Backup script
├── venv/                # Python virtual environment
└── backup_temp/         # Temporary backup directory
```

### ❓ FAQ
Q: Invalid Token?

Ensure token is copied correctly

Make sure bot is not deleted or disabled

Regenerate token via @BotFather

### Q: Messages not forwarding?

Direct Mode: Ensure you have sent /start to the bot

Topic Mode: Ensure bot is admin & topic ID is correct

### 📊 System Requirements
|Item	|Requirement|
|------|------|
|OS	Ubuntu| 20.04+ / Debian 10+
|Python|	3.11+|
|RAM|	Minimum 512MB (1GB recommended)|
|Disk| Minimum 1GB free|
|Network	Stable internet connection|

### 🆘 Getting Help

- 📖 See the full documentation (this README)
- 

### 🐛 Report Issues

Please include:

1.Detailed error message

2.Relevant logs

3.Steps to reproduce

### ⚠️ Notes

1.Protect your Bot Token — never share it

2.Backup regularly even though auto-backup exists

3.Be careful when deleting bots — data cannot be restored

4.Follow Telegram usage policies

5.Monitor logs regularly for issues

### 📜 License

MIT License — Free to use with copyright notice.

### 🎯 Version Info

- **Current Version**: v2.0

- **Updated**: 2025-11-18

- **Database**: SQLite 3

- **Python**: 3.11+

**Made with ❤️ for Telegram Bot Lovers**


