(documentation/purposal for advance and powerful discord bot, contant @ykblmao on discord for purchase)

# FiveM Discord Bot

A advance & powerful Discord bot for managing FiveM servers with QBCore and txAdmin integration. This bot provides comprehensive server management capabilities through Discord slash commands, with a focus on security, stability, and ease of use.

## Key Features

### Server Management
- Start, stop, and restart server controls
- Resource management and monitoring
- Automated backups and maintenance
- Server status and analytics tracking

### Player Administration
- Comprehensive player control commands
- Advanced moderation tools with validation
- Detailed player information tracking
- Economy and inventory management

### Security & Protection
- Server security and DDoS protection
- IP banning and filtering
- Rate limiting on sensitive commands
- Input validation and sanitization

### Integrations & Logging
- Full QBCore Framework integration
- txAdmin API compatibility
- Comprehensive webhook logging
- Audit trails for all actions

### Quality of Life
- Discord moderation features
- Server announcements
- Vehicle management system
- Property and business controls

Each feature includes:
- Success/failure tracking
- Detailed execution logs
- Error monitoring
- Permission controls

## Requirements

- Node.js 16.9.0 or higher
- Discord Bot Token
- FiveM Server with txAdmin
- QBCore Framework


## Command Documentation

This section provides detailed documentation for all available commands. Each command is marked with its required permission level and includes syntax, examples, and notes about usage.

- (Admin) - Requires administrator permissions
- (Mod) - Can be used by moderators and administrators
- No marking - Available to all staff members

### Player Management Commands

#### Player Control (/control) - Admin Only
Advanced player control commands for server administrators.

| Command | Description | Example | Notes |
|---------|-------------|---------|-------|
| `/control freeze <player> <true\|false>` | Freeze/unfreeze a player | `/control freeze 123 true` | Rate limited |
| `/control heal <player> [armor]` | Heal player and restore armor | `/control heal 123 true` | Uses QBCore functions |
| `/control screenshot <player>` | Take screenshot of player's game | `/control screenshot 123` | Uses txAdmin API |
| `/control weapons <player> removeall` | Remove all weapons | `/control weapons 123 removeall` | Server-side validation |
| `/control addmoney <player> <cash\|bank> <amount>` | Give money to player | `/control addmoney 123 bank 5000` | Transaction logged |
| `/control setjob <player> <job> <grade>` | Set player's job and grade | `/control setjob 123 police 2` | Uses QBCore job system |
| `/control gang <player> <gang> <grade>` | Set player's gang and grade | `/control gang 123 ballas 2` | Database integrated |
| `/control noclip <player>` | Toggle noclip mode | `/control noclip 123` | Movement cheats monitored |
| `/control godmode <player>` | Toggle god mode | `/control godmode 123` | Abuse logged |
| `/control invisible <player>` | Toggle invisibility | `/control invisible 123` | Visual only |
| `/control stamina <player> <level>` | Set stamina (0-100) | `/control stamina 123 100` | Affects movement speed |

### Vehicle Management Commands

#### Basic Vehicle Commands
| Command | Permission | Description | Example | Notes |
|---------|------------|-------------|---------|-------|
| `/spawnvehicle <playerid> <vehicle> [temporary]` | Mod | Spawn a vehicle for player | `/spawnvehicle 123 adder true` | Optional temporary flag |
| `/fixvehicle <playerid>` | Mod | Repair player's current vehicle | `/fixvehicle 123` | Full repair and cleanup |

#### Vehicle Control (/vehiclecontrol) - Admin Only
Advanced vehicle modification and tuning commands.

| Command | Description | Example | Parameters |
|---------|-------------|---------|------------|
| `/vehiclecontrol tune <player> <part> <level>` | Apply performance tuning | `/vehiclecontrol tune 123 engine 4` | Parts: engine, brakes, transmission, suspension, turbo<br>Levels: 0-5 |
| `/vehiclecontrol color <player> <primary> <secondary>` | Change vehicle colors | `/vehiclecontrol color 123 0 0` | RGB values |
| `/vehiclecontrol plate <player> <text>` | Change license plate | `/vehiclecontrol plate 123 FIVEM` | Max 8 characters |
| `/vehiclecontrol fuel <player> <amount>` | Set fuel level | `/vehiclecontrol fuel 123 100` | Range: 0-100 |

