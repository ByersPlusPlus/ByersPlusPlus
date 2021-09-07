# ByersPlusPlus

This is the main repository for ByersPlusPlus! Here you can find instructions on how to run your own copy of the popular Homestuck Radio bot called lumiRadio!

**WARNING:** This bot is still in very early development! Everything can change at any time. Please only proceed if you are aware of this! Also, setting this bot up right now is a little tedious. If you aren't knowledgeable about Docker and GCP (Google Cloud Platform), you will probably not be able to set this up.

## Prerequisites

In order to get this bot, you will need the following list of things.
If you cannot do all of these steps, you will not be able to run the bot!

- A clientsecret.json file, which you can obtain by creating a project in the Google Cloud Platform, adding the YouTube Data API to the project, creating credentials for the type "TV" (or similarly named) and then downloading those. **Please be careful not to share this file with anyone, unless you want someone else to generate tokens on your behalf!**
- Docker installed on your machine / server (including docker-compose)
- A reasonable powerful machine to run this on (the project consists of multiple Docker containers running simultaneously)

## Recommended prerequisites

These prerequisites are not mandatory but they are very much recommended:

- 2 YouTube accounts (they can be linked to the same or different Google accounts)
- Some knowledge about gRPC and Rust (for debugging, if needed)

## Setting things up

First you need to clone this repository. After that is done, enter the directory and copy your clientsecrets.json file into the repository (make sure to rename it to clientsecrets.json).

After that is done, you will need to fill a couple of env files:

1. Rename .env.example to .env and fill in a password to use for the database. Make sure this is a secure password!
2. (**Only necessary, if the chat the bot is for is not on your account!**) Create a new .env file called .youtubeservice.env and fill it with the contents below.

### .youtubeservice.env

```.env
YTS_LIVECHAT_ID=[THE LIVECHAT ID OF THE CHAT YOU WANT TO USE THIS BOT ON, PLEASE REPLACE THIS AND THE ANGLED BRACKETS!]
```

## Running the bot

After you set everything up, you can start the bot by running either `docker-compose up` (if you want to manually shut it down with CTRL-C) or `docker-compose up -d` (if you want to shut it down using `docker-compose down`).

As of now, there is no way to determine if the bot is working fine other than checking the logs of the containers (those will be displayed if you ran `docker-compose up` or if you run `docker-compose logs -f` after running `docker-compose up -d`).

**IMPORTANT:** The bot in its current state cannot run for longer than about 3 hours (and some minutes) due to the YouTube API quota limit (which is at 10000 units per day) unless you apply for an extension at Google!

## Contributing

If you want to assist in the development of the bot, please create an issue on the GitHub (a requirement is that you are on the LumiDiscord server, the official lumiRadio Discord) or send me a message.

Please keep in mind, that I cannot share the client secrets of the official bot with anyone except people I trust (like Lumi or Venarion) as the GCP project will most likely get an increased API quota for running the bot 24/7.
