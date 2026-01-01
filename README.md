-- ScreenGui اصلی
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "CustomHub"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- گلوبال برای دسترسی
_G.MainHubGui = ScreenGui

-- فریم اصلی
local MainFrame = Instance.new("Frame")
MainFrame.Size = UDim2.new(0, 350, 0, 460) 
MainFrame.Position = UDim2.new(0.5, -175, 0.5, -230)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
MainFrame.Active = true 
MainFrame.Draggable = false 
MainFrame.Parent = ScreenGui

-- دکمه $ برای Drag
local DragButton = Instance.new("TextButton")
DragButton.Size = UDim2.new(0, 40, 0, 40)
DragButton.Position = UDim2.new(0, 5, 1, -5)
DragButton.AnchorPoint = Vector2.new(0,1)
DragButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
DragButton.Text = "$"
DragButton.TextColor3 = Color3.fromRGB(255, 0, 0)
DragButton.Font = Enum.Font.SourceSansBold
DragButton.TextSize = 24
DragButton.Parent = MainFrame

-- تابع Dragify
local function Dragify(Frame, DragHandle)
    local UIS = game:GetService("UserInputService")
    local dragging, dragInput, dragStart, startPos

    DragHandle.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            dragStart = input.Position
            startPos = Frame.Position

            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)

    DragHandle.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            dragInput = input
        end
    end)

    UIS.InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            local delta = input.Position - dragStart
            Frame.Position = UDim2.new(
                startPos.X.Scale, startPos.X.Offset + delta.X,
                startPos.Y.Scale, startPos.Y.Offset + delta.Y
            )
        end
    end)
end
Dragify(MainFrame, DragButton)

-- عنوان (toggle باز/بسته)
local Title = Instance.new("TextButton")
Title.Size = UDim2.new(1, 0, 0, 40)
Title.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Title.Text = "GUI Fr_394"
Title.TextColor3 = Color3.new(1,1,1)
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 20
Title.Parent = MainFrame
Title.MouseButton1Click:Connect(function()
    MainFrame.Visible = not MainFrame.Visible
end)

-- ScrollingFrame
local ScrollFrame = Instance.new("ScrollingFrame")
ScrollFrame.Size = UDim2.new(1, -10, 1, -50)
ScrollFrame.Position = UDim2.new(0, 5, 0, 45)
ScrollFrame.CanvasSize = UDim2.new(0, 0, 3, 0)
ScrollFrame.ScrollBarThickness = 8
ScrollFrame.BackgroundTransparency = 1
ScrollFrame.Parent = MainFrame

-- ساخت دکمه
local function CreateButton(name, posY, callback)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0.8, 0, 0, 50)
    btn.Position = UDim2.new(0.1, 0, 0, posY)
    btn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    btn.Text = name
    btn.TextColor3 = Color3.fromRGB(255,0,0)
    btn.Font = Enum.Font.SourceSansBold
    btn.TextSize = 22
    btn.Parent = ScrollFrame
    btn.MouseButton1Click:Connect(callback)
    return btn
end

