<p align="center"><a href="https://anuraghazra.github.io"><img width="60%" src="./bannar.png" /></a></p>

A super advanced, fully modular roblox sprinting system with PublicAPI calls.

> [!CAUTION]
> This project is in early **BETA** so remember to report any issues!
> Also you can find the latest version in [**Releases**](https://github.com/FreelessUnlimited/RSS/releases)

---

## Table of Content

- [Features](#features)  
- [Installation](#installation)  
- [Configuration](#configuration)  
- [How To Use](#how-to-use)  
- [Public API](#public-api)  
- [Examples](#examples)  
- [License](#license)  

---

## Features

- Client-side, Server-side, and Hybrid authority support  
- Optional sprint animation support  
- Keyboard and controller input support  
- Live runtime configuration changes  
- Full external API for other scripts (speed override, forced sprint, multipliers)  
- Safe, modular, and production-ready  

---

## Installation
1. Download **RSS.rbxm**
2. Open **Roblox Studio** then click on **File** then **Import Roblox Model** then select the **RSS.rbxm** file then press Enter and It's In!
3. Add `SprintModule` to the following Directory in your game:

```
StarterPlayer
└─ StarterPlayerScripts
```
4. Require and instantiate the module in a controller LocalScript when the player’s character loads:

```lua
local SprintModule = require(script.SprintModule)
local sprint = SprintModule.new(player.Character)
```

---

## Configuration
> [!NOTE]
> All default configuration is in the 'SprintModule.lua'
> So going into the script and editing is not really needed.
> Also remember if any issues show, make a post in [**Issues**](https://github.com/FreelessUnlimited/RSS/issues)

- **Client** → Cosmetic only  
- **Server** → Authoritative speed control  
- **Hybrid** → Client requests, server applies  

---

## How To Use

### Creating a Sprint Instance

```lua
local SprintModule = require(path.to.SprintModule)
local sprint = SprintModule.new(character)
```

### Starting or Stopping Sprint

```lua
sprint:Start()
sprint:Stop()
```

### Force Sprint or Apply Effects

```lua
sprint:SetForcedSprint(true)
sprint:SetSpeedMultiplier(0.5)
```

### Restore Default Movement

```lua
sprint:ClearSpeedOverride()
sprint:ResetSpeedMultiplier()
sprint:SetForcedSprint(false)
```

### Authority Mode

```lua
SprintModule.Authority = "Client" -- Client | Server | Hybrid
```

You can find what **Authority** does in the [Configuration Section](#configuration)

### Animation Support

Leave `AnimationID` empty to disable animations.
And to change during runtime:

```lua
sprint:SetAnimation("rbxassetid://YOUR_ANIMATION_ID")
```

---

## Public API

### Queries

```lua
sprint:IsSprinting()        -- Returns boolean
sprint:GetCurrentSpeed()    -- Returns current humanoid WalkSpeed
```

### Sprint Control

```lua
sprint:Start()
sprint:Stop()
sprint:SetForcedSprint(boolean)
```

### Speed Control

```lua
sprint:SetWalkSpeed(number)
sprint:SetSprintSpeed(number)

sprint:SetSpeedOverride(number)
sprint:ClearSpeedOverride()

sprint:SetSpeedMultiplier(number)
sprint:ResetSpeedMultiplier()
```

### Animation Control

```lua
sprint:SetAnimation("rbxassetid://123456789")
```

### Lifecycle

```lua
sprint:Destroy()
```

---

## Examples

### Slowing Player Down (Debuff)

```lua
sprint:SetSpeedMultiplier(0.4)
```

### Require Sprint (Cutscene / Chase)

```lua
sprint:SetForcedSprint(true)
```

### Stun Player

```lua
sprint:SetSpeedOverride(0)
```

### Restore Normal Movement

```lua
sprint:ClearSpeedOverride()
sprint:ResetSpeedMultiplier()
sprint:SetForcedSprint(false)
```
