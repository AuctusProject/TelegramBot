Forked from OriginProtocol and added few modifications. 

# Telegram Bot

- Deletes messages matching specified patterns
- Bans users for posting messagses matching specified patterns
- Bans users with usernames matching specified patterns
- Records logs of converstations

## Installation

 - Required: Python 3.x, pip, PostgreSQL
 - Create virtualenv
 - Clone this repo
 - `pip install --upgrade -r requirements.txt`

## Setup

 - Create a Telegram bot by talking to `@BotFather` : https://core.telegram.org/bots#creating-a-new-bot
 - Use `/setprivacy` with `@BotFather` in order to allow it to see all messages in a group.
 - Save your Telegram Bot Token to be used further.
 - Create your Telegram group.
 - Add your bot to the group like so: https://stackoverflow.com/questions/37338101/how-to-add-a-bot-to-a-telegram-group
 - Make your bot an admin in the group

## Variables JSON setup

 - Create a json named variables.json in current folder. The code should follow this template:
 
 ```
 {
"TELEGRAM_BOT_POSTGRES_URL": "postgresql://<user>:<pw>@localhost/<database>",
	"TELEGRAM_BOT_TOKEN":"<tokenCode>",
	"SAFE_USER_IDS":"list of trusted ids, comma separated",
	"MESSAGE_HIDE_PATTERNS":|[0-9a-fA-Z]{34,34},
	"MESSAGE_BAN_PATTERNS":"",
	"NAME_BAN_PATTERNS":""
}

 ``` 
 - Regex patterns will be read from the following env variables
	- `MESSAGE_BAN_PATTERNS` Messages matching this will ban the user.
	- `MESSAGE_HIDE_PATTERNS` Messages matching this will be hidden/deleted
	- `NAME_BAN_PATTERNS` Users with usernames or first/last names maching this will be banned from the group.
	- `SAFE_USER_IDS` User ID's that are except from these checkes. Note that the bot cannot ban admin users, but can delete their messages.

## Database setup

 - Run: `python model.py` to setup the DB tables.

## Running

### Locally
 - Run: `python bot.py` to start logger
 - Messages will be displayed on `stdout` as they are logged.

### On Heroku
 - You must enable the worker on Heroku app dashboard. (By default it is off.)
