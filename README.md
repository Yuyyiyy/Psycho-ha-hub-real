-- SERVICES
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Allowed users list
local allowedUsers = {
    "Test1", "test2", "test3", "psychopowerful90", "test5",
    "Test6", "Test7", "Test8", "Test9", "Test10",
    "Test11", "Test12", "Test13", "Test14", "Test15",
    "testUser16", "testUser17", "testUser18", "testUser19", "testUser20",
    "testUser21", "testUser22", "testUser23", "testUser24", "testUser25",
    "testUser26", "testUser27", "testUser28", "testUser29", "testUser30",
    "testUser31", "testUser32", "testUser33", "testUser34", "testUser35",
    "testUser36"
}

if not table.find(allowedUsers, player.Name) then
    player:Kick("HAHA🖕🖕STUPID 🤣")
    return
end

-- GUI Setup
local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "PsychoHAHub"
screenGui.ResetOnSpawn = false

-- Toggle Group Frame
local toggleGroup = Instance.new("Frame")
toggleGroup.Name = "ToggleGroup"
toggleGroup.Parent = screenGui
toggleGroup.BackgroundTransparency = 1
toggleGroup.Size = UDim2.new(0, 80, 0, 80)
toggleGroup.AnchorPoint = Vector2.new(0.5, 0.5)
toggleGroup.Position = UDim2.new(0.93, 0, 0.05, 0)

-- Background Circle for Toggle
local backgroundCircle = Instance.new("Frame", toggleGroup)
backgroundCircle.Name = "BackgroundCircle"
backgroundCircle.Size = UDim2.new(1, 0, 1, 0)
backgroundCircle.BackgroundColor3 = Color3.fromRGB(10, 10, 25)
backgroundCircle.BorderSizePixel = 0
backgroundCircle.AnchorPoint = Vector2.new(0.5, 0.5)
backgroundCircle.Position = UDim2.new(0.5, 0, 0.5, 0)
Instance.new("UICorner", backgroundCircle).CornerRadius = UDim.new(1, 0)
local bgStroke = Instance.new("UIStroke", backgroundCircle)
bgStroke.Thickness = 2
bgStroke.Color = Color3.fromRGB(255, 215, 0)

-- Emoji Toggle Button
local toggleButton = Instance.new("TextButton", toggleGroup)
toggleButton.Name = "ToggleButton"
toggleButton.Text = "😂"
toggleButton.Font = Enum.Font.SourceSansBold
toggleButton.TextSize = 28
toggleButton.TextColor3 = Color3.fromRGB(255, 215, 0)
toggleButton.BackgroundTransparency = 1
toggleButton.BorderSizePixel = 0
toggleButton.Size = UDim2.new(0, 50, 0, 50)
toggleButton.Position = UDim2.new(0.5, 0, 0.5, 0)
toggleButton.AnchorPoint = Vector2.new(0.5, 0.5)
Instance.new("UICorner", toggleButton).CornerRadius = UDim.new(1, 0)
local emojiStroke = Instance.new("UIStroke", toggleButton)
emojiStroke.Thickness = 2
emojiStroke.Color = Color3.fromRGB(255, 215, 0)
emojiStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

-- Outer HAHA ring
local hahaTextOuter = "HAHAHAHAHAHAHA"
local outerLetters = {}
local outerRadius = 38

for i = 1, #hahaTextOuter do
    local char = Instance.new("TextLabel", toggleGroup)
    char.Name = "OuterLetter"..i
    char.Text = hahaTextOuter:sub(i, i)
    char.Font = Enum.Font.SourceSansBold
    char.TextSize = 12
    char.TextColor3 = Color3.fromRGB(255, 215, 0)
    char.BackgroundTransparency = 1
    char.Size = UDim2.new(0, 14, 0, 14)
    char.AnchorPoint = Vector2.new(0.5, 0.5)
    outerLetters[i] = char
end

-- Inner HAHA ring
local hahaTextInner = "HAHA"
local innerLetters = {}
local innerRadius = 20

for i = 1, #hahaTextInner do
    local char = Instance.new("TextLabel", toggleGroup)
    char.Name = "InnerLetter"..i
    char.Text = hahaTextInner:sub(i, i)
    char.Font = Enum.Font.SourceSansBold
    char.TextSize = 10
    char.TextColor3 = Color3.fromRGB(255, 215, 0)
    char.BackgroundTransparency = 1
    char.Size = UDim2.new(0, 12, 0, 12)
    char.AnchorPoint = Vector2.new(0.5, 0.5)
    innerLetters[i] = char
