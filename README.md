local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Allowed users list
local testUsers = {
    "Klaywessels_48171", "Vealskylab", "Xdemon123679", "psychopowerful049", "psychopowerful90",
    "imdabestkid273", "Test7", "Test8", "Test9", "Test10",
    "Test11", "Test12", "Test13", "Test14", "Test15",
    "testUser16", "testUser17", "testUser18", "testUser19", "testUser20",
    "testUser21", "testUser22", "testUser23", "testUser24", "testUser25",
    "testUser26", "testUser27", "testUser28", "testUser29", "testUser30",
    "testUser31", "testUser32", "testUser33", "testUser34", "testUser35",
    "testUser36"
}

local function isAllowed(name)
    name = string.lower(name)
    for _, allowedName in ipairs(testUsers) do
        if string.lower(allowedName) == name then
            return true
        end
    end
    return false
end

-- Kick unauthorized players
if not isAllowed(player.Name) then
    player:Kick("HAHA 🖕🖕STUPID 🤣")
    return
end

-- GUI setup
local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "PsychoHAHub"
screenGui.ResetOnSpawn = false

-- Main window
local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Name = "MainFrame"
mainFrame.BackgroundColor3 = Color3.fromRGB(10,10,25)
mainFrame.BorderColor3 = Color3.fromRGB(255,215,0)
mainFrame.Position = UDim2.new(0.25,0,0.2,0)
mainFrame.Size = UDim2.new(0,500,0,420)
mainFrame.BorderSizePixel = 4
mainFrame.Active = true
mainFrame.Draggable = true
Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0,15)
local frameStroke = Instance.new("UIStroke", mainFrame)
frameStroke.Thickness = 3
frameStroke.Color = Color3.fromRGB(184,134,11)

-- Title
local title = Instance.new("TextLabel", mainFrame)
title.Text = "🤣Psycho HA Hub🤣"
title.Font = Enum.Font.SourceSansBold
title.TextSize = 42
title.TextColor3 = Color3.fromRGB(255,215,0)
title.BackgroundTransparency = 1
title.Position = UDim2.new(0.05,0,0.01,0)
title.Size = UDim2.new(0.9,0,0.15,0)

-- Scroll area
local scroll = Instance.new("ScrollingFrame", mainFrame)
scroll.BackgroundTransparency = 1
scroll.Size = UDim2.new(1,-20,0.65,0)
scroll.Position = UDim2.new(0,10,0.2,0)
scroll.ScrollBarThickness = 6
scroll.BorderSizePixel = 0
scroll.CanvasSize = UDim2.new(0,0,0,0)
Instance.new("UICorner", scroll).CornerRadius = UDim.new(0,10)
local sStroke = Instance.new("UIStroke", scroll)
sStroke.Thickness = 2
sStroke.Color = Color3.fromRGB(184,134,11)

local layout = Instance.new("UIGridLayout", scroll)
layout.CellSize = UDim2.new(0,140,0,50)
layout.CellPadding = UDim2.new(0,10,0,10)
layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    scroll.CanvasSize = UDim2.new(0,0,0, layout.AbsoluteContentSize.Y + 20)
end)

