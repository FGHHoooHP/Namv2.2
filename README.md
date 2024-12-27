warn("Anti AFK Actived")
local part = Instance.new("Part")
part.Size = Vector3.new(4, 1, 4)  -- ขนาดของบล็อก
part.Position = Vector3.new(3701, 9999, 1582)  -- ตำแหน่ง
part.Anchored = true  -- ทำให้บล็อกอยู่นิ่ง
part.Parent = workspace  -- เพิ่มบล็อกใน workspace


local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "XXX hub",
    SubTitle = "by XXX",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

--Fluent provides Lucide Icons https://lucide.dev/icons/ for the tabs, icons are optional
local Tabs = {
    Main = Window:AddTab({ Title = "Main", Icon = "" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local Options = Fluent.Options

do

local Toggle = Tabs.Main:AddToggle("MyToggle", {Title = "Auto Farm", Default = false})

Toggle:OnChanged(function(state)

_G.Autoitem = state
_G.AutoPlayers = state
_G.AutoSell = state
_G.AintAFK = state
_G.animationTrack = state
_G.AutoSell = state

if _G.Autoitem then
    task.spawn(function()
        while _G.Autoitem do
            task.wait(1)  -- เช็คทุก 1 วินาที

local function moveFarmItems(farmPath, offset)
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

    local farmItems = farmPath:GetChildren()
    for i = 1, math.min(#farmItems, 1000) do
        local item = farmItems[i]
        local targetPosition = humanoidRootPart.CFrame + offset

        if item:IsA("Model") then
            item:PivotTo(targetPosition)
        elseif item:IsA("BasePart") then
            item.CFrame = targetPosition
        end
    end
end


moveFarmItems(workspace.Farm.Apple.FarmItem, Vector3.new(0, 0, 0))

moveFarmItems(workspace.Farm.Banana.FarmItem, Vector3.new(0, 0, 0))

moveFarmItems(workspace.Farm.Cabbage.FarmItem, Vector3.new(0, 0, 0))

moveFarmItems(workspace.Farm.Strawberry.FarmItem, Vector3.new(0, 0, 0))

moveFarmItems(workspace.Farm.Meat.FarmItem, Vector3.new(0, 0, 0))

moveFarmItems(workspace.Farm.Orange.FarmItem, Vector3.new(0, 0, 0))

moveFarmItems(workspace.Farm.Watermelon.FarmItem, Vector3.new(0, 0, 0))
      end
   end)
end



if _G.AutoPlayers then
    task.spawn(function()
        while _G.AutoPlayers do
            task.wait(0)  -- เช็คทุก 1 วินาที

game.Players.LocalPlayer.Character:MoveTo(Vector3.new(3674, 4, 2653))
wait(0.2)
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(3220, 4, 329))
wait(0.2)
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(786, 4, -2831))
wait(0.2)
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(-554, 173, -1065))
wait(0.2)
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(-2707, 5, -1304))
wait(0.2)
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(-4198, 4, -111))
wait(0.2)
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(-6737, 4, 2943))
wait(0.2)
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(3701, 10005, 1582))
wait(0.2)
_G.AutoPlayers = false
      end
   end)
end







if _G.AutoSell then
    task.spawn(function()
        while _G.AutoSell do
            task.wait(1)  -- Delay between selling actions to prevent overloading the server
            
            local items = {"Apple", "Banana", "Cabbage", "Strawberry", "Meat", "Orange", "Watermelon"}
            local price = 60  -- Ensure price is set as a number for transaction

            for _, item in ipairs(items) do
                local args = {
                    [1] = "Sell",
                    [2] = item,
                    [3] = price
                }
                game:GetService("ReplicatedStorage"):WaitForChild("Remote"):WaitForChild("Economy"):FireServer(unpack(args))
            end
        end
    end)
end



if _G.AintAFK then
    task.spawn(function()
        local VirtualUser = game:GetService("VirtualUser")
        
        -- รันลูปเพื่อทำงานทุก 5 วินาที
        while _G.AintAFK do
            -- จำลองการกดปุ่มเมาส์ขวา
            VirtualUser:CaptureController()
            VirtualUser:ClickButton2(Vector2.new())

            -- รอ 5 วินาทีก่อนทำงานซ้ำ
            task.wait(5)
        end
    end)
end
end)
end




if _G.animationTrack then
    task.spawn(function()
        while _G.animationTrack do
            task.wait(0)  -- เช็คทุก 1 วินาที

local humanoid = game.Players.LocalPlayer.Character:WaitForChild("Humanoid")
local animator = humanoid:WaitForChild("Animator")

-- หยุดการเล่นอนิเมชันทั้งหมด
for _, animationTrack in pairs(animator:GetPlayingAnimationTracks()) do
    animationTrack:Stop()
end
end
end)
end

local Toggle = Tabs.Main:AddToggle("MyToggle", {Title = "CheckAdmin", Default = true})

Toggle:OnChanged(function(state)

_G.Checkadmin = state

if _G.Checkadmin then
    task.spawn(function()
        while _G.Checkadmin do
            task.wait(1)  -- เช็คทุก 1 วินาที


local playerNames = {"may65448", "BossFriends9", "thong2821", "Sky_Alinsip"}

for _, playerName in ipairs(playerNames) do
    local player = game:GetService("Players"):FindFirstChild(playerName)
    
    if player then
game.Players.LocalPlayer:Kick("เเอดมินมาาาาาาาาา!!!!!!!!")


    end
end
end
end)
end
end)



local Toggle = Tabs.Main:AddToggle("MyToggle", {Title = "AutoEat", Default = true})

local isAutoEating = false  -- Variable to track if the loop is running

Toggle:OnChanged(function(state)
    _G.Hunger = state

    if _G.Hunger and not isAutoEating then
        isAutoEating = true
        task.spawn(function()
            while _G.Hunger do
                task.wait(1)  -- เช็คทุก 1 วินาที

                -- เช็คค่าความหิว
                if game:GetService("Players").LocalPlayer.Status.Hunger.Value < 50 then
                    local args = {
                        [1] = "Use",
                        [2] = "Bread"
                    }

                    game:GetService("ReplicatedStorage"):WaitForChild("Remote"):WaitForChild("Inventory"):FireServer(unpack(args))
                end

                -- เช็คค่าความกระหายน้ำ
                if game:GetService("Players").LocalPlayer.Status.Thirsty.Value < 50 then
                    local args = {
                        [1] = "Use",
                        [2] = "Water"
                    }

                    game:GetService("ReplicatedStorage"):WaitForChild("Remote"):WaitForChild("Inventory"):FireServer(unpack(args))
                end
            end
        end)
    elseif not _G.Hunger and isAutoEating then
        isAutoEating = false
    end
end)