end

local rotationOuter = 0
local rotationInner = 0
local speedOuter = math.rad(60)
local speedInner = -math.rad(90)

RunService.RenderStepped:Connect(function(dt)
    rotationOuter = (rotationOuter + speedOuter * dt) % (2 * math.pi)
    rotationInner = (rotationInner + speedInner * dt) % (2 * math.pi)

    local centerX = toggleGroup.AbsoluteSize.X / 2
    local centerY = toggleGroup.AbsoluteSize.Y / 2

    for i, letter in ipairs(outerLetters) do
        local angle = (2 * math.pi / #outerLetters) * (i - 1) + rotationOuter
        local x = centerX + outerRadius * math.cos(angle)
        local y = centerY + outerRadius * math.sin(angle)
        letter.Position = UDim2.new(0, x, 0, y)
    end

    for i, letter in ipairs(innerLetters) do
        local angle = (2 * math.pi / #innerLetters) * (i - 1) + rotationInner
        local x = centerX + innerRadius * math.cos(angle)
        local y = centerY + innerRadius * math.sin(angle)
        letter.Position = UDim2.new(0, x, 0, y)
    end
end)

-- Main Frame
local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Name = "MainFrame"
mainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 25)
mainFrame.BorderColor3 = Color3.fromRGB(255, 215, 0)
mainFrame.Position = UDim2.new(0.25, 0, 0.2, 0)
mainFrame.Size = UDim2.new(0, 500, 0, 420)
mainFrame.Visible = true
mainFrame.BorderSizePixel = 4
mainFrame.Active = true
mainFrame.Draggable = true
Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 15)
local mainStroke = Instance.new("UIStroke", mainFrame)
mainStroke.Thickness = 3
mainStroke.Color = Color3.fromRGB(184, 134, 11)

local title = Instance.new("TextLabel", mainFrame)
title.Text = "🤣Psycho HA Hub🤣"
title.Font = Enum.Font.SourceSansBold
title.TextSize = 42
title.TextColor3 = Color3.fromRGB(255, 215, 0)
title.BackgroundTransparency = 1
title.Position = UDim2.new(0.05, 0, 0.01, 0)
title.Size = UDim2.new(0.9, 0, 0.15, 0)

-- Scrolling Frame for Script Buttons
local scroll = Instance.new("ScrollingFrame", mainFrame)
scroll.BackgroundTransparency = 1
scroll.Size = UDim2.new(1, -20, 0.65, 0)
scroll.Position = UDim2.new(0, 10, 0.2, 0)
scroll.ScrollBarThickness = 6
scroll.BorderSizePixel = 0
scroll.CanvasSize = UDim2.new(0, 0, 0, 0)
Instance.new("UICorner", scroll).CornerRadius = UDim.new(0, 10)
local scrollStroke = Instance.new("UIStroke", scroll)
scrollStroke.Thickness = 2
scrollStroke.Color = Color3.fromRGB(184, 134, 11)

local layout = Instance.new("UIGridLayout", scroll)
layout.CellSize = UDim2.new(0, 140, 0, 50)
layout.CellPadding = UDim2.new(0, 10, 0, 10)
layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    scroll.CanvasSize = UDim2.new(0, 0, 0, layout.AbsoluteContentSize.Y + 20)
end)

-- Page Buttons Frame
local pageButtonsFrame = Instance.new("Frame", mainFrame)
pageButtonsFrame.Name = "PageButtonsFrame"
pageButtonsFrame.BackgroundTransparency = 1
pageButtonsFrame.Position = UDim2.new(0, 10, 0.87, 0)
pageButtonsFrame.Size = UDim2.new(1, -20, 0, 40)

local pageBtn = Instance.new("TextButton", pageButtonsFrame)
pageBtn.Name = "PageButton1"
pageBtn.Text = "1"
pageBtn.Font = Enum.Font.SourceSansSemibold
pageBtn.TextColor3 = Color3.fromRGB(255, 215, 0)
pageBtn.TextSize = 18
pageBtn.BackgroundColor3 = Color3.fromRGB(15, 15, 30)
pageBtn.BorderColor3 = Color3.fromRGB(255, 215, 0)
pageBtn.Size = UDim2.new(0, 30, 0, 30)
Instance.new("UICorner", pageBtn).CornerRadius = UDim.new(0, 6)