#### Garage Management (/garage) - Admin Only
Advanced vehicle ownership and tracking system.

| Command | Description | Example | Notes |
|---------|-------------|---------|-------|
| `/garage list <player>` | List owned vehicles | `/garage list 123` | Shows all vehicles |
| `/garage remove <player> <plate>` | Remove vehicle | `/garage remove 123 ABC123` | Deletes from database |
| `/garage transfer <from> <to> <plate>` | Transfer ownership | `/garage transfer 123 456 ABC123` | Updates ownership |
| `/garage locate <plate>` | Find vehicle location | `/garage locate ABC123` | Shows coordinates |

### Economy Management Commands

#### Business Management (/business) - Admin Only
Comprehensive business management system integrated with QBCore economy.

| Command | Description | Example | Options |
|---------|-------------|---------|----------|
| `/business info <business>` | View business details | `/business info mechanic` | Shows finances, employees, stats |
| `/business employees <business> <action> [player]` | Manage employees | `/business employees mechanic add 123` | Actions:<br>• list - Show all employees<br>• add - Add new employee<br>• remove - Remove employee<br>• promote/demote - Change rank |
| `/business funds <business> <action> [amount]` | Manage business funds | `/business funds mechanic deposit 5000` | Actions:<br>• balance - Check balance<br>• deposit - Add funds<br>• withdraw - Remove funds |

#### Property Management (/property) - Admin Only  
Real estate and property control system.

| Command | Description | Example | Notes |
|---------|-------------|---------|-------|
| `/property list [player]` | List properties | `/property list 123` | Optional player filter |
| `/property assign <property> <player>` | Set ownership | `/property assign house1 123` | Handles deed transfer |
| `/property remove <property>` | Remove ownership | `/property remove house1` | Returns to market |
| `/property access <property> <action> [player]` | Control access | `/property access house1 addaccess 123` | Actions:<br>• lock/unlock - Security<br>• addaccess/removeaccess - Keys |

### Server Management Commands

#### Analytics (/analytics) - Admin Only
Comprehensive server monitoring and statistics system.

| Command | Description | Example | Details |
|---------|-------------|---------|---------|
| `/analytics resources <type>` | Resource usage stats | `/analytics resources cpu` | Types:<br>• cpu - Processor usage<br>• memory - RAM usage<br>• network - Bandwidth stats |
| `/analytics players <timeframe>` | Player activity stats | `/analytics players daily` | Timeframes:<br>• daily - 24h stats<br>• weekly - 7 day overview<br>• monthly - 30 day trends |
| `/analytics economy <type>` | Economic analytics | `/analytics economy money` | Types:<br>• money - Cash flow<br>• items - Trading activity<br>• business - Company stats |
| `/analytics activity <category> <hours>` | Server activity logs | `/analytics activity commands 24` | Categories:<br>• commands - Usage stats<br>• moderation - Admin actions<br>• errors - System issues<br>Hours: 1-72 |

#### Utility Commands (/utility) - Admin Only
Server maintenance and system management tools.

| Command | Description | Example | Notes |
|---------|-------------|---------|-------|
| **Data Refresh** |
| `/utility refreshitems` | Update item data | - | Refreshes all item metadata |
| `/utility refreshjobs` | Update job data | - | Syncs job information |
| `/utility refreshgangs` | Update gang data | - | Refreshes gang details |
| `/utility reloadinventory` | Reload inventory | - | Updates inventory system |
| `/utility refreshperms` | Update permissions | - | Syncs permission data |
| `/utility refreshphones` | Update phone system | - | Reloads phone data |
| `/utility refreshstashes` | Update stash locations | - | Syncs storage points |
| `/utility reloadconfig` | Reload configuration | - | Updates server config |
| **World Management** |
| `/utility coords <location>` | Get coordinates | `/utility coords legion` | Common locations mapped |
| `/utility cleararea <radius> <location>` | Clear area | `/utility cleararea 50 legion` | Removes entities |
| `/utility repairvehicles <radius> <location>` | Area vehicle repair | `/utility repairvehicles 50 legion` | Mass vehicle fix |
| `/utility savecar <player>` | Save vehicle | `/utility savecar 123` | Persists to database |