-- All your script buttons
local buttonsPagesData = {{
    {Text = "Instant Spawn", ScriptLink = "https://pastebin.com/raw/4mJt6ZNt"},
    {Text = "No cooldown 75%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/246d84003ec77b3348b785f4c4b40951/raw/2e03b6f231e8ddeba6c7e40afedd919907138ddf/gistfile1.txt"},
    {Text = "No cooldown 100%", ScriptLink = "https://pastebin.com/raw/Qxnj4RG9"},
    {Text = "Aura", ScriptLink = "https://pastebin.com/raw/Yc09EgZY"},
    {Text = "No clip for damage hitbox", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/04661c54b473431b9ab554de484e1e1f/raw/2a08e9b05c7cd4c64001138728a6b3c316a805e7"},
    {Text = "coming soon", ScriptLink = ""},
    {Text = "spin claws", ScriptLink = "https://pastebin.com/raw/fe8Ut9JQ"},
    {Text = "Anti lag", ScriptLink = "https://pastebin.com/raw/u5KgwBeD"},
    {Text = "Power UP ", ScriptLink = ""}, -- Added placeholder link
    {Text = "SPT auto grab", ScriptLink = "https://pastebin.com/raw/MHN7tVU8"},
    {Text = "Loopbring", ScriptLink = "https://pastebin.com/raw/auhh19BE"},
    {Text = "Use tools", ScriptLink = "https://pastebin.com/raw/fnGNW8Lk"},
    {Text = "Auto grab", ScriptLink = "https://pastebin.com/raw/QUjHZPAb"},
    {Text = "Damage hitbox", ScriptLink = "https://pastebin.com/raw/BF4LJ4QB"},
    {Text = "FPS", ScriptLink = "https://pastebin.com/raw/ZMM98Aaj"},
    {Text = "Lag server", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/6f38723afc3d835dc1f8bc96b9f61bd8/raw/9d7b2525de18a7f1220d5c78fcfdf34b7da5e05f"},
    {Text = "No cooldown 20%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/435a09384699c8f3e910444d877f123c/raw/29721b83c34f0c51059a6839e978c1b0fc4a7570"},
    {Text = "No cooldown 30%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/602ad74771fa6ed8b0118b8b2303c0cb/raw/a90c5000987fe694ae8fd250df0e981032245b4a"},
    {Text = "No cooldown 50%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/b2fc36b1230d4bb9b06db2a419f50a8a/raw/e442c967add6123afd88d717b773361f7ad62af2"},
    {Text = "Auto base", ScriptLink = "https://pastefy.app/kS9BglBQ/raw"},
    {Text = "Fling", ScriptLink = "https://pastebin.com/raw/uh8c1JPM"},
    {Text = "Script 22", ScriptLink = "https://pastebin.com/raw/placeholder2"}, -- Fixed syntax error and added placeholder
}}

-- Make buttons
local function clearScroll()
    for _, c in ipairs(scroll:GetChildren()) do
        if c:IsA("TextButton") then
            c:Destroy()
        end
    end
end

local function createScriptButtons()
    clearScroll()
    for i, data in ipairs(buttonsPagesData[1]) do
        if data.Text and data.Text ~= "" then
            local btn = Instance.new("TextButton", scroll)
            btn.Name = "ScriptBtn"..i
            btn.Text = data.Text
            btn.Font = Enum.Font.SourceSansSemibold
            btn.TextSize = 20
            btn.TextColor3 = Color3.fromRGB(255,215,0)
            btn.BackgroundColor3 = Color3.fromRGB(15,15,30)
            btn.BorderColor3 = Color3.fromRGB(255,215,0)
            btn.Size = UDim2.new(0,140,0,50)
            btn.AutoButtonColor = true
            Instance.new("UICorner", btn).CornerRadius = UDim.new(0,8)
            local st = Instance.new("UIStroke", btn)
            st.Thickness = 1.5
            st.Color = Color3.fromRGB(184,134,11)
            st.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

            btn.MouseButton1Click:Connect(function()
                print("Executing:", data.Text)
                if data.ScriptLink and data.ScriptLink ~= "" then
                    local success, result = pcall(function()
                        local scriptContent = game:HttpGet(data.ScriptLink)
                        return loadstring(scriptContent)()
                    end)
                    if not success then
                        warn("Error loading " .. data.Text .. ": " .. tostring(result))
                    end
                else
                    warn("No script link provided for: " .. data.Text)
                end
            end)
        end
    end
end

createScriptButtons()

-- Toggle Button
local toggleGroup = Instance.new("Frame")
toggleGroup.Name = "ToggleGroup"
toggleGroup.Parent = screenGui
toggleGroup.BackgroundTransparency = 1
toggleGroup.Size = UDim2.new(0, 80, 0, 80)
toggleGroup.AnchorPoint = Vector2.new(0.5, 0.5)
toggleGroup.Position = UDim2.new(0.93, 0, 0.05, 0)

local bg = Instance.new("Frame", toggleGroup)
bg.Name = "BackgroundCircle"
bg.Size = UDim2.new(1, 0, 1, 0)
bg.BackgroundColor3 = Color3.fromRGB(10,10,25)
bg.BorderSizePixel = 0
bg.AnchorPoint = Vector2.new(0.5,0.5)
bg.Position = UDim2.new(0.5,0,0.5,0)
Instance.new("UICorner", bg).CornerRadius = UDim.new(1,0)
local stroke = Instance.new("UIStroke", bg)
stroke.Thickness = 2
stroke.Color = Color3.fromRGB(255,215,0)

local btn = Instance.new("TextButton", toggleGroup)
btn.Name = "ToggleButton"
btn.Text = "🤣"
btn.Font = Enum.Font.SourceSansBold
btn.TextSize = 28
btn.TextColor3 = Color3.fromRGB(255,215,0)
btn.BackgroundTransparency = 1
btn.BorderSizePixel = 0
btn.Size = UDim2.new(0,50,0,50)
btn.AnchorPoint = Vector2.new(0.5,0.5)
btn.Position = UDim2.new(0.5,0,0.5,0)
Instance.new("UICorner", btn).CornerRadius = UDim.new(1,0)
local btnStroke = Instance.new("UIStroke", btn)
btnStroke.Thickness = 2
btnStroke.Color = Color3.fromRGB(255,215,0)
btnStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

-- Open/Close Logic
local isOpen = true
btn.MouseButton1Click:Connect(function()
    isOpen = not isOpen
    mainFrame.Visible = isOpen
end)

-- Rotating HA letters
local outerText, innerText = "HAHAHAHA", "HAHA"
local outerLetters, innerLetters = {}, {}
local outerRad, innerRad = 35, 20
for i = 1, #outerText do
    local tl = Instance.new("TextLabel", toggleGroup)
    tl.Text = outerText:sub(i,i)
    tl.Font = Enum.Font.SourceSansBold
    tl.TextSize = 12
    tl.TextColor3 = Color3.fromRGB(255,215,0)
    tl.BackgroundTransparency = 1
    tl.Size = UDim2.new(0,14,0,14)
    tl.AnchorPoint = Vector2.new(0.5,0.5)
    outerLetters[i] = tl
end
for i = 1, #innerText do
    local tl = Instance.new("TextLabel", toggleGroup)
    tl.Text = innerText:sub(i,i)
    tl.Font = Enum.Font.SourceSansBold
    tl.TextSize = 10
    tl.TextColor3 = Color3.fromRGB(255,215,0)
    tl.BackgroundTransparency = 1
    tl.Size = UDim2.new(0,12,0,12)
    tl.AnchorPoint = Vector2.new(0.5,0.5)
    innerLetters[i] = tl
end

local rotOuter, rotInner = 0, 0
local speedO, speedI = math.rad(60), -math.rad(90)
RunService.RenderStepped:Connect(function(dt)
    rotOuter = (rotOuter + speedO*dt) % (2*math.pi)
    rotInner = (rotInner + speedI*dt) % (2*math.pi)
    local cx, cy = toggleGroup.AbsoluteSize.X/2, toggleGroup.AbsoluteSize.Y/2
    for i, tl in ipairs(outerLetters) do
        local ang = (2*math.pi/#outerLetters)*(i-1) + rotOuter
        tl.Position = UDim2.new(0, cx + outerRad*math.cos(ang), 0, cy + outerRad*math.sin(ang))
    end
    for i, tl in ipairs(innerLetters) do
        local ang = (2*math.pi/#innerLetters)*(i-1) + rotInner
        tl.Position = UDim2.new(0, cx + innerRad*math.cos(ang), 0, cy + innerRad*math.sin(ang))
    end
end)
