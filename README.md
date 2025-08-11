# Pokemon Trading Card Game Bot (PTCGPB_HL_v3)

A Node.js-based automation bot for the Pokemon Trading Card Game mobile application. This bot provides automated functionality for account management, friend requests, pack opening, and various game interactions, along with a modern web interface for manual operations.

## 🎯 Features

### Core Functionality
- **Account Management**: Automated login and session management
- **Friend System**: Auto-approve friend requests, manage friend lists
- **Pack Operations**: Automated pack opening with smart healing system
- **Social Features**: Share pack openings, view friend feeds
- **Multi-Account Support**: Manage multiple game accounts simultaneously
- **Web Interface**: Modern Vue.js-based web application for manual operations

### Automation Features
- **Auto Friend Approval**: Automatically accepts incoming friend requests
- **Session Management**: Handles login sessions with automatic renewal
- **Discord Integration**: Webhook notifications for bot activities
- **Error Recovery**: Automatic retry mechanisms with exponential backoff

### Web Interface Features
- **Real-time Operations**: Socket.IO-based real-time communication
- **Account Management**: Switch between multiple game accounts
- **Pack Operations**: Manual pack opening and management
- **Friend Management**: Send, approve, reject friend requests
- **Social Feed**: View and interact with friend activities
- **Deck Management**: View and manage card decks
- **Event Battles**: Participate in special game events

## 🏗️ Project Structure

```
PTCGPB_HL_v3/
├── config/                 # Configuration files
│   ├── main.json          # Main bot configuration
│   ├── main.json.example  # Main bot configuration template
│   ├── server.json        # Server configuration
│   ├── server.json.example # Server configuration template
│   ├── static.json        # Static app configuration
│   ├── pack.json          # Pack configuration
│   └── eventBattle.json   # Event battle configuration
├── lib/                    # Core libraries
│   ├── Grpc.js            # gRPC communication layer
│   ├── client.js          # gRPC client management
│   ├── axiosClient.js     # HTTP client wrapper
│   ├── Units.js           # Utility functions
│   └── packer/            # Data encryption/decryption
├── steps/                  # Game operation modules
│   ├── Login.js           # Authentication
│   ├── SystemClient.js    # System operations
│   ├── PlayerProfileClient.js # Profile management
│   ├── FriendClient.js    # Friend system operations
│   ├── PackClient.js      # Pack management
│   ├── PackShopClient.js  # Shop operations
│   ├── FeedClient.js      # Social feed operations
│   ├── OpenPack.js        # Pack opening logic
│   └── GetJwt.js          # JWT token retrieval
├── server/                 # Server components
│   ├── server.js          # Express + Socket.IO server
│   └── actions.js         # Server-side actions
├── client/                 # Web interface
│   ├── index.html         # Main application entry
│   ├── app.html           # Application interface
│   ├── login.html         # Login page
│   ├── main.js            # Vue.js application
│   ├── api.js             # API client
│   ├── toast.js           # Toast notifications
│   └── stores/            # Pinia state management
├── tester/                 # Interactive testing tool
├── generated/              # Generated files
├── approve.js             # Main automation script
├── start.bat              # Windows startup script
└── package.json           # Dependencies and project info
```

## 🚀 Installation

### Prerequisites
- Node.js 22.2.0 (specified in package.json)
- npm or yarn package manager

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd PTCGPB_HL_v3
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure the bot**
   ```bash
   # Copy configuration templates (if not already present)
   cp config/main.json.example config/main.json
   cp config/server.json.example config/server.json
   ```

4. **Edit configuration files**
   - `config/main.json`: Add your game accounts and Discord webhook
   - `config/server.json`: Configure the JWT server endpoint

## ⚙️ Configuration

### Main Configuration (`config/main.json`)

