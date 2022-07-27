# Server online-status check with reporting to telegram

This simple script uses `netcat` to check if - for instance - a webserver is running on a server. If the service is not running, it utilizes the telegram bot API for sending a message to inform the operator of the server.  

## How to
### 1. Register the bot
Go to the [BotFather](https://t.me/botfather) bot-account and create a bot by writing `/newbot`. Then, copy the token.

### 2. Find your chat-id
Send a message to you newly created bot *(you can find the link to your bot in the success message sent by BotFather)*.  

Visit `https://api.telegram.org/bot{token}/getUpdates` to get your chat id: `result => 0 => message => chat => id`  
Please note that the token must be directly behind `bot` in the URL. If your token starts with `AAAA` the URL looks like `/botAAAA` and so on.  

### 3. Configure the script
Fill in the four variables `server`, `port` (SSL is on 443 by default), `botToken` and `chatId`.

### 4. Make the script executable
Execute `chmod +x serverOnline.sh` to make the script executable.

### 5. Test the script
To test the script, enter an unused port and execute it via `./serverOnline.sh`. Don't forget to change the port number after testing.

### 6. Cron
Use `crontab -e` to append the following line to the cronjob list:  
`* * * * * /path/to/serverOnline.sh`  
Make sure you leave an empty line at the end of the file!

## That's it!

<sub>And to make it absolutely and undoubtedly clear:<br>
The script is supposed to be run on a different server, than the server being checked.</sub>
