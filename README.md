# LLM_Slack_ChatBot

![image](https://github.com/wayne540500/LLM_Slack_ChatBot/assets/69573286/a8d70b76-f9f2-4cd8-b6fc-cb601494c290)


Slack Setup

Choose an existing Slack workspace or create a new one.

Go to https://api.slack.com/apps and sign in with your Slack account. 

Click "Create New App" and provide an app name and select your workspace as the development workspace. Click "Create App".

Set up your bot

Under the "Add features and functionality" section, click on "Bots". 

Click "Add a Bot User" and fill in the display name and default username. Save your changes.

Add permissions to your bot

In the left sidebar menu, click on "OAuth & Permissions". 

Scroll down to "Scopes" and add the required bot token scopes. For this example, you'll need at least app_mentions:read, chat:write, and channels:history.

Install the bot to your workspace

In the left sidebar menu to go basic information and click on "Install App". 

Click "Install App to Workspace" and authorize the app.

Retrieve the bot token

After installation, go back to “OAuth & Permissions" page. 

Copy the "Bot User OAuth Access Token" (it starts with xoxb-). You'll need it for your Python script.


Python Setup

pip install slack-sdk slack-bolt Flask

Set the environment variable in the .env file !!!

Create a .env file in your project directory and add the following keys:

![image](https://github.com/wayne540500/LLM_Slack_ChatBot/assets/69573286/e7996bd5-8ec9-439a-b246-3052d7223699)


Run the Python script in the terminal (macOS/Linux) or Command Prompt (Windows): python app.py The server should start, and you'll see output indicating that it's running on http://127.0.0.1:5000/.

![image](https://github.com/wayne540500/LLM_Slack_ChatBot/assets/69573286/09b2b851-c4e2-462e-bb86-fbe67996f433)


Server Setup (Local)

If you haven't installed ngrok, you can download it from https://ngrok.com/download or, on macOS, install it via Homebrew by running: brew install ngrok 

Please Sign in to your ngork account, and go to terminal run: Your Authtoken Authenticate your ngrok agent. You only have to do this once. The Authtoken is saved in the default configuration file.
ngrok config add-authtoken "your authtoken"

In a new terminal (macOS/Linux) or Command Prompt (Windows), start ngrok by running the following command: ngrok http 5000 

Note the HTTPS URL provided by ngrok (e.g., https://yoursubdomain.ngrok.io). You'll need it for the next step.

If you run sucess it will looks like this:
![image](https://github.com/wayne540500/LLM_Slack_ChatBot/assets/69573286/0aa24ab7-3947-4f48-9b83-9b6c756ee60f)



Configure your Slack app with the ngrok URL

Go back to your Slack app settings at https://api.slack.com/apps. 

Click on "Event Subscriptions" in the left sidebar menu.

Enable events and enter your ngrok URL followed by /slack/events (e.g., https://yoursubdomain.ngrok.io/slack/events).

Scroll down to "Subscribe to bot events" and click "Add Bot User Event". Add the app_mention event and save your changes.

Please note that every time you restart ngrok in the terminal, you have to update the URL in Slack — this is just for testing.


Reinstall your Slack app to update the permissions

In the left sidebar menu, click on "Install App". 

Click "Reinstall App to Workspace" and authorize the app.

Add your bot to a Slack channel

Type /invite @bot-name in the channel.




reference: https://docs.datalumina.io/3y3XPD66nBJaub/b/99068549-DC3C-41E3-863E-30F16DBB7A2A/Part-4-%E2%80%94-Add-Custom-Functions

