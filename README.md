**Mirror Bot** is a _multipurpose_ Telegram Bot written in Python for mirroring files on the Internet to Google Drive. Based on [python-aria-mirror-bot](https://github.com/lzzy12/python-aria-mirror-bot)

# How to deploy?
Deploying is pretty much simple and is divided into several steps as follows:

## Installing requirements

- Clone this repo:
```
git clone https://github.com/ayush-rathore/mirror-bot
cd mirror-bot
```

- Install dependencies for running setup scripts:
```
pip3 install -r requirements-cli.txt
```

## Setting up config file
```
cp config_sample.env config.env
```
Fill up rest of the fields. Meaning of each field is discussed below:

### Required Field
- `BOT_TOKEN`: Telegram Bot Token from [@BotFather](https://t.me/BotFather)
- `TELEGRAM_API`: https://my.telegram.org.
- `TELEGRAM_HASH`: https://my.telegram.org
- `OWNER_ID`: Telegram User ID
- `GDRIVE_FOLDER_ID`: Folder ID of the Google Drive Folder

### Optional Field
- `TOKEN_PICKLE_URL`
- `AUTHORIZED_CHATS`
- `IS_TEAM_DRIVE`
- `INDEX_URL`
- `AS_DOCUMENT`

## Bot commands to be set in [@BotFather](https://t.me/BotFather)
- `mirror` (Use qb for QBittorrent)
- `leech`
- `clone`
- `cancel`
- `stats`

## Generating Token.pickle
```
pip3 install google-api-python-client google-auth-httplib2 google-auth-oauthlib
python3 generate_drive_token.py
```

## Deploying On VPS

- Start Docker daemon:
```
sudo dockerd
```
- Build Docker image:
```
sudo docker build . -t mirror-bot
```
- Run the image:
```
sudo docker run mirror-bot
```

## Deploying on Heroku
Set the following Environment Secrets for the Repo and run the workflow from actions tab.
- `HEROKU_EMAIL`
- `HEROKU_API_KEY`
- `HEROKU_APP_NAME`
- `CONFIG_FILE_URL`
- `TOKEN_PICKLE_URL`