-- Script Buttons Data
local buttonsPagesData = {{
    {Text = "Instant Spawn", ScriptLink = "https://pastebin.com/raw/CYa08iQL"},
    {Text = "", ScriptLink = ""},
    {Text = "No cooldown 75%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/246d84003ec77b3348b785f4c4b40951/raw/2e03b6f231e8ddeba6c7e40afedd919907138ddf/gistfile1.txt"},
    {Text = "No cooldown 100%", ScriptLink = "https://pastebin.com/raw/Qxnj4RG9"},
    {Text = "Aura", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/69cd1fb21a09185e359a3eb706108aa9/raw/94e203ae28989cbe5c4c5fa2f9bf0f1263937738/gistfile1.txt"},
    {Text = "No clip for damage hitbox", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/04661c54b473431b9ab554de484e1e1f/raw/2a08e9b05c7cd4c64001138728a6b3c316a805e7/gistfile1.txt"},
    {Text = "grab base", ScriptLink = "https://pastebin.com/raw/KeFcGRBg"},
    {Text = "Script 8", ScriptLink = "https://pastebin.com/raw/WKvWP9KC"},
    {Text = "script 9", ScriptLink = ""},
    {Text = "Auto grab", ScriptLink = "https://pastebin.com/raw/uASxtqN3"},
    {Text = "spt auto grab", ScriptLink = "https://pastebin.com/raw/MHN7tVU8"},
    {Text = " loopbring", ScriptLink = "https://pastebin.com/raw/NHcMJWXu"},
    {Text = "usetools", ScriptLink = "https://pastebin.com/raw/fnGNW8Lk"},
    {Text = "damage kill", ScriptLink = "https://pastebin.com/raw/MFr8E9ag"},
    {Text = "Damage hitbox", ScriptLink = "https://pastebin.com/raw/63T2aMVi"},
    {Text = "anti lag", ScriptLink = "https://pastebin.com/raw/Y2rYwLTp"},
    {Text = "Lag server", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/6f38723afc3d835dc1f8bc96b9f61bd8/raw/9d7b2525de18a7f1220d5c78fcfdf34b7da5e05f/gistfile1.txt"},
    {Text = "No cooldown 20%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/435a09384699c8f3e910444d877f123c/raw/29721b83c34f0c51059a6839e978c1b0fc4a7570/gistfile1.txt"},
    {Text = "No cooldown 30%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/602ad74771fa6ed8b0118b8b2303c0cb/raw/a90c5000987fe694ae8fd250df0e981032245b4a/gistfile1.txt"},
    {Text = "No cooldown 50%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/b2fc36b1230d4bb9b06db2a419f50a8a/raw/e442c967add6123afd88d717b773361f7ad62af2/gistfile1.txt"},
}}

local currentPage = 1

local function clearScroll()
    for _, child in pairs(scroll:GetChildren()) do
        if child:IsA("TextButton") then
            child:Destroy()
        end
    end
end

local function createScriptButtons(page)
    clearScroll()
    local pageData = buttonsPagesData[page]
    for index = 1, #pageData do
        local data = pageData[index]
        local button = Instance.new("TextButton", scroll)
        button.Name = "ScriptButton" .. index
        button.TextWrapped = true
        button.TextYAlignment = Enum.TextYAlignment.Center
        button.Text = data.Text
        button.Font = Enum.Font.SourceSansSemibold
        button.TextColor3 = Color3.fromRGB(255, 215, 0)
        button.TextSize = 20
        button.BackgroundColor3 = Color3.fromRGB(15, 15, 30)
        button.BorderColor3 = Color3.fromRGB(255, 215, 0)
        button.AutoButtonColor = true
        button.Size = UDim2.new(0, 140, 0, 50)

        local btnCorner = Instance.new("UICorner", button)
        btnCorner.CornerRadius = UDim.new(0, 8)

        local btnStroke = Instance.new("UIStroke", button)
        btnStroke.Thickness = 1.5
        btnStroke.Color = Color3.fromRGB(184, 134, 11)
        btnStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

        button.MouseButton1Click:Connect(function()
            print(data.Text .. " button clicked")
            local success, err = pcall(function()
                loadstring(game:HttpGet(data.ScriptLink))()
            end)
            if not success then
                warn("Failed to load script:", err)
            end
        end)
    end
end

pageBtn.MouseButton1Click:Connect(function()
    currentPage = 1
    createScriptButtons(currentPage)
end)

-- Initial buttons load
createScriptButtons(currentPage)

-- Toggle Main Frame Visibility on toggleButton click
toggleButton.MouseButton1Click:Connect(function()
    mainFrame.Visible = not mainFrame.Visible
end)