```json
{
  "deviceAccounts": [
    {
      "id": "your_game_account_id",
      "password": "your_game_password"
    }
  ],
  "reLoginWaitTime": 10,
  "testAccount": {
    "id": "test_account_id",
    "password": "test_account_password"
  },
  "auth": {
    "enable": false,
    "username": "web_username",
    "password": "web_password",
    "secret": "session_secret"
  },
  "webhook": "your_discord_webhook_url"
}
```

### Server Configuration (`config/server.json`)

```json
{
  "server": "https://your-jwt-server.com"
}
```

## 🎮 Usage

### Web Interface (Recommended)

Start the web server and access the modern interface:

```bash
npm run start-server
```

The web interface will automatically open at `http://localhost:9487/`

**Features available in web interface:**
- Account switching and management
- Login/Registration
- Profile management
- Pack opening and management
- Friend request management
- Social feed viewing
- Deck management
- Event battle participation
- Item shop operations

### Interactive Testing Tool

Run the interactive tester for manual operations:

```bash
node tester/tester.js
```

Available operations:
- Account switching
- Login/Registration
- Profile management
- Pack opening
- Friend management
- Social feed viewing

### Automated Bot

Run the main automation script:

```bash
node approve.js
```

The bot will:
1. Automatically log in to configured accounts
2. Monitor and approve friend requests
3. Send notifications to Discord webhook
4. Handle session renewals and error recovery

## 🔧 Key Components

### Web Server
- **Express.js**: HTTP server framework
- **Socket.IO**: Real-time bidirectional communication
- **Session Management**: Optional authentication for web interface
- **Static File Serving**: Vue.js application hosting

### Authentication System
- JWT-based authentication with external server
- Session token management
- Automatic login renewal
- Optional web interface authentication

### gRPC Communication
- Encrypted communication with game servers
- Automatic retry with exponential backoff
- Error handling for various network conditions

### Friend Management
- Automatic friend request approval
- Friend list monitoring
- Request management (send/cancel/reject)

### Pack Operations
- Smart pack opening with healing system
- Transaction tracking
- Card result logging

## 🛡️ Security Features

- Encrypted gRPC communication
- Session token management
- Secure credential storage
- Rate limiting and retry mechanisms
- Optional web interface authentication

## 📊 Monitoring

### Discord Integration
The bot can send notifications to Discord via webhook:
- Login success/failure notifications
- Friend request approvals
- Error alerts

### Logging
- Console-based logging with timestamps
- Error tracking and reporting
- Performance monitoring

## 🔄 Automation Features

### Session Management
- Automatic session renewal every 50 minutes
- Graceful handling of login conflicts
- Error recovery with exponential backoff

### Friend Request Automation
- Continuous monitoring of incoming requests
- Automatic approval with rate limiting
- Conflict detection and resolution

## 🚨 Error Handling

The bot includes comprehensive error handling:
- Network error recovery
- Session conflict resolution
- Rate limit management
- Graceful degradation

## 📝 Dependencies

- `@grpc/grpc-js`: gRPC communication
- `axios`: HTTP client
- `express`: Web server framework
- `express-session`: Session management
- `socket.io`: Real-time communication
- `google-protobuf`: Protocol buffer support
- `inquirer`: Interactive CLI
- `uuid`: Unique identifier generation
- `open`: Auto-open browser

## 🚀 Quick Start

1. **Install dependencies**: `npm install`
2. **Configure accounts**: Edit `config/main.json`
3. **Start web interface**: `npm run start-server`
4. **Access at**: `http://localhost:9487/`

## ⚠️ Disclaimer

This bot is for educational and personal use only. Please ensure compliance with the game's Terms of Service and use responsibly. The developers are not responsible for any account actions taken by game administrators.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the ISC License.

## 🆘 Support

For issues and questions:
1. Check the existing issues
2. Create a new issue with detailed information
3. Include logs and configuration details

---

**Note**: This bot interacts with the Pokemon Trading Card Game mobile application. Use at your own risk and ensure compliance with the game's terms of service. 