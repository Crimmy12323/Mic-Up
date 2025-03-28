local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
local Window = Rayfield:CreateWindow({
    Name = "Mic Up",
    Icon = 0, LoadingTitle = "Mic Up", 
    LoadingSubtitle = "Made with ❤️ by @fuckluau", 
    Theme = "Bloom",
    DisableRayfieldPrompts = false,
    DisableBuildWarnings = false,
    ConfigurationSaving = {Enabled = true,
    FolderName = nil, FileName = "Big Hub"},
    Discord = {Enabled = false, Invite = "noinvitelink",
    RememberJoins = true},
    KeySystem = false,
    KeySettings = {Title = "Untitled",
    Subtitle = "Key System",
    Note = "No method of obtaining the key is provided", 
    FileName = "Key", SaveKey = true,
    GrabKeyFromSite = false, Key = {"Hello"}}
})

local PlayerTab, AnimTab, BaseplateTab, VoiceTab, UITab = Window:CreateTab("Player", 6961018885), Window:CreateTab("Animations", 18290544015), Window:CreateTab("Baseplate", 4483364408), Window:CreateTab("Voice Chat", 4370317928), Window:CreateTab("UI", 4384400106)
local Players, LocalPlayer, Camera = game:GetService("Players"), game:GetService("Players").LocalPlayer, workspace.CurrentCamera

PlayerTab:CreateSection("Movement")

PlayerTab:CreateSlider({Name = "WalkSpeed Slider",
 Range = {0, 150}, Increment = 1,
 Suffix = " Studs",
 CurrentValue = 16,
 Flag = "WalkSpeedSlider",
 Callback = function(Value) LocalPlayer.Character.Humanoid.WalkSpeed = Value end})
 PlayerTab:CreateSlider({Name = "JumpPower Slider",
 Range = {0, 150}, Increment = 1,
 Suffix = " JumpPower",
 CurrentValue = 50,
 Flag = "JumpPowerSlider",
 Callback = function(Value) LocalPlayer.Character.Humanoid.JumpPower = Value end})

PlayerTab:CreateSection("Wanking Stuff")

PlayerTab:CreateButton({Name = "Jerk Off Tool",
 Callback = function() loadstring(game:HttpGet("https://pastefy.app/YZoglOyJ/raw"))() end})

BaseplateTab:CreateSection("Baseplate Customization")

BaseplateTab:CreateToggle({
    Name = "Baseplate Expander",
    CurrentValue = false,
    Flag = "Toggle1",
    Callback = function(Value)
        if Value then
            local newBaseplate = Instance.new("Part")
            newBaseplate.Name = "ExpandedBaseplate"
            newBaseplate.Size = Vector3.new(100000, 16, 100000)
            newBaseplate.Anchored = true
            newBaseplate.Material = Enum.Material.Grass
            newBaseplate.Position = Vector3.new(65.99996948242188, -8, 72.49996948242188)
            local texture = Instance.new("Texture")
            texture.Texture = "rbxassetid://10442413242"
            texture.Face = Enum.NormalId.Top
            texture.StudsPerTileU = 10
            texture.StudsPerTileV = 10
            texture.Color3 = Color3.fromRGB(114, 229, 114)
            texture.Parent = newBaseplate
            newBaseplate.Parent = workspace
        else
            local existingBaseplate = workspace:FindFirstChild("ExpandedBaseplate")
            if existingBaseplate and type(existingBaseplate.Destroy) == "function" then
                existingBaseplate:Destroy()
            end
        end
    end
})

VoiceTab:CreateButton({Name = "VC Unban",
 Callback = function()
     game:GetService("VoiceChatService"):joinVoice()

 end})

PlayerTab:CreateSection("Player Stuff")
local function getPlayerNames()
    local names = {}
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer then table.insert(names, player.Name) end
    end
    return names
end

local PlayerDropdown = PlayerTab:CreateDropdown({
    Name = "Spy on Player",
    Options = getPlayerNames(),
    CurrentOption = {""},
    MultipleOptions = false,
    Flag = "Dropdown1",
    Callback = function(Options)
        local selectedPlayer = Players:FindFirstChild(Options[1])
        if selectedPlayer and selectedPlayer.Character and selectedPlayer.Character:FindFirstChild("HumanoidRootPart") then
            Camera.CameraSubject = selectedPlayer.Character.HumanoidRootPart
            Camera.CFrame = selectedPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0, 5, -10)
        end
    end
})

