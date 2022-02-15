Client chat API
===============

Callbacks
---------

The client chat callbacks allow you to intercept chat messages and modify or block them.


### `struct ClClient_MessageStruct { ... }`

Contains details on a chat message to be displayed. You can receive one of these by adding a chat callback with
[`AddCallback_OnReceivedSayTextMessage`](#void-function-addcallback_onreceivedsaytextmessagecallbackfunc).

**Fields:**

 - `string message` - the text sent by the player.
 - `entity player` - the player who sent the chat.
 - `bool isTeam` - whether this chat has a `[TEAM]` tag.
 - `bool isDead` - whether this chat has a `[DEAD]` tag.
 - `bool isWhisper` - whether this chat has a `[WHISPER]` tag.
 - `bool shouldBlock` - if true, this chat will not be displayed.

#### `void function AddCallback_OnReceivedSayTextMessage(callbackFunc)`

Adds a callback that will be run when a chat message is received from the server. This will only be triggered for
messages from players, not server messages.

The provided function should accept a [`ClClient_MessageStruct`](#struct-clclient_messagestruct---) and return an optionally modified copy of it. When a
chat message is received, each registered callback is run in sequence to modify or block the message.

**Example:**

```squirrel
ClClient_MessageStruct function MyChatFilter(ClClient_MessageStruct message)
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

Writing to Chat
---------------

A handful of functions are provided to write messages in local chat windows. These do not send messages to other
players, they only display them locally.

### `void function Chat_GameWriteLine(string text)`

Writes a line of text in local game chat panels. Supports [ANSI escape codes](client-chat.md#ansi-escape-codes).

**Example:**

```squirrel
void function OnGameStarted()
{
    Chat_GameWriteLine("You got this, " + GetLocalClientPlayer().GetPlayerName() + "!")
}
```

### `void function Chat_GameWrite(string text)`

Appends text to local game chat panels. Supports [ANSI escape codes](client-chat.md#ansi-escape-codes).

**Example:**
```squirrel
void function InitialiseHEVSuit()
{
    Chat_GameWriteLine("SENSOR ARRAYS-")
    ActivateSensorArrays()
    Chat_GameWrite("ACTIVATED")
    wait 1
    Chat_GameWriteLine("BIOMETRIC MONITORING SYSTEMS-")
    ActivateBiometricMonitoringSystems()
    Chat_GameWrite("ACTIVATED")
    wait 1
    Chat_GameWriteLine("HAVE A VERY SAFE DAY.")
}
```

### `void function Chat_NetworkWriteLine(string text)`

Writes a line of text in local network chat panels. Supports [ANSI escape codes](client-chat.md#ansi-escape-codes).

**Example:**

```squirrel
void function MyModInit()
{
    Chat_NetworkWriteLine("MyMod v1.0.0 is good to go!")
}
```

### `void function Chat_NetworkWrite(string text)`

Appends text to local network chat panels. Supports [ANSI escape codes](client-chat.md#ansi-escape-codes).

**Example:**

```squirrel
void function OnButtonPressed()
{
    Chat_NetworkWrite("Connecting in 3...")
    wait 1
    Chat_NetworkWrite("2...")
    wait 1
    Chat_NetworkWrite("1...")
    wait 1
    Chat_NetworkWrite("0")
    Connect()
}
```