### Server Administration Commands

#### Moderation Commands
Core server moderation tools with logging.

| Command | Permission | Description | Example | Notes |
|---------|------------|-------------|---------|-------|
| `/kick <playerid> <reason>` | Mod | Remove player from server | `/kick 123 "Breaking rules"` | Immediate effect |
| `/ban <playerid> <duration> <reason>` | Admin | Ban player with duration | `/ban 123 7d "Cheating"` | Durations: 1h, 1d, 7d, permanent |
| `/warn <playerid> <reason>` | Mod | Issue warning to player | `/warn 123 "Language warning"` | Tracked in database |
| `/checkban <identifier>` | Mod | Check ban status | `/checkban steam:123456` | Shows ban history |
| `/unban <identifier>` | Admin | Remove ban | `/unban steam:123456` | Requires reason |
| `/ipban <ip> <reason> [duration]` | Admin | Ban IP address | `/ipban 1.2.3.4 "DDoS" 30d` | Network-level |

#### World Control Commands
Environment and world state management.

| Command | Permission | Description | Example | Options |
|---------|------------|-------------|---------|---------|
| `/settime <hour> <minute> [freeze]` | Mod | Set server time | `/settime 12 0 true` | 24-hour format<br>Optional time freeze |
| `/setweather <type>` | Mod | Change weather | `/setweather CLEAR` | Types: CLEAR, RAIN, THUNDER, FOGGY, OVERCAST, CLOUDS |

#### Teleport Commands - Admin Only
Advanced player positioning system.

| Command | Description | Example | Notes |
|---------|-------------|---------|-------|
| `/teleport toplayer <source> <target>` | Move player to player | `/teleport toplayer 123 456` | Permission checked |
| `/teleport tocoords <player> <x> <y> <z>` | Move to coordinates | `/teleport tocoords 123 100 200 300` | Safe landing |
| `/teleportall <location>` | Mass teleport | `/teleportall legion` | Preset locations:<br>• legion<br>• airport<br>• pd<br>• hospital |

### Discord Management Commands

#### User Management
Core Discord user moderation tools.

| Command | Permission | Description | Example | Notes |
|---------|------------|-------------|---------|-------|
| `/timeout <user> <duration> <reason>` | Mod | Temporary timeout | `/timeout @user 1h "Spam"` | Max 28 days |
| `/mute <user> <reason>` | Mod | Permanent mute | `/mute @user "Inappropriate behavior"` | All channels |
| `/unmute <user> <reason>` | Mod | Remove mute | `/unmute @user "Time served"` | Requires reason |
| `/discordkick <user> <reason>` | Mod | Remove from server | `/discordkick @user "Breaking rules"` | Can rejoin |
| `/discordban <user> <reason> [days] [permanent]` | Admin | Ban from server | `/discordban @user "Severe violation" 7 true` | Optional message deletion |
| `/discordunban <userid> <reason>` | Admin | Remove ban | `/discordunban 123456789 "Appeal accepted"` | Uses user ID |

#### Role Management
User role and permission controls.

| Command | Permission | Description | Example | Notes |
|---------|------------|-------------|---------|-------|
| `/addrole <user> <role> <reason>` | Mod | Add role to user | `/addrole @user @VIP "Donation"` | Permission checked |
| `/removerole <user> <role> <reason>` | Mod | Remove role | `/removerole @user @VIP "Expired"` | Logs change |

#### Channel Management
Channel control and moderation tools.

| Command | Permission | Description | Example | Notes |
|---------|------------|-------------|---------|-------|
| `/lock <reason>` | Mod | Lock channel | `/lock "Maintenance"` | Prevents messages |
| `/unlock <reason>` | Mod | Unlock channel | `/unlock "Maintenance complete"` | Restores access |
| `/slowmode <seconds> <reason>` | Mod | Set message delay | `/slowmode 10 "High traffic"` | 0-21600 seconds |
| `/purge <amount> [user]` | Mod | Delete messages | `/purge 50 @user` | Max 100 messages |

#### Information Commands
User and server information tools.

| Command | Permission | Description | Example | Details Shown |
|---------|------------|-------------|---------|---------------|
| `/userinfo [user]` | Mod | Show user details | `/userinfo @user` | • Join date<br>• Roles<br>• Status<br>• Account age |

