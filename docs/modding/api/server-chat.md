Server Chat API
========

Callbacks
---------

The server chat callbacks allow you to intercept incoming chat messages and modify or block them.

### `struct ClServer_MessageStruct { ... }`

Contains details on an incoming chat message. You can receive one of these by adding a chat callback with
[`AddCallback_OnReceivedSayTextMessage`](#void-function-addcallback_onreceivedsaytextmessagecallbackfunc).

**Fields:**
 - `string message` - the text sent by the player.
 - `entity player` - the player who sent the chat.
 - `bool isTeam` - whether this chat is only sent to the player's team.
 - `bool shouldBlock` - if true, this chat will not be sent.

### `void function AddCallback_OnReceivedSayTextMessage(callbackFunc)`

Adds a callback that will be run when a chat message is received from a player. This will not be fired for custom
messages sent by server mods.

The provided function should accept a [`ClServer_MessageStruct`](#struct-clserver_messagestruct---) and return an
optionally modified copy of it. When a chat message is received, each registered callback is run in sequence to modify
or block the message.

**Example:**

```squirrel
ClServer_MessageStruct function MyChatFilter(ClServer_MessageStruct message)
{
    if (message.message.find("nft") != null)
    {
        message.shouldBlock = true
    }
    
    message.message = StringReplace(message.message, "yes", "no", true, true)
    
    return message
}

void function MyModInit()
{
    AddCallback_OnReceivedSayTextMessage(MyChatFilter)
}
```

Custom Messages
---------------

With custom messages you can send chat messages at any time, to all players or to specific players.

### `void function Chat_Impersonate(entity player, string text, bool isTeamChat)`

Displays a chat message as if the player sent it. Only use this when the player has performed a clear action to send a
chat message.

**Parameters:**

 - `entity player` - the player that the chat message will appear to be from.
 - `string text` - the contents of the chat message. Supports [ANSI escape codes](#ansi-escape-codes) for colors.
 - `bool isTeamChat` - whether this chat is only sent to the player's team.

**Example:**

```squirrel
void function OnSayRedCommand(entity player, string text)
{
    Chat_Impersonate(player, "red text -> \x1b[31m" + text)
}
```

### `void function Chat_PrivateMessage(entity fromPlayer, entity toPlayer, string text, bool whisper)`

Sends a private chat message from a player that is only displayed to one other player. Only use this when the player has
performed a clear action to send a chat message.

**Parameters:**

 - `entity fromPlayer` - the player the message will be from.
 - `entity toPlayer` - the player that the message will be shown to.
 - `string text` - the contents of the chat message. Supports [ANSI escape codes](#ansi-escape-codes) for colors.
 - `bool whisper` - if true, `[WHISPER]` will be displayed before the message to indicate the message is private.

**Example:**

```squirrel
void function OnSendToFriendsCommand(entity fromPlayer, string text)
{
    array<entity> friends = GetPlayerFriends(fromPlayer)
    foreach (friend in friends)
    {
        Chat_PrivateMessage(fromPlayer, friend, text, true)
    }
}
```

### `void function Chat_ServerBroadcast(string text)`

Displays a server message to all players in the chat.

**Parameters:**

 - `string text` - the contents of the chat message. Supports [ANSI escape codes](#ansi-escape-codes) for colors.

**Example:**

```squirrel
void function RestartServerThread()
{
    // wait one hour
    wait 3600
    Chat_ServerBroadcast("Server will be shut down in \x1b[93m5 seconds")
    wait 1
    Chat_ServerBroadcast("Server will be shut down in \x1b[93m4 seconds")
    wait 1
    Chat_ServerBroadcast("Server will be shut down in \x1b[93m3 seconds")
    wait 1
    Chat_ServerBroadcast("Server will be shut down in \x1b[93m2 seconds")
    wait 1
    Chat_ServerBroadcast("Server will be shut down in \x1b[93m1 second")
    wait 1
    StopServer()
}
```

### `void function Chat_ServerPrivateMessage(entity toPlayer, string text, bool whisper)`

Sends a server message to a specific player in the chat.

**Parameters:**

 - `entity toPlayer` - the player that the message will be shown to.
 - `string text` - the contents of the chat message. Supports [ANSI escape codes](#ansi-escape-codes) for colors.
 - `bool whisper` - if true, `[WHISPER]` will be displayed before the message to indicate the message is private.

**Example:**

```squirrel
void function OnBanCommand(entity player, array<string> args)
{
    if (!PlayerIsModerator(player))
    {
        Chat_ServerPrivateMessage(player, "You do not have the permissions to perform this command.", true)
        return
    }
    
    BanPlayerByName(args[0])
}
```

ANSI Escape Codes
-----------------

All messages support ANSI escape codes for customising text color. These are commands in strings that have special
meaning. For example, the string:

```
Hello world, \x1b[31mthis text is red\x1b[0m. And \x1b[34mthis text is blue\x1b[0m.
```

`\x1b` is a special character that Squirrel (and other languages) replace with a reserved ASCII character. For future
reference this will be referred to with `ESC` (e.g. setting red text is `ESC[31m`).

The following commands are available:

 - `ESC[0m` and `ESC[39m` - reset text formatting
 - `ESC[30-37m`, `ESC[90-97m` - set to one of [the available color presets](https://en.wikipedia.org/wiki/ANSI_escape_code#3-bit_and_4-bit).
 - `ESC[38;5;Xm` - set to one of [the available 8-bit colors](https://en.wikipedia.org/wiki/ANSI_escape_code#8-bit).
 - `ESC[38;2;R;G;Bm` - set to an RGB color, with `R`, `G` and `B` in the range 0-255.
 - `ESC[110m` - set to chat text color
 - `ESC[111m` - set to friendly player name color
 - `ESC[112m` - set to enemy player name color
 - `ESC[113m` - set to network name color
