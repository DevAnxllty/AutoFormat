# AutoFormat
You need to add the model into your game, https://www.roblox.com/library/13737311032/AutoFormat

If you want to add a filtering system you need to change your code to,

```lua
local TextService = game:GetService("TextService")
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	local function FormatText(text)
		-- Strikethrough formatting
		text = text:gsub("~(.-)~", "<s>%1</s>")

		-- Italic formatting with underscore
		text = text:gsub("*(.-)*", "<i>%1</i>")

		-- Bold formatting with pound/hashtag symbol
		text = text:gsub("#(.-)#", "<b>%1</b>")

		text = TextService:FilterStringAsync(text, player.UserId):GetChatForUserAsync(player.UserId)

		return text
	end

	local text = FormatText("~*#Hello World!#*~")
	print(text) -- Since this is a print, it won't format it

	-- If you use a text label with Rich Text on, then it will format
end)
```
