<h1 align="center">
  ⭐ The Ultimate Roblox Sprint System (R.S.S) ⭐
</h1>

<p align="center">
  An advanced, fully modular Roblox Sprinting System (R.S.S) with easy to use API calls.
</p>

> [!CAUTION]
> This project is in early **BETA** so remember to report any issues to the [Issues Tab](https://github.com/FreelessUnlimited/RSS/issues)!
> Also you can find the latest version in [**Releases**](https://github.com/FreelessUnlimited/RSS/releases/tag/Release)
> 
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
- Compatibility with **R6** & **R15**
- Multi-Keybind support
  
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
> So going into the script and editing isn't as need as in other scripts & systems similar to this.

| Config Name          | How To Use                                                                                   | Example                                                        |
|----------------------|----------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| Walk Speed           | You use this to change the players **Default Walk Speed**                                    | **16** or **24** |
| Run Speed            | You use this to change the players **Sprint Speed**                                          | **24** or **32**   |
| AnimationID          | You use this to change the **animation** that plays when the player sprints.                 | **rbxassetid://0** |

> [!NOTE]
> You can do multiple things to disable the animation!
> One of them is to simple leave it blank. Another is the type in the number '0'
> This is because the script has a few of these presets inorder for you to disable the animation!
> Animation also works with R6 & R15 as long as you have the animation for it of course!

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