-- Function to refresh the dropdown options every 10 seconds
local function refreshDropdown()
    while true do
        if PlayerDropdown and type(PlayerDropdown.SetOptions) == "function" then
            PlayerDropdown:SetOptions(getPlayerNames())
        end
        wait(10) -- Wait for 10 seconds before refreshing again
    end
end

-- Start the refresh loop
task.spawn(refreshDropdown)

PlayerTab:CreateButton({Name = "Stop Spying",
 Callback = function()
    Camera.CameraSubject = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
    Camera.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0, 5, -10)
end})

Players.PlayerAdded:Connect(function()
    if PlayerDropdown and type(PlayerDropdown.SetOptions) == "function" then
        PlayerDropdown:SetOptions(getPlayerNames())
    end
end)

Players.PlayerRemoving:Connect(function()
    if PlayerDropdown and type(PlayerDropdown.SetOptions) == "function" then
        PlayerDropdown:SetOptions(getPlayerNames())
    end
end)

UITab:CreateSection("Themes")
local themes = {"Default", "Amber Glow", "Amyethyst", "Bloom", "Green", "Light", "Ocean", "Serenity"}
for _, theme in ipairs(themes) do
    UITab:CreateButton({Name = theme, Callback = function() Window.ModifyTheme(theme) end})
end

PlayerTab:CreateButton({
    Name = "Invisibility",
    Callback = function()
        local InvisibilitySettings = {TransparentClone = true,
        QuickMode = true,
        ChatNotifier = true}
        local lplr, char, oldChar, cooldown = game.Players.LocalPlayer,
        game.Players.LocalPlayer.Character, nil, false
        char.Archivable = true
        local UserInputService = game:GetService("UserInputService")

        local function createPlatform()
            local platform = Instance.new("Part")
            platform.Size = Vector3.new(10, 1, 10)
            platform.Position = Vector3.new(0, 10000, 0)
            platform.Anchored = true
            platform.Parent = workspace
            return platform
        end

        local function notify(message)
            if InvisibilitySettings.ChatNotifier then
                game.TextChatService.ChatInputBarConfiguration.TargetTextChannel:DisplaySystemMessage(message)
            end
        end

        local function activateInvisibility()
            if not char or not char:FindFirstChild("HumanoidRootPart") then return end
            oldChar = char
            local oldCFrame = char:GetPivot()
            local humanoidRootPart = oldChar:FindFirstChild("HumanoidRootPart")
            if humanoidRootPart then
                humanoidRootPart.CFrame = createPlatform().CFrame + Vector3.new(0, 3, 0)
                humanoidRootPart.Anchored = true
            else
                return
            end
            task.wait(InvisibilitySettings.QuickMode and .001 or .001)
            local clone = char:Clone()
            clone.Parent = workspace
            lplr.Character = clone
            workspace.CurrentCamera.CameraSubject = clone:FindFirstChildOfClass("Humanoid")
            local cloneHumanoidRootPart = clone:FindFirstChild("HumanoidRootPart")
            if cloneHumanoidRootPart then
                cloneHumanoidRootPart.CFrame = oldCFrame
                cloneHumanoidRootPart.Anchored = false
            else
                return
            end
            if InvisibilitySettings.TransparentClone then
                for _, part in ipairs(clone:GetDescendants()) do
                    if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
                        part.Transparency = 0.5
                    end
                end
            end
            if clone:FindFirstChild("Animate") then
                clone.Animate.Disabled = true
                task.wait()
                clone.Animate.Disabled = false
            end
            clone:FindFirstChildOfClass("Humanoid").DisplayName = clone.Name..""
            notify("Invisibility | You are now invisible! Press F to return normal")
            char = clone
            char:FindFirstChildOfClass("Humanoid").Died:Connect(function() deactivateInvisibility() end)
        end

        local function deactivateInvisibility()
            notify("Invisibility |You are now visible!")
            if oldChar then
                local clonePos = char and char:GetPivot() or CFrame.new(0, 0, 0)
                if char then char:Destroy() end
                if oldChar:FindFirstChildOfClass("Humanoid") then
                    workspace.CurrentCamera.CameraSubject = oldChar:FindFirstChildOfClass("Humanoid")
                end
                if oldChar:FindFirstChild("HumanoidRootPart") then
                    oldChar:FindFirstChild("HumanoidRootPart").Anchored = false
                end
                lplr.Character = oldChar
                lplr.Character:PivotTo(clonePos)
                char, oldChar = lplr.Character, nil
            end
        end

        local function onKeyPress(input, gameProcessed)
            if gameProcessed or cooldown then return end
            if input.KeyCode == Enum.KeyCode.F then
                if invisibilityActive then
                    deactivateInvisibility()
                else
                    activateInvisibility()
                end
                invisibilityActive = not invisibilityActive
                cooldown = true
                task.wait(1)
                cooldown = false
            end
        end

        UserInputService.InputBegan:Connect(onKeyPress)
    end
})