### System Status Commands

#### Server Monitoring
Server state and configuration commands.

| Command | Permission | Description | Example | Details Shown |
|---------|------------|-------------|---------|---------------|
| `/status` | Mod | Server status check | `/status` | • Player count<br>• Resource usage<br>• Uptime<br>• Queue info |
| `/botstatus <status> <type>` | Admin | Set bot status | `/botstatus "Playing FiveM" "PLAYING"` | Types:<br>• PLAYING<br>• WATCHING<br>• LISTENING<br>• COMPETING |

#### Announcements
Server-wide communication tools.

| Command | Permission | Description | Example | Options |
|---------|------------|-------------|---------|---------|
| `/announce <message> [ingame]` | Mod | Send announcement | `/announce "Server restart in 5 min" true` | Optional in-game broadcast |

## Statistics

- **Total Commands**: 90 unique commands
  - 48 main slash commands
  - 42 subcommands across 8 main commands
  - Categories:
    - Player Management (control, setjob, etc.)
    - Server Administration (manage, utility, analytics, etc.) 
    - Vehicle System (vehiclecontrol, fixvehicle, etc.)
    - Economy Features (business, property, etc.)
    - Moderation Tools (ban, kick, warn, etc.)
    - Discord Integration (mute, roles, etc.)

- **Utility Functions**: ~30 internal functions
  - Permission Management
  - Command Validation
  - Logging & Monitoring
  - API Integration
  - Data Management
  - Error Handling

- **Environment Variables**: 8 required variables
  - Bot Configuration (2)
  - Server Integration (2)
  - Channel Settings (2)
  - Role Management (2)

## Additional Features

### Security System

#### DDoS Protection
The bot includes an advanced DDoS detection and prevention system:

- Real-time metrics monitoring
- Network traffic analysis
- Suspicious connection detection
- Threat level assessment (Low, Medium, High)
- Automatic mitigation responses
- Detailed incident logging
- IP blocking capabilities

### Command Handling Features

- Rate limiting on sensitive commands
- Input validation and sanitization
- Success/failure tracking
- Detailed execution logs
- Error monitoring and reporting
- Permission level enforcement
- Command cooldowns
- User preference tracking

### Integration Features

- Full QBCore Framework compatibility
- txAdmin API integration
- Discord webhook logging
- Database synchronization
- Real-time server monitoring
- Cross-platform notifications
- Automated backups

### Advanced Bot Features

#### Monitoring Systems
- Health and status monitoring
- Resource usage monitoring
- Network traffic monitoring
- Error rate monitoring
- Command usage analytics
- Performance metrics tracking

#### Administration Tools
- Advanced command rate limiting
- Intelligent spam prevention
- Permission level management
- Audit trail generation
- Backup scheduling
- Configuration management

#### Security Features
- DDoS attack detection
- IP blocking and filtering
- Suspicious activity monitoring
- Connection tracking
- User permission validation
- Resource access control

### Support

If you need help with the bot:

1. Check the documentation thoroughly
2. Look for similar issues in the issue tracker
3. Contact the maintainers through Discord
4. Create a new issue with details about your problem


### Development

#### Technology Stack
- Node.js 16.9.0+
- Discord.js v14
- QBCore Framework
- txAdmin API
- SQLite/MySQL Database


### Documentation

Detailed documentation is available for various aspects of the bot:

#### Command Documentation
- See above sections for detailed command syntax and usage
- Each command includes permission requirements and examples
- Full parameter documentation with validation rules

#### Setup Instructions
- Basic installation steps in Requirements section
- Advanced configuration options in Configuration section
- Development setup guide in Development section

#### API Integration
- QBCore Framework integration details
- txAdmin API usage and endpoints
- Discord API features and limitations


## Support and Community

### Getting Help
If you need assistance with the bot:

1. Read the documentation thoroughly
2. Check existing issues directly from us
3. Join our Discord community
4. Open a new ticket with details

### Security
Report security vulnerabilities responsibly:

1. Do not disclose publicly
2. Create ticket in our discord server
3. Allow time for patches
4. Disclose responsibly


---
© 2025 AutomateX Studio. All rights reserved.


