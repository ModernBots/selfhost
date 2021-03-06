## How to self-host any of the ModernBots

# Don't want to deal with all the stuff here?
### We offer self-hosting as a paid service for just **$5/month!** This is far cheaper and easier than most VPS and homelab solutions.

### [Check it out here!](https://about:blank)

---

### Prerequisites
- You have to have a VPS/Homelab/Raspberry Pi.
    - It is ***highly reccomended*** to run a GNU/Linux distrobution. I will not provide any support for non-Linux solutions.
    - If you do not have a VPS, [Ploxhost](https://plox.host/vps-hosting) πΊπΈ, [HostKey](https://hostkey.com/) π³π±, [Vultr](https://www.vultr.com/) π, [Cockbox](https://cockbox.org/) π±πΉ, and [Hetzner](https://www.hetzner.com) π©πͺ are good options.
    - I do not reccomend Raspberry Pis, but if you have one lying around, it's better than nothing.
    - DO NOT use Repl.it or Heroku. They have extremely poor performance, and will probably fail at saving data in the database.
- You have to have (very minimal) CLI and Linux knowledge

### Step 1: Installing dependencies
- Download and install [MongoDB](https://mondodb.com)
- Download and install [Python 3](https://python.org)
     - If you are running GNU/Linux, there's a very good chance Python is pre-installed, so don't worry about this
> At this point in time, it's a good idea to open up the terminal (and `ssh` into your VPS if needed)!
- Clone/download the repo of the bot you want to self host (either [DropBot](https://github.com/modernbots/dropbot), [ModernBot](https://github.com/modernbots/modbot), or [ContentBot](https://github.com/modernbots/contentbot))
     - Many people think this is forking the repo, which isn't. DO NOT fork any of the repositories unless you plan on contributing code!
     - To clone the repository with the CLI, type in `git clone https://github.com/modernbots/BOTNAMEHERE` and hit <kbd>Enter</kbd>, replacing `BOTNAMEHERE` with the name of the bot you want to self-host
- `cd` into directory of the repo you cloned/downloaded
    - I.e. type `cd dropbot` and hit <kbd>Enter</kbd> 
-  Type `python3 -m pip install -r requirements.txt` and hit <kbd>Enter</kbd>

### Step 2: Making the bot with Discord
- Go to the [Discord Developer Portal](https://discord.com/developers)
    - Sometimes it can be buggy and take you to the main Discord webapp. If this happens, just close the site and click the Discord Developer Portal link again.
- Click the "New Application" button in the top-right
- Give it a name (this will be the name of the bot, which you can change later), and click the "Create" button
- (Optional) upload an image into the "APP ICON" section to give the bot a profile picture, and type in a bio into the "DESCRIPTION" section (this will appear in the bot's bio)
- Open the side menu and click on "Bot"
    - You may have to click the button at the top-left with the 3 lines in order to see the sidebar
- Under "Build-A-Bot", click the "Add Bot" button, then click the "Yes, do it!" button
- Turn the "PUBLIC BOT" switch **OFF**
> If you are self-hosting ModBot, scroll down to Privileged Gateway Intents and turn **ON** "SERVER MEMBERS INTENT".
- Under "TOKEN", click the "Copy" button
> NEVER give this token to anyone else!

### Step 3: Setting the bot up
- Back in the terminal, type `echo "DISCORD=`, paste the token you copied, `" > .env` and hit <kbd>Enter</kbd>
    - It should look like `echo "DISCORD=abcdefg" > .env`
- Type `sed -i 's/"info", "tasks"]/]/ ./src/bot.py` and hit <kbd>Enter</kbd>
- Type `python3 src/bot.py` and hit <kbd>Enter</kbd>
> To have the bot still running when you close the session, install **and** run `tmux` before running this command!

### Step 4: Inviting the bot
- Go back to the [Discord Developer Portal](https://discord.com/developers) and open the app you created
- Open the sidebar and click on "Oauth2", then click on "URL Generator"
- Under "SCOPES", check the "bot" **AND** the "applications.commands" boxes
- Under "GENERAL PERMISSIONS", check the "Administrator" box
- Copy the URL at the bottom and open it in a new tab
- Select your server from the dropdown, click the "Continue" button, click the "Authorize" button, and fill out the hCaptcha if needed

# **Congrats!** The bot is now in your server!