-- Invis End

local Section = AnimTab:CreateSection("Animation Loader")

local Button = AnimTab:CreateButton({
    Name = "Load FE Animation Loader",
    Callback = function()
        local TweenService = game:GetService("TweenService")
local Player = game:GetService("Players").LocalPlayer
local AlreadyEmoting = false
local UserInputService = game:GetService("UserInputService")
function Emote(danceid)
local char = Player.Character
local morph = game.Players:CreateHumanoidModelFromDescription(Player.Character:FindFirstChild("Humanoid"):FindFirstChild("HumanoidDescription"), Enum.HumanoidRigType.R15)
game:GetService("ReplicatedStorage"):WaitForChild("RagdollEvent"):FireServer()
pcall(function()
    settings().Physics.PhysicsEnvironmentalThrottle = Enum.EnvironmentalPhysicsThrottle.Enabled
end)
settings().Physics.AllowSleep = false
for _,inst in pairs(char.Humanoid:GetChildren()) do
    if inst:IsA("NumberValue") then
        morph:WaitForChild("Humanoid"):WaitForChild(inst.Name).Value = inst.Value
    end
end
morph:PivotTo(Player.Character:GetPivot())
morph.Name = Player.Name
Player.Character = morph
morph.Parent = workspace
game:GetService("StarterGui"):FindFirstChild("Menu"):Clone().Parent = Player.PlayerGui
spawn(function()
    repeat task.wait() until char.Humanoid.Health == 0 AlreadyEmoting = false
end)
game:GetService("UserInputService").InputBegan:Connect(function(key,bp)
    if not bp and morph.Parent ~= nil and key.KeyCode == Enum.KeyCode.R then
        morph.Humanoid.Health = 0
        AlreadyEmoting = false
        wait(.1)
        game:GetService("StarterGui"):FindFirstChild("Menu"):Clone().Parent = Player.PlayerGui
        game:GetService("ReplicatedStorage"):WaitForChild("UnragdollEvent"):FireServer()
    end
end)
for i,v in pairs(morph:GetDescendants()) do
    if v:IsA("Decal") or v:IsA("BasePart") then
        v.Transparency = 1
        if v:IsA("BasePart") then
            v.CanCollide = false
        end
    end
end

spawn(function()
repeat game:GetService("RunService").Heartbeat:wait()
        for _, v in pairs(game:GetService("Players"):GetPlayers()) do
            if v ~= game:GetService("Players").LocalPlayer then
                sethiddenproperty(v, "MaximumSimulationRadius", 0.1)
                sethiddenproperty(v, "SimulationRadius", 0)
            end
        end

        sethiddenproperty(game:GetService("Players").LocalPlayer, "MaximumSimulationRadius", math.huge)
        sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
    until morph.Humanoid.Health == 0
end)
spawn(function()
    repeat 
    

        for i,v in pairs(char:GetDescendants()) do
            if v:IsA("BasePart") then
                v.CanCollide = false
                v.Velocity = Vector3.new(0,0,0)
            end
        end
        for i,v in pairs(char:GetChildren()) do
            if v:IsA("BasePart") then
                v.CFrame = morph[tostring(v)].CFrame
            end
        end
        game:GetService("RunService").Heartbeat:Wait()

    until morph:WaitForChild("Humanoid").Health == 0
    Player.Character = char
    workspace.CurrentCamera.CameraSubject = char.Humanoid
    morph:Destroy()
end)
local Frame = (60)
local chr = game.Players.LocalPlayer.Character
Service =
    setmetatable(
    {
        Get = function(Self, Serv)
            if Service[Serv] then
                return Service[Serv]
            end
            local S = game:GetService(Serv)
            if S then
                Service[Serv] = S
            end
            return S
        end
    },
    {
        __index = function(Self, Index)
            local S = game:GetService(Index)
            if S then
                Service[Index] = S
            end
            return S
        end
    }
)

local LP = Service["Players"].LocalPlayer
local Char = LP["Character"]
local Torso, Root, Humanoid = Char["UpperTorso"], Char["HumanoidRootPart"], Char["Humanoid"]
local TService, UIS = Service["TweenService"], Service["UserInputService"]

coroutine.wrap(
    function()
        Root["Anchored"] = true
        wait(.8)
        Root["Anchored"] = false
    end
)()

local Create = function(Obj, Parent)
    local I = Instance.new(Obj)
    I["Parent"] = Parent
    return I
end

local Contains = function(Table, KV)
    for K, V in next, Table do
        if rawequal(KV, K) or rawequal(KV, V) then
            return true
        end
    end
    return false
end

local PoseToCF = function(Pose, Motor)
    return (Motor["Part0"].CFrame * Motor["C0"] * Pose["CFrame"] * Motor["C1"]:Inverse()):ToObjectSpace(
        Motor["Part0"].CFrame
    )
end

local Joints = {
    ["LeftHand"] = game.Players.LocalPlayer.Character.LeftHand["LeftWrist"],
    ["LeftLowerArm"] = chr.LeftLowerArm["LeftElbow"],
    ["LeftUpperArm"] = chr.LeftUpperArm["LeftShoulder"],
    ["RightHand"] = chr.RightHand["RightWrist"],
    ["RightLowerArm"] = chr.RightLowerArm["RightElbow"],
    ["RightUpperArm"] = chr.RightUpperArm["RightShoulder"],
    ["UpperTorso"] = chr.UpperTorso["Waist"],
    ["LeftFoot"] = chr.LeftFoot["LeftAnkle"],
    ["LeftLowerLeg"] = chr.LeftLowerLeg["LeftKnee"],
    ["LeftUpperLeg"] = chr.LeftUpperLeg["LeftHip"],
    ["RightFoot"] = chr.RightFoot["RightAnkle"],
    ["RightLowerLeg"] = chr.RightLowerLeg["RightKnee"],
    ["RightUpperLeg"] = chr.RightUpperLeg["RightHip"],
    ["LowerTorso"] = chr.LowerTorso["Root"],
    ["Head"] = chr.Head["Neck"]

}

for K, V in next, Char:GetChildren() do
    if V:IsA("BasePart") then
        coroutine.wrap(
            function()
                repeat
                    V["CanCollide"] = false
                    Service["RunService"].Stepped:Wait()
                until Humanoid["Health"] < 1
            end
        )()
    end
end

for K, V in next, Joints do
    local AP, AO, A0, A1 =
        Create("AlignPosition", V["Part1"]),
        Create("AlignOrientation", V["Part1"]),
        Create("Attachment", V["Part1"]),
        Create("Attachment", V["Part0"])
    AP["RigidityEnabled"] = true
    AO["RigidityEnabled"] = true
    AP["Attachment0"] = A0
    AP["Attachment1"] = A1
    AO["Attachment0"] = A0
    AO["Attachment1"] = A1
    A0["Name"] = "CFAttachment0"
    A1["Name"] = "CFAttachment1"
    A0["CFrame"] = V["C1"] * V["C0"]:Inverse()
    V:Remove()
end

local Edit = function(Part, Value, Duration, Style, Direction)
    Style = Style or "Enum.EasingStyle.Linear"
    Direction = Direction or "Enum.EasingDirection.In"
    local Attachment = Part:FindFirstChild("CFAttachment0")
    if Attachment ~= nil then
        TService:Create(
            Attachment,
            TweenInfo.new(
                Duration,
                Enum["EasingStyle"][tostring(Style):split(".")[3]],
                Enum["EasingDirection"][tostring(Direction):split(".")[3]],
                0,
                false,
                0
            ),
            {CFrame = Value}
        ):Play()
    end
end

if not Service["RunService"]:FindFirstChild("Delta") then
    local Delta = Create("BindableEvent", Service["RunService"])
    Delta["Name"] = "Delta"
    local A, B = 0, tick()
    Service["RunService"].Delta:Fire()
    Service["RunService"].Heartbeat:Connect(
        function(C, D)
            A = A + C
            if A >= (1 / Frame) then
                for I = 1, math.floor(A / (1 / Frame)) do
                    Service["RunService"].Delta:Fire()
                end
                B = tick()
                A = A - (1 / Frame) * math.floor(A / (1 / Frame))
            end
        end
    )
end

coroutine.wrap(
    function()
        Humanoid["Died"]:Wait()
        for K, V in next, Char:GetDescendants() do
            if V["Name"]:match("Align") then
                V:Destroy()
            end
        end
    end
)()

local PreloadAnimation = function(AssetId)
    local Sequence = game:GetObjects("rbxassetid://" .. AssetId)[1]
    assert(Sequence:IsA("KeyframeSequence"), "Instance is not a KeyframeSequence.")
    wait(.06)
    local Class = {}
    Class["Speed"] = 1
    local Yield = function(Seconds)
        local Time = Seconds * (Frame + Sequence:GetKeyframes()[#Sequence:GetKeyframes()].Time)
        for I = 1, Time, Class["Speed"] do
            Service["RunService"].Delta["Event"]:Wait()
        end
    end
    Class["Stopped"] = false
    Class["Complete"] = Instance.new("BindableEvent")
    Class["Play"] = function()
    Class["Stopped"] = false
    coroutine.wrap(function()
        repeat
            local keyframes = Sequence:GetKeyframes()
            for K = 1, #keyframes do
                local K0 = keyframes[K - 1]
                local K1 = keyframes[K]
                local K2 = keyframes[K + 1]
                
                if not Class["Stopped"] and Humanoid.Health > 0 then
                    if K0 then
                        Yield(K1.Time - K0.Time)
                    end

                    coroutine.wrap(function()
                        for _, Pose in ipairs(K1:GetDescendants()) do
                            if Contains(Joints, Pose.Name) and Char:FindFirstChild(Pose.Name) then
                                local Duration = (K2 and (K2.Time - K1.Time) / Class["Speed"]) or 0.5
                                Edit(
                                    Char[Pose.Name],
                                    PoseToCF(Pose, Joints[Pose.Name]),
                                    Duration,
                                    Pose.EasingStyle,
                                    Pose.EasingDirection
                                )
                            end
                        end
                    end)()
                end
            end

            -- Fire the 'Complete' event after each full cycle
            Class["Complete"]:Fire()
        until not Sequence.Loop or Class["Stopped"] or Humanoid.Health < 1
    end)()
end

    Class["Stop"] = function()
        Class["Stopped"] = true
    end
    Class["Reset"] = function()
        coroutine.wrap(
            function()
                wait(.02)
                assert(Class["Stopped"], "Track Must Be Stopped First!")
                for K, V in next, Joints do
                    local Part = Char[K]
                    if Part ~= nil then
                        local Attachment = Part:FindFirstChild("CFAttachment0")
                        if Attachment ~= nil then
                            Attachment["CFrame"] = V["C1"] * V["C0"]:Inverse()
                        end
                    end
                end
            end
        )()
    end
    return Class
end

Humanoid.WalkSpeed = 16

local Animation = PreloadAnimation(danceid)
wait(1)
Mouse = LP:GetMouse()
--[[local StopAll = function()
    for K, V in next, Anims do
        if V["Stopped"] ~= true then
            V:Stop()
        end
    end
end]]

Animation:Play()

end

local G2L = {};

G2L["1"] = Instance.new("ScreenGui", game.CoreGui);
G2L["1"]["ZIndexBehavior"] = Enum.ZIndexBehavior.Sibling;


G2L["2"] = Instance.new("Frame", G2L["1"]);
G2L["2"]["BorderSizePixel"] = 0;
G2L["2"]["BackgroundColor3"] = Color3.fromRGB(30, 30, 30);
G2L["2"]["Size"] = UDim2.new(0, 417, 0, 213);
G2L["2"]["Position"] = UDim2.new(0.34205, 0, 0.3593, 0);
G2L["2"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["2"]["Name"] = [[UI]];


G2L["3"] = Instance.new("UICorner", G2L["2"]);

G2L["4"] = Instance.new("ImageLabel", G2L["2"]);
G2L["4"]["ZIndex"] = -5;
G2L["4"]["SliceCenter"] = Rect.new(85, 85, 427, 427);
G2L["4"]["ScaleType"] = Enum.ScaleType.Slice;
G2L["4"]["ImageTransparency"] = 0.5;
G2L["4"]["AnchorPoint"] = Vector2.new(0.5, 0.5);
G2L["4"]["Image"] = [[rbxassetid://12817494724]];
G2L["4"]["Size"] = UDim2.new(1, 142, 1, 142);
G2L["4"]["BackgroundTransparency"] = 1;
G2L["4"]["Name"] = [[FrameShadow]];
G2L["4"]["Position"] = UDim2.new(0.5, 0, 0.5, 2);

G2L["5"] = Instance.new("TextLabel", G2L["2"]);
G2L["5"]["TextWrapped"] = true;
G2L["5"]["BorderSizePixel"] = 0;
G2L["5"]["TextScaled"] = true;
G2L["5"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["5"]["TextSize"] = 14;
G2L["5"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["5"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["5"]["BackgroundTransparency"] = 1;
G2L["5"]["Size"] = UDim2.new(0, 256, 0, 33);
G2L["5"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["5"]["Text"] = [[Animation ID Loader | Mic UP ]];
G2L["5"]["Name"] = [[Title]];
G2L["5"]["Position"] = UDim2.new(0.19185, 0, 0, 0);

G2L["6"] = Instance.new("Frame", G2L["2"]);
G2L["6"]["BorderSizePixel"] = 0;
G2L["6"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["6"]["Size"] = UDim2.new(0, 256, 0, 1);
G2L["6"]["Position"] = UDim2.new(0.19185, 0, 0.14, 0);
G2L["6"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["6"]["Name"] = [[Divider]];

G2L["7"] = Instance.new("Frame", G2L["2"]);
G2L["7"]["BorderSizePixel"] = 0;
G2L["7"]["BackgroundColor3"] = Color3.fromRGB(23, 23, 23);
G2L["7"]["Size"] = UDim2.new(0, 396, 0, 36);
G2L["7"]["Position"] = UDim2.new(0.02398, 0, 0.21127, 0);
G2L["7"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["7"]["Name"] = [[TextBox Holder]];


G2L["8"] = Instance.new("UICorner", G2L["7"]);

G2L["9"] = Instance.new("UIStroke", G2L["7"]);
G2L["9"]["Color"] = Color3.fromRGB(66, 66, 66);

G2L["a"] = Instance.new("TextBox", G2L["7"]);
G2L["a"]["CursorPosition"] = -1;
G2L["a"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["a"]["PlaceholderColor3"] = Color3.fromRGB(133, 133, 133);
G2L["a"]["BorderSizePixel"] = 0;
G2L["a"]["TextSize"] = 14;
G2L["a"]["Name"] = [[Main thingy]];
G2L["a"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["a"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["a"]["RichText"] = true;
G2L["a"]["ClipsDescendants"] = true;
G2L["a"]["PlaceholderText"] = [[Insert Animation ID]];
G2L["a"]["Size"] = UDim2.new(0, 396, 0, 36);
G2L["a"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["a"]["Text"] = [[]];
G2L["a"]["BackgroundTransparency"] = 1;

G2L["a"].FocusLost:Connect(function()
	if AlreadyEmoting == true then AlreadyEmoting = false
		Player.Character.Humanoid.Health = 0
		wait(.1)
	end
	AlreadyEmoting = true
	local ID = G2L["a"].Text
	G2L["a"].Text = ""
	Emote(ID)
end)


G2L["b"] = Instance.new("Frame", G2L["2"]);
G2L["b"]["BorderSizePixel"] = 0;
G2L["b"]["BackgroundColor3"] = Color3.fromRGB(23, 23, 23);
G2L["b"]["Size"] = UDim2.new(0, 396, 0, 86);
G2L["b"]["Position"] = UDim2.new(0.02398, 0, 0.43662, 0);
G2L["b"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["b"]["Name"] = [[Infomation]];

G2L["c"] = Instance.new("UICorner", G2L["b"]);

G2L["d"] = Instance.new("UIStroke", G2L["b"]);
G2L["d"]["Color"] = Color3.fromRGB(255, 255, 255);

G2L["e"] = Instance.new("ImageLabel", G2L["b"]);
G2L["e"]["BorderSizePixel"] = 0;
G2L["e"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["e"]["Image"] = [[rbxthumb://type=AvatarHeadShot&id=]]..game:GetService("Players").LocalPlayer.UserId.."&w=420&h=420";
G2L["e"]["Size"] = UDim2.new(0, 64, 0, 64);
G2L["e"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["e"]["BackgroundTransparency"] = 1;
G2L["e"]["Position"] = UDim2.new(0.0404, 0, 0.12791, 0);

G2L["f"] = Instance.new("UICorner", G2L["e"]);
G2L["f"]["CornerRadius"] = UDim.new(0, 90000);

G2L["10"] = Instance.new("UIStroke", G2L["e"]);
G2L["10"]["Color"] = Color3.fromRGB(255, 255, 255);

G2L["11"] = Instance.new("TextLabel", G2L["b"]);
G2L["11"]["BorderSizePixel"] = 0;
G2L["11"]["TextXAlignment"] = Enum.TextXAlignment.Left;
G2L["11"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["11"]["TextSize"] = 14;
G2L["11"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["11"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["11"]["BackgroundTransparency"] = 1;
G2L["11"]["Size"] = UDim2.new(0, 266, 0, 18);
G2L["11"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["11"]["Text"] = [[Name: ]]..game:GetService("Players").LocalPlayer.DisplayName.."( "..tostring(game:GetService("Players").LocalPlayer).." )";
G2L["11"]["Name"] = [[Name]];
G2L["11"]["Position"] = UDim2.new(0.2702, 0, 0.12791, 0);

G2L["12"] = Instance.new("TextLabel", G2L["b"]);
G2L["12"]["BorderSizePixel"] = 0;
G2L["12"]["TextXAlignment"] = Enum.TextXAlignment.Left;
G2L["12"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["12"]["TextSize"] = 14;
G2L["12"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["12"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["12"]["BackgroundTransparency"] = 1;
G2L["12"]["Size"] = UDim2.new(0, 266, 0, 18);
G2L["12"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["12"]["Text"] = [[UserID: ]]..game:GetService("Players").LocalPlayer.UserId;
G2L["12"]["Name"] = [[USERID]];
G2L["12"]["Position"] = UDim2.new(0.2702, 0, 0.33721, 0);

G2L["13"] = Instance.new("TextLabel", G2L["b"]);
G2L["13"]["BorderSizePixel"] = 0;
G2L["13"]["TextXAlignment"] = Enum.TextXAlignment.Left;
G2L["13"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["13"]["TextSize"] = 14;
G2L["13"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["13"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["13"]["BackgroundTransparency"] = 1;
G2L["13"]["Size"] = UDim2.new(0, 266, 0, 18);
G2L["13"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["13"]["Text"] = [[Account Age: ]]..game:GetService("Players").LocalPlayer.AccountAge.." day's";
G2L["13"]["Name"] = [[Age]];
G2L["13"]["Position"] = UDim2.new(0.2702, 0, 0.54651, 0);

G2L["14"] = Instance.new("TextLabel", G2L["b"]);
G2L["14"]["BorderSizePixel"] = 0;
G2L["14"]["TextXAlignment"] = Enum.TextXAlignment.Left;
G2L["14"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["14"]["TextSize"] = 14;
G2L["14"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["14"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["14"]["BackgroundTransparency"] = 1;
G2L["14"]["Size"] = UDim2.new(0, 266, 0, 18);
G2L["14"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["14"]["Text"] = [[Executor: ]]..identifyexecutor();
G2L["14"]["Name"] = [[Executor]];
G2L["14"]["Position"] = UDim2.new(0.2702, 0, 0.75581, 0);

G2L["15"] = Instance.new("TextLabel", G2L["2"]);
G2L["15"]["BorderSizePixel"] = 0;
G2L["15"]["TextXAlignment"] = Enum.TextXAlignment.Right;
G2L["15"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["15"]["TextSize"] = 14;
G2L["15"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["15"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["15"]["BackgroundTransparency"] = 1;
G2L["15"]["Size"] = UDim2.new(0, 200, 0, 22);
G2L["15"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["15"]["Text"] = [[Credits: 3itx / Sal (CommonUI)]];
G2L["15"]["Name"] = [[Credits]];
G2L["15"]["Position"] = UDim2.new(0.494, 0, 0.89671, 0);

G2L["16"] = Instance.new("TextLabel", G2L["2"]);
G2L["16"]["TextWrapped"] = true;
G2L["16"]["BorderSizePixel"] = 0;
G2L["16"]["TextXAlignment"] = Enum.TextXAlignment.Left;
G2L["16"]["ClipsDescendants"] = true;
G2L["16"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["16"]["TextSize"] = 14;
G2L["16"]["FontFace"] = Font.new([[rbxasset://fonts/families/SourceSansPro.json]], Enum.FontWeight.Bold, Enum.FontStyle.Normal);
G2L["16"]["TextColor3"] = Color3.fromRGB(255, 255, 255);
G2L["16"]["BackgroundTransparency"] = 1;
G2L["16"]["Size"] = UDim2.new(0, 200, 0, 15);
G2L["16"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["16"]["Text"] = [[MOTD: ]]..game:HttpGet("https://raw.githubusercontent.com/Just3itx/LOOOOOO/refs/heads/main/MOTD");
G2L["16"]["Name"] = [[MOTD]];
G2L["16"]["Position"] = UDim2.new(0.01439, 0, 0.92958, 0);

G2L["17"] = Instance.new("Frame", G2L["2"]);
G2L["17"]["BorderSizePixel"] = 0;
G2L["17"]["BackgroundColor3"] = Color3.fromRGB(255, 255, 255);
G2L["17"]["Size"] = UDim2.new(0, 417, 0, 33);
G2L["17"]["BorderColor3"] = Color3.fromRGB(0, 0, 0);
G2L["17"]["Name"] = [[DragFrame]];
G2L["17"]["BackgroundTransparency"] = 1;

function MakeDraggable(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil
	local TweenSpeed = 0.1  -- Speed of the tween effect

	local function Update(input)
		local Delta = input.Position - DragStart
		local targetPosition =
			UDim2.new(
				StartPosition.X.Scale,
				StartPosition.X.Offset + Delta.X,
				StartPosition.Y.Scale,
				StartPosition.Y.Offset + Delta.Y
			)
		
		local tween = TweenService:Create(object, TweenInfo.new(TweenSpeed, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), {Position = targetPosition})
		tween:Play()
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
				DragInput = input
			end
		end
	)

	game:GetService("UserInputService").InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end

MakeDraggable(G2L["17"], G2L["2"])

UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.Minus and not UserInputService:GetFocusedTextBox() then
        if G2L["2"] then
            G2L["2"]["Visible"] = not G2L["2"]["Visible"]
        else
            warn("G2L[2] is nil. Ensure it’s defined before toggling visibility.")
        end
    end
end)

game:GetService("RunService").RenderStepped:Connect(function(deltaTime)
    G2L["a"]["PlaceholderColor3"] = Color3.fromHSV(tick() * 0.1 % 1, 1, 1)
end)

    end,
 })

 local Divider = AnimTab:CreateDivider()

 local Label = AnimTab:CreateLabel("Random Anims", 106756897158809, Color3.fromRGB(255, 183, 197), false) -- Title, Icon, Color, IgnoreTheme

 local Button = AnimTab:CreateButton({
    Name = "Swastika ID",
    Callback = function()
        setclipboard("93170225110433")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Heil Hitler ID",
    Callback = function()
        setclipboard("93079733222935")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Goofy Hump ID",
    Callback = function()
        setclipboard("90394111093691")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Among Us ID",
    Callback = function()
        setclipboard("106571448976554")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Skibidi Toilet ID",
    Callback = function()
        setclipboard("118415982698053")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Crouch Walk ID",
    Callback = function()
        setclipboard("96685695645215")
    end,
 })

 local Label = AnimTab:CreateLabel("Emote Anims", 18754693229, Color3.fromRGB(255, 183, 197), false) -- Title, Icon, Color, IgnoreTheme

 local Button = AnimTab:CreateButton({
    Name = "Default Dance ID",
    Callback = function()
        setclipboard("134651738516658")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Take The L ID",
    Callback = function()
        setclipboard("133213000719063")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Orange Justice ID",
    Callback = function()
        setclipboard("134067833790406")
    end,
 })

 local Button = AnimTab:CreateButton({
    Name = "Hype ID",
    Callback = function()
        setclipboard("74907390263971")
    end,
 })
