**Door Documentation**

**Spawning Items**

require(game.ServerStorage.Modules.Assets):GetItem("item"):Clone().Parent = workspace.Player

**Exobyte pls give documentation for following**

- Spawning in Player
- Spawning Entities
- Adding Interactions to an object (Click and Gold purchase)
- Allowing Player to jump in following room
- Notification
- Killing player giving the name of what they died to
- Giving player gold



**Script for Nextbot appearance (you will have to change folder)**

```
local HttpService = game:GetService("HttpService")
local data = HttpService:GetAsync("https://raw.githubusercontent.com/StrikeWasTaken/door/refs/heads/main/nextbot-appearance.json")

local function get_random_nextbot(jsonData)
    local decodedData = HttpService:JSONDecode(jsonData)
    local nextbots = decodedData.nextbots
    local randomIndex = math.random(#nextbots)
    return nextbots[randomIndex]
end

local selectedNextbot = get_random_nextbot(data)


--values to use

--selectedNextbot.name
--selectedNextbot.appearance.imageId
--selectedNextbot.appearance.audio.id
--selectedNextbot.appearance.audio.volume
```
**Script for game room**

```
local InsertService = game:GetService("InsertService")
local HttpService = game:GetService("HttpService")
local jsonData = HttpService:JSONDecode(HttpService:GetAsync("https://raw.githubusercontent.com/StrikeWasTaken/door/refs/heads/main/game-rooms.json"))
local folder = your folder

local function importRoom(modelId)
    local model = InsertService:LoadAsset(modelId)
    model.Parent = folder
    model.Name = model:GetChildren()[1].Name
end



for i, roomData in ipairs(jsonData.rooms) do
    importRoom(jsonData.rooms[i].id)
end
```

