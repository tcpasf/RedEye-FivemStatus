# FiveM Status Discord Bot
*Copyright © 2024 AlphaDev from RedEye Team. All rights reserved.*

A Discord bot built with Discord.js v14 that provides detailed information about FiveM servers using slash commands.

## Features

### `/status` Command
Displays comprehensive information about the FiveM server:
- Server name and connection details with detailed connection instructions
- Server thumbnail and banner images (when available)
- Server description information
- Current player count with visual progress bar
- Game build and version information
- OneSync status and server tags
- Online player list (limited to 15 players)
- Interactive buttons to connect via web and refresh status
- Distinctive red theme for emphasis

### `/players` Command
Shows a detailed list of all players on the server:
- Player IDs and names
- Ping information for each player
- Pagination for servers with many players
- Refresh button to update the player list in real-time
- Preconfigured to connect to the specific server

### `/resources` Command
Lists all resources running on the server:
- Categorized resources with appropriate icons (ESX, QB, vRP, etc.)
- Visual indicators for different resource types
- Pagination for servers with many resources
- Refresh button to update the resource list
- Preconfigured to connect to the specific server

### `/setip` Command
Administrative command to set the server IP (for bot owners):
- Configure which FiveM server the bot connects to
- Updates all commands to use the new server
- Validates that the server is online before saving
- Stores server information for all users

## Setup Instructions

1. **Prerequisites**
   - Node.js 16.9.0 or higher
   - npm (Node Package Manager)
   - A Discord bot token (create one at [Discord Developer Portal](https://discord.com/developers/applications))

2. **Installation**
   ```bash
   # Clone the repository
   git clone https://github.com/tcpasf/RedEye-FivemStatus.git
   cd RedEye-FivemStatus

   # Install dependencies
   npm install
   ```

3. **Configuration**

   **Option 1: Interactive Setup (Recommended)**
   ```bash
   npm run setup
   ```
   This will guide you through the setup process, including:
   - Creating the .env file with your bot token and client ID
   - Installing dependencies
   - Deploying slash commands

   **Option 2: Manual Setup**
   - Copy `.env.example` to `.env`
   - Fill in your Discord bot token and application client ID:
     ```
     TOKEN=your_discord_bot_token_here
     CLIENT_ID=your_discord_application_client_id_here
     ```

4. **Register Slash Commands**

   For global deployment (available in all servers, but can take up to an hour to propagate):
   ```bash
   npm run deploy
   ```

   For testing in a specific server (instant deployment, but only works in that server):
   ```bash
   npm run deploy YOUR_SERVER_ID
   ```
   Replace `YOUR_SERVER_ID` with the ID of your Discord server. You can get this by enabling Developer Mode in Discord settings, then right-clicking on your server and selecting "Copy ID".

5. **Start the Bot**
   ```bash
   npm start
   ```

## Troubleshooting

### "Unknown Application" Error
If you see an error like `DiscordAPIError[10002]: Unknown Application` when deploying commands, it means the CLIENT_ID in your `.env` file is incorrect or doesn't match your bot token.

To fix this:
1. Go to the [Discord Developer Portal](https://discord.com/developers/applications)
2. Select your application
3. Copy the "Application ID" from the General Information tab
4. Make sure this ID matches the CLIENT_ID in your `.env` file
5. Verify that your TOKEN is from the same application (Bot tab)

### Timeout Errors
If you see timeout errors when trying to connect to a FiveM server, it means the server is taking too long to respond. This could be due to:

- The server is under heavy load
- The server has network issues
- The server is starting up
- Your network connection has issues

The bot automatically increases the default timeout from 1 second to 10 seconds to help with this issue. If you still experience timeout errors, you can try:

1. Waiting a few minutes and trying again
2. Checking if the server is listed on the FiveM server list
3. Contacting the server administrator

### URL Protocol Errors
If you see errors related to URL protocols (like `Invalid URL protocol`), it's because Discord only allows certain URL protocols in buttons (`http:`, `https:`, and `discord:`). The bot has been updated to provide connection instructions in the embed instead of using a direct connect button with the `fivem://` protocol.

### Bot Permissions
Make sure your bot has the following permissions when you invite it to your server:
- `bot` scope
- `applications.commands` scope
- `Send Messages` permission
- `Embed Links` permission
- `Use External Emojis` permission (optional, but recommended)

Note: All commands can only be used by users with the Administrator permission in your Discord server. This is a security measure to ensure that only authorized users can access server information.

You can generate an invite link with the correct permissions in the OAuth2 URL Generator in the Discord Developer Portal.

## Usage

Once the bot is running and added to your server, you can use the following slash commands:

- `/status` - Check the status of the FiveM server (admin only)
- `/players` - List all players on the FiveM server (admin only)
- `/resources` - List all resources on the FiveM server (admin only)
- `/setip ip:<server_ip> port:<server_port>` - Configure which FiveM server the bot connects to (admin only)

Notes:
- All commands can only be used by server administrators
- The bot connects to the server configured with the `/setip` command
- If no server has been configured, it defaults to `5.252.103.233:30120`
- Commands are simplified with no parameters needed
- All status information is displayed with a red theme for emphasis

## Credits
This bot was created by AlphaDev from RedEye Team
- GitHub: tcpasf
- Telegram: tcpasf
- Discord: tcpasf

All rights reserved. This project is the intellectual property of AlphaDev from RedEye Team.

## Dependencies

- [discord.js](https://discord.js.org/) (v14.18.0) - Discord API wrapper
- [fivem](https://www.npmjs.com/package/fivem) (v2.1.8) - FiveM server API wrapper
- [dotenv](https://www.npmjs.com/package/dotenv) (v16.4.7) - Environment variable management

## License

Copyright © 2024 AlphaDev from RedEye Team. All rights reserved.

This project is the intellectual property of AlphaDev from RedEye Team. Unauthorized copying, distribution, modification, public display, or public performance of this work is strictly prohibited without express written permission from the author.
