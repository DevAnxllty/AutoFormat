# AutoFormat
You need to add the script into your game, https://www.roblox.com/library/13737311032/AutoFormat

I made this using gsub & patterns

# Types of Formatting

| Character | Type | Preview |
| ------------- | ------------- | ------------- |
| #  | Bold  | **Hello World!** |
| *  | Italic  | *Hello World!* |
| ~  | Strike Through | ~~Hello World!~~ |
| _  | Underline | <ins>Hello World!</ins> |

> You need to wrap the character around the text.

# Filtering
If you want to add a filtering system you need your code to look something like this,

```lua
local TextService = game:GetService("TextService")
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	local function FormatText(text)
		-- Strikethrough formatting
		text = text:gsub("~(.-)~", "<s>%1</s>")

		-- Italic formatting with underscore
		text = text:gsub("*(.-)*", "<i>%1</i>")

		-- Bold formatting
		text = text:gsub("#(.-)#", "<b>%1</b>")
		
		--Underline formatting
		text = text:gsub("_(.-)_", "<u>%1</u>")

		-- Filterer		
		text = TextService:FilterStringAsync(text, player.UserId):GetChatForUserAsync(player.UserId)

		return text
	end

	local text = FormatText("_~*#Hello World!#*~_")
	print(text)
end)
```
