**hi this is door so the nextbot appearance gives data on the name of the nextbot, the image id and audio id (the name is used for the kill screen). it will say Died to (name) Nextbot. the game room are roblox model ids of the rooms that will need to be imported.**

**Script for Nextbot appearance (you will have to change folder)**

local HttpService = game:GetService("HttpService")
local data = HttpService:GetAsync("https://raw.githubusercontent.com/StrikeWasTaken/door/refs/heads/main/nextbots.json")

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

**Script for game room**


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


exobyte pls make documentation for door