-- همه دکمه‌های اصلی
CreateButton("Aim Bot", 0, function() loadstring(game:HttpGet("https://raw.githubusercontent.com/sdfesdfsedf/srgtergasdfs/main/aim", true))() end)
CreateButton("Invalid", 60, function() loadstring(game:HttpGet('https://pastebin.com/raw/3Rnd9rHf'))() end)
CreateButton("ESP", 120, function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jonthedruger/LatvixDoc/script/idkgamenameforgot.lua",true))() end)
CreateButton("Zepher HUB", 180, function() loadstring(game:HttpGet("https://rawscripts.net/raw/Murderers-VS-Sheriffs-Duels-ZEPHYR-MVSD-SCRIPT-KEYLESS-36170"))() end)
CreateButton("99 NIGHT", 240, function() loadstring(game:HttpGet("https://rawscripts.net/raw/99-Nights-in-the-Forest-Voidware-48939"))() end)
CreateButton("Street Life", 300, function() loadstring(game:HttpGet("https://rawscripts.net/raw/Street-Life-Remastered-Street-life-Remastered-New-Best-Script-43326"))() end)
CreateButton("UI INI", 360, function() loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Infinite-Yield-43437"))() end)
CreateButton("Fly", 420, function() loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Fly-Script-48648"))() end)
CreateButton("Ghost", 480, function() loadstring(game:HttpGet('https://raw.githubusercontent.com/GhostPlayer352/Test4/main/GhostHub'))() end)
CreateButton("Wallhop", 530, function() loadstring(game:HttpGet("https://raw.githubusercontent.com/ScpGuest666/Random-Roblox-script/refs/heads/main/Roblox%20WallHop%20V4%20script"))() end)
CreateButton("F3X Tool", 610, function() loadstring(game:GetObjects("rbxassetid://6695644299")[1].Source)() end)
CreateButton("Fly Invincible ", 670, function() loadstring(game:HttpGet('https://pastebin.com/raw/hbZ7EWkU'))() end)
CreateButton("Stell Item ", 790, function() loadstring(game:HttpGet("https://raw.githubusercontent.com/RealBatu20/AI-Scripts-2025/refs/heads/main/BackpackToolCounter.lua"))() end)
CreateButton("ITEM GUVEr", 850, function() loadstring(game:HttpGet("https://raw.githubusercontent.com/yofriendfromschool1/Sky-Hub-Backup/main/gametoolgiver.lua"))() end)
CreateButton("99NIGHT +", 910, function() loadstring(game:HttpGet("https://raw.githubusercontent.com/0jayz0/Elysium99nights/main/source.lua"))() end)
CreateButton("AIMBOT MOBILE", 970,function() loadstring(game:HttpGet("https://raw.githubusercontent.com/DanielHubll/DanielHubll/refs/heads/main/Aimbot%20Mobile"))() end)
CreateButton("fly V2", 1030,function()
    local UserInputService = game:GetService("UserInputService")
    local isMobile = UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled
    if isMobile then loadstring(game:HttpGet("https://raw.githubusercontent.com/396abc/Script/refs/heads/main/MobileFly.lua"))()
    else loadstring(game:HttpGet("https://raw.githubusercontent.com/396abc/Script/refs/heads/main/FlyR15.lua"))() end
end)
CreateButton("kill all need sword", 1090,function()
    local player = game:GetService("Players").LocalPlayer
    local isActive = false

    local gui = Instance.new("ScreenGui")
    gui.Parent = _G.MainHubGui

    local toggleButton = Instance.new("TextButton")
    toggleButton.Size = UDim2.new(0, 100, 0, 50)
    toggleButton.Position = UDim2.new(0.5, -50, 0.9, -30)
    toggleButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
    toggleButton.Text = "OFF"
    toggleButton.Font = Enum.Font.SourceSansBold
    toggleButton.TextSize = 20
    toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    toggleButton.Parent = gui

    toggleButton.MouseButton1Click:Connect(function()
        isActive = not isActive
        toggleButton.BackgroundColor3 = isActive and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(255, 0, 0)
        toggleButton.Text = isActive and "ON" or "OFF"
    end)

    game:GetService("RunService").RenderStepped:Connect(function()
        if isActive then
            for _, otherPlayer in ipairs(game.Players:GetPlayers()) do
                if otherPlayer ~= player then
                    local character = otherPlayer.Character
                    local myChar = player.Character
                    if character and myChar then
                        local tool = myChar:FindFirstChildOfClass("Tool")
                        if tool and tool:FindFirstChild("Handle") then
                            local ff = character:FindFirstChildOfClass("ForceField")
                            if ff then ff:Destroy() end
                            tool:Activate()
                            for _, part in ipairs(character:GetDescendants()) do
                                if part:IsA("BasePart") then
                                    firetouchinterest(tool.Handle, part, 0)
                                    firetouchinterest(tool.Handle, part, 1)
                                end
                            end
                        end
                    end
                end
            end
        end
    end)
end)
CreateButton("Murder vs sharif", 1150,function() loadstring(game:HttpGet("https://bitbucket.org/lua-buffoonery/scripts/raw/ea1d852fbc75e549db0a427892be7769805248d7/mvsd/gui.lua"))() end)
CreateButton("aimbto", 1210,function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Exunys/Aimbot-V3/main/src/Aimbot.lua"))()
    ExunysDeveloperAimbot()
end)

-- دکمه FR_PLAYERGUI1.01 با قابلیت Bring All
CreateButton("FR_PLAYERGUI1.01", 1270, function()
    local Players = game:GetService("Players")
    local RunService = game:GetService("RunService")
    local Workspace = game:GetService("Workspace")
    local LocalPlayer = Players.LocalPlayer

    local originalPositions = {}
    local bringLoops = {}
    local espLoops = {}
    local espMarkers = {}
    local viewingTarget = nil
    local espActive = {}
    local freezeLoops = {}
    local isFrozen = false
    local freezeMeLoop = nil

    local gui = Instance.new("ScreenGui")
    gui.Name = "Fr_GUIFE"
    gui.ResetOnSpawn = false
    gui.Parent = _G.MainHubGui

    local frame = Instance.new("ScrollingFrame", gui)
    frame.Size = UDim2.new(0, 260, 0, 420)
    frame.Position = UDim2.new(0.5, -130, 0.5, -210)
    frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    frame.CanvasSize = UDim2.new(0, 0, 0, 600)
    frame.ScrollBarThickness = 6
    frame.Active = true
    frame.Draggable = true

    local exitBtn = Instance.new("TextButton", frame)
    exitBtn.Size = UDim2.new(0, 60, 0, 30)
    exitBtn.Position = UDim2.new(1, -70, 0, 5)
    exitBtn.Text = "Exit"
    exitBtn.BackgroundColor3 = Color3.fromRGB(100, 0, 0)
    exitBtn.TextColor3 = Color3.new(1, 1, 1)
    exitBtn.MouseButton1Click:Connect(function()
        frame.Visible = false
    end)

    local title = Instance.new("TextLabel", frame)
    title.Size = UDim2.new(1, -80, 0, 30)
    title.Position = UDim2.new(0, 10, 0, 5)
    title.Text = "Fr_GUIFE"
    title.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    title.TextColor3 = Color3.new(1, 1, 1)
    title.Font = Enum.Font.SourceSansBold
    title.TextSize = 18

    local input = Instance.new("TextBox", frame)
    input.Size = UDim2.new(1, -20, 0, 30)
    input.Position = UDim2.new(0, 10, 0, 40)
    input.PlaceholderText = "نام پلیر یا 'all' برای همه"
    input.Text = ""

    local distanceBox = Instance.new("TextBox", frame)
    distanceBox.Size = UDim2.new(1, -20, 0, 30)
    distanceBox.Position = UDim2.new(0, 10, 0, 80)
    distanceBox.PlaceholderText = "فاصله (مثلاً 3)"
    distanceBox.Text = "3"

    local function findPlayer(partial)
        if partial == "" then return nil end
        partial = partial:lower()
        for _, p in pairs(Players:GetPlayers()) do
            if p.Name:lower():sub(1, #partial) == partial then
                return p
            end
        end
        return nil
    end

    local function createButton(text, yOffset, color)
        local btn = Instance.new("TextButton", frame)
        btn.Size = UDim2.new(1, -20, 0, 30)
        btn.Position = UDim2.new(0, 10, 0, yOffset)
        btn.Text = text
        btn.BackgroundColor3 = color
        btn.TextColor3 = Color3.new(1, 1, 1)
        btn.Font = Enum.Font.SourceSans
        btn.TextSize = 16
        return btn
    end

    local bringBtn = createButton("Bring", 120, Color3.fromRGB(0, 170, 0))
    local unbringBtn = createButton("Unbring", 160, Color3.fromRGB(170, 0, 0))
    local viewBtn = createButton("View", 200, Color3.fromRGB(0, 85, 170))
    local unviewBtn = createButton("Unview", 240, Color3.fromRGB(85, 0, 170))
    local espBtn = createButton("ESP Toggle", 280, Color3.fromRGB(255, 85, 0))
    local tpBtn = createButton("Teleport to Player", 320, Color3.fromRGB(0, 200, 200))
    local freezeBtn = createButton("Freeze Player", 360, Color3.fromRGB(200, 200, 0))
    local freezeMeBtn = createButton("FreezeMe", 400, Color3.fromRGB(255, 200, 0))
    local speedBtn = createButton("Speed", 440, Color3.fromRGB(120, 120, 255))

    local speedInput = Instance.new("TextBox", frame)
    speedInput.Size = UDim2.new(1, -20, 0, 30)
    speedInput.Position = UDim2.new(0, 10, 0, 480)
    speedInput.PlaceholderText = "مقدار سرعت (مثلاً 50)"
    speedInput.Text = ""

    -- Bring با پشتیبانی از all
    bringBtn.MouseButton1Click:Connect(function()
        local text = input.Text:lower()
        local distance = tonumber(distanceBox.Text) or 3

        if text == "all" then
            for _, target in pairs(Players:GetPlayers()) do
                if target ~= LocalPlayer and target.Character and target.Character:FindFirstChild("HumanoidRootPart") then
                    local targetRoot = target.Character.HumanoidRootPart
                    local myRoot = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                    if myRoot then
                        if not originalPositions[target.Name] then
                            originalPositions[target.Name] = targetRoot.CFrame
                        end
                        if bringLoops[target.Name] then bringLoops[target.Name]:Disconnect() end
                        bringLoops[target.Name] = RunService.Heartbeat:Connect(function()
                            if targetRoot.Parent and myRoot.Parent then
                                targetRoot.CFrame = myRoot.CFrame * CFrame.new(0, 0, -distance)
                            end
                        end)
                    end
                end
            end
        else
            local target = findPlayer(input.Text)
            if target and target ~= LocalPlayer and target.Character then
                local targetRoot = target.Character:FindFirstChild("HumanoidRootPart")
                local myRoot = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                if targetRoot and myRoot then
                    if not originalPositions[target.Name] then
                        originalPositions[target.Name] = targetRoot.CFrame
                    end
                    if bringLoops[target.Name] then bringLoops[target.Name]:Disconnect() end
                    bringLoops[target.Name] = RunService.Heartbeat:Connect(function()
                        targetRoot.CFrame = myRoot.CFrame * CFrame.new(0, 0, -distance)
                    end)
                end
            end
        end
    end)

    -- Unbring با پشتیبانی از all
    unbringBtn.MouseButton1Click:Connect(function()
        local text = input.Text:lower()

        if text == "all" then
            for _, target in pairs(Players:GetPlayers()) do
                if target ~= LocalPlayer and bringLoops[target.Name] then
                    bringLoops[target.Name]:Disconnect()
                    bringLoops[target.Name] = nil
                    if originalPositions[target.Name] and target.Character then
                        local root = target.Character:FindFirstChild("HumanoidRootPart")
                        if root then root.CFrame = originalPositions[target.Name] end
                        originalPositions[target.Name] = nil
                    end
                end
            end
        else
            local target = findPlayer(input.Text)
            if target and bringLoops[target.Name] then
                bringLoops[target.Name]:Disconnect()
                bringLoops[target.Name] = nil
                if originalPositions[target.Name] and target.Character then
                    local root = target.Character:FindFirstChild("HumanoidRootPart")
                    if root then root.CFrame = originalPositions[target.Name] end
                    originalPositions[target.Name] = nil
                end
            end
        end
    end)

    -- بقیه دکمه‌ها (همون قبلی خودت)
    viewBtn.MouseButton1Click:Connect(function()
        local target = findPlayer(input.Text)
        if target and target.Character then
            local root = target.Character:FindFirstChild("HumanoidRootPart")
            if root then
                Workspace.CurrentCamera.CameraSubject = root
            end
        end
    end)

    unviewBtn.MouseButton1Click:Connect(function()
        if LocalPlayer.Character then
            Workspace.CurrentCamera.CameraSubject = LocalPlayer.Character:FindFirstChild("Humanoid")
        end
    end)

    espBtn.MouseButton1Click:Connect(function()
        local target = findPlayer(input.Text)
        if target and target.Character and LocalPlayer.Character then
            local root = target.Character:FindFirstChild("HumanoidRootPart")
            local humanoid = target.Character:FindFirstChildOfClass("Humanoid")
            local myRoot = LocalPlayer.Character:FindFirstChild("HumanoidRootPart")

            if root and humanoid and myRoot then
                if espActive[target.Name] then
                    espActive[target.Name] = false
                    if espMarkers[target.Name] then espMarkers[target.Name]:Destroy() espMarkers[target.Name] = nil end
                    if espLoops[target.Name] then espLoops[target.Name]:Disconnect() espLoops[target.Name] = nil end
                else
                    espActive[target.Name] = true
                    local marker = Instance.new("Part")
                    marker.Size = Vector3.new(1.5, 1.5, 1.5)
                    marker.Shape = Enum.PartType.Ball
                    marker.Color = Color3.new(1, 0, 0)
                    marker.Material = Enum.Material.Neon
                    marker.Anchored = true
                    marker.CanCollide = false
                    marker.Parent = Workspace
                    espMarkers[target.Name] = marker

                    local billboard = Instance.new("BillboardGui", marker)
                    billboard.Size = UDim2.new(0, 100, 0, 40)
                    billboard.AlwaysOnTop = true
                    billboard.StudsOffset = Vector3.new(0, 2, 0)

                    local label = Instance.new("TextLabel", billboard)
                    label.Size = UDim2.new(1, 0, 1, 0)
                    label.BackgroundTransparency = 1
                    label.TextColor3 = Color3.new(1, 1, 1)
                    label.TextStrokeTransparency = 0
                    label.Font = Enum.Font.SourceSansBold
                    label.TextSize = 16

                    espLoops[target.Name] = RunService.Heartbeat:Connect(function()
                        if root.Parent and marker.Parent then
                            marker.CFrame = root.CFrame
                            local dist = math.floor((myRoot.Position - root.Position).Magnitude)
                            local hp = humanoid.Health > 0 and math.floor(humanoid.Health) or 0
                            label.Text = target.Name .. "\nHP: " .. hp .. " | Dist: " .. dist
                        end
                    end)
                end
            end
        end
    end)

    tpBtn.MouseButton1Click:Connect(function()
        local target = findPlayer(input.Text)
        if target and target.Character and LocalPlayer.Character then
            local myRoot = LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            local tRoot = target.Character:FindFirstChild("HumanoidRootPart")
            if myRoot and tRoot then
                myRoot.CFrame = tRoot.CFrame * CFrame.new(0, 0, -3)
            end
        end
    end)

    freezeBtn.MouseButton1Click:Connect(function()
        local target = findPlayer(input.Text)
        if target and target.Character then
            local root = target.Character:FindFirstChild("HumanoidRootPart")
            if root then
                if freezeLoops[target.Name] then
                    freezeLoops[target.Name]:Disconnect()
                    freezeLoops[target.Name] = nil
                else
                    local pos = root.Position
                    freezeLoops[target.Name] = RunService.Heartbeat:Connect(function()
                        if root.Parent then
                            root.Velocity = Vector3.new(0,0,0)
                            root.RotVelocity = Vector3.new(0,0,0)
                            root.CFrame = CFrame.new(pos)
                        end
                    end)
                end
            end
        end
    end)

    freezeMeBtn.MouseButton1Click:Connect(function()
        local char = LocalPlayer.Character
        if char then
            local root = char:FindFirstChild("HumanoidRootPart")
            if root then
                if isFrozen then
                    if freezeMeLoop then freezeMeLoop:Disconnect() end
                    isFrozen = false
                else
                    local pos = root.Position
                    freezeMeLoop = RunService.Heartbeat:Connect(function()
                        root.Velocity = Vector3.new(0,0,0)
                        root.RotVelocity = Vector3.new(0,0,0)
                        root.CFrame = CFrame.new(pos)
                    end)
                    isFrozen = true
                end
            end
        end
    end)

    speedBtn.MouseButton1Click:Connect(function()
        local char = LocalPlayer.Character
        if char then
            local humanoid = char:FindFirstChildOfClass("Humanoid")
            if humanoid then
                local val = tonumber(speedInput.Text)
                if val and val > 0 then
                    humanoid.WalkSpeed = val
                end
            end
        end
    end)
end)

print("Custom Hub با Bring All لود شد!")
