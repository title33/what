---Close UI
local openshit = Instance.new("ScreenGui")
local mainopen = Instance.new("TextButton")
local mainopens = Instance.new("UICorner")
local loki = Instance.new("ImageLabel")
local posto = Instance.new("UIStroke")

openshit.Name = "openshit"
openshit.Parent = game.CoreGui
openshit.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local UICorner_11 = Instance.new("UICorner")
local UICorner_12 = Instance.new("UICorner")

local buttonframe = Instance.new("Frame")

local ImageButton_2 = Instance.new("ImageButton")

buttonframe.Parent = openshit
buttonframe.Name = "buttonframe"
buttonframe.BackgroundColor3 = Color3.fromRGB(0,0,0)
buttonframe.BorderColor3 = Color3.fromRGB(0, 0, 0)
buttonframe.BackgroundTransparency = 1.000
buttonframe.BorderSizePixel = 0
buttonframe.Position = UDim2.new(0.00790273491, 0, 0.233524337, 0)
buttonframe.Size = UDim2.new(0, 51, 0, 50)

UICorner_11.Parent = buttonframe
UICorner_12.Parent = ImageButton_2

ImageButton_2.Parent = buttonframe
ImageButton_2.BackgroundColor3 = Color3.fromRGB(86,255,255)
ImageButton_2.BorderColor3 = Color3.fromRGB(86,255,255)
ImageButton_2.BackgroundTransparency = 1.000
ImageButton_2.BorderSizePixel = 0
ImageButton_2.Position = UDim2.new(0.0242961459, 0, 0.0168576241, 0)
ImageButton_2.Size = UDim2.new(0, 49, 0, 48)
ImageButton_2.Image = "rbxassetid://14491200389"
ImageButton_2.MouseButton1Click:Connect(function()
game:GetService("VirtualInputManager"):SendKeyEvent(true,Enum.KeyCode.End,false,game)
end)

mainopens.Parent = mainopen
 
 loki.Name = "loki"
 loki.Parent = mainopen
 loki.BackgroundColor3 = Color3.fromRGB(224,224,224)
 loki.BackgroundTransparency = 1.000
 loki.Position = UDim2.new(-0.0529999994, 0, -0.244000003, 0)
 loki.Size = UDim2.new(0, 69, 0, 62)
 loki.Image = "rbxassetid://14491200389"
 
 posto.Name = "posto"
 posto.Parent = mainopen
 posto.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 posto.Color = Color3.fromRGB(224,224,224)
 posto.LineJoinMode = Enum.LineJoinMode.Round
 posto.Thickness = 1
 posto.Transparency = 0
 posto.Enabled = true
 posto.Archivable = true
 
 local UserInputService = game:GetService("UserInputService")
 local TweenService = game:GetService("TweenService")
 
 local function MakeDraggable(topbarobject, object)
 local Dragging = nil
 local DragInput = nil
 local DragStart = nil
 local StartPosition = nil
 
 local function Update(input)
 local Delta = input.Position - DragStart
 local pos = UDim2.new(StartPosition.X.Scale, StartPosition.X.Offset + Delta.X, StartPosition.Y.Scale, StartPosition.Y.Offset + Delta.Y)
 local Tween = TweenService:Create(object, TweenInfo.new(0.15), {
  Position = pos
 })
 Tween:Play()
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
  if
   input.UserInputType == Enum.UserInputType.MouseMovement or
  input.UserInputType == Enum.UserInputType.Touch
  then
  DragInput = input
  end
  end
 )
 
 UserInputService.InputChanged:Connect(
  function(input)
  if input == DragInput and Dragging then
  Update(input)
  end
  end
 )
 end
 





local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/title33/SaveManager/main/README.md"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "Xylo Hub",
    SubTitle = "by Sky",
    TabWidth = 160,
    Size = UDim2.fromOffset(530, 340),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

--Fluent provides Lucide Icons https://lucide.dev/icons/ for the tabs, icons are optional
local Tabs = {
    General = Window:AddTab({ Title = "General", Icon = "home" }),
    Stats = Window:AddTab({ Title = "Stats", Icon = "bar-chart" }),
    Skil = Window:AddTab({ Title = "Skil", Icon = "battery-charging" }),
    Fruit = Window:AddTab({ Title = "Fruit", Icon = "apple" }),
    TP = Window:AddTab({ Title = "TP", Icon = "chevrons-right" }),
    Shop = Window:AddTab({ Title = " Shop", Icon = "shopping-cart" }),
    Inventory = Window:AddTab({ Title = "Inventory", Icon = "scroll" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local Options = Fluent.Options

function No()
    for i, v in ipairs(workspace.Lives:GetChildren()) do
        if not game:GetService("Players"):GetPlayerFromCharacter(v) then -- if not player then
            local cleanedName = string.gsub(v.Name, "%d+$", "")
            v.Name = tostring(cleanedName)
        end
    end

    workspace.Lives.ChildAdded:Connect(function(model)
        wait()
        if not game:GetService("Players"):GetPlayerFromCharacter(model) then -- if not player then
            local cleanedName = string.gsub(model.Name, "%d+$", "")
            model.Name = cleanedName
        end
    end)
end

function TP(targetCFrame)
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = targetCFrame
end


Boss = {
 "None",
 "Natsu",
 "Choso",
 "Ichigo",
 "Killua",
 "Gojo [Unleashed]",
 "Sukuna [Half Power]",
 "Gojo",
 "Sukuna",
 "Shank",
 "Kashimo",
 "Artoria",
 "Bomb Man",
 "Sand Man",
 "Monkey King",
 "Bandit Leader"
}

local Farm = Tabs.General:AddSection("Farm")

local Dropdown = Tabs.General:AddDropdown("Boss", {
    Title = "Boss",
 Values = {"None", "Bandit", "Bandit Leader", "Clown Pirate", "Marine", "Monkey", "Monkey King", "Bomb Man", "Sand Man", "Snow Bandit", "Snow Bandit Leader"},
    Multi = false,
    Default = 1,
})

Dropdown:SetValue("None")

Dropdown:OnChanged(function(v)
    free = v
end)

local Toggle = Tabs.General:AddToggle("MyToggle", {Title = "Auto Farm Boss", Default = false })

Toggle:OnChanged(function(t)
 No()
_G.p = t

function A()
  game:GetService'VirtualUser':CaptureController()
game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
end

end)

Options.MyToggle:SetValue(false)

spawn(function()
    while wait() do
        pcall(function()
            if _G.p then
                for _, v in pairs(game:GetService("Workspace").Lives:GetDescendants()) do
                    if v.Name == free and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health >= 1 then
                        repeat
                            wait()
                            A()
                            v.HumanoidRootPart.Size = Vector3.new(10, 10, 10)
                            v.HumanoidRootPart.Transparency = 0.9
                            v.Humanoid.WalkSpeed = 0
                            v.Humanoid.JumpPower = 0
                            TP(v.HumanoidRootPart.CFrame * CFrame.new(0, 0, 5))
                        until not _G.p
                    end
                end
            end
        end)
    end
end)


function MonsSpawned(Mons)
   for _, v in pairs(game:GetService('Workspace').Lives:GetDescendants()) do
        if v.Name == Mons and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health >= 1 then
            return true
        end
    end
    return false
end

function FarmBoss(v)
    if v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health >= 1 then
        repeat
            No()
            wait()
            v.HumanoidRootPart.Size = Vector3.new(10, 10, 10)
            v.HumanoidRootPart.Transparency = 0.9
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 0, 7)
        until _G.eami == false or v.Humanoid.Health <= 0
    end
end

spawn(function()
    while wait() do
        pcall(function()
            if _G.eami then
                local MonNames = {
                    "Shadow",
                    "Gojo",
                    "Kashimo",
                    "Sukuna",
                    "Artoria",
                    "Uraume",
                    "Gojo [Unleashed]",
                    "Sukuna [Half Power]",
                    "Rimuru",
                    "Killua",
                    "Ichigo",
                    "Choso"
                }

                for _, v in pairs(game:GetService('Workspace').Lives:GetDescendants()) do
                    if table.find(MonNames, v.Name) then
                        FarmBoss(v)
                    end
                end
            end
        end)
    end
end)

local Toggle = Tabs.General:AddToggle("Auto Farm Boss [ETC]", { Title = "Auto Farm Boss [ETC]", Default = false })

Toggle:OnChanged(function(a)
    _G.eami = a
end)

local Weapon = Tabs.General:AddSection("Weapon")

local Weaponlist = {}
local Weapon = nil
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
    end

Tabs.General:AddDropdown("Weapon", {
        Title = "Weapon",
        Values = Weaponlist,
        Multi = false,
        Default = nil,
        Callback = function(v)
        _G.Weapon = v
       end
   })



     local Toggle = Tabs.General:AddToggle("Auto Equip", {Title = "Auto Equip", Default = false })
    Toggle:OnChanged(function(a)
    _G.AutoEquiped = a
    end)
    
spawn(function()
while wait() do
if _G.AutoEquiped then
pcall(function()
game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(_G.Weapon))
end)
end
end
end)    

    local Toggle = Tabs.General:AddToggle("Auto Attack", {Title = "Auto Attack", Default = false })
    Toggle:OnChanged(function(ah)
_G.Ato = ah
while _G.Ato do wait()
game:GetService'VirtualUser':CaptureController()
game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
end
    end)

local Chests = Tabs.General:AddSection("Chests")

    local Toggle = Tabs.General:AddToggle("Auto Chests", {Title = "Auto Chests", Default = false })
    Toggle:OnChanged(function(wow)
        _G.aa = wow
        while _G.aa do wait()
for i,v in pairs(game:GetService("Workspace").Chests:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
                end
            end
        end
    end)


local Stats = Tabs.Stats:AddSection("Stats")

local function SetupToggle(tabName, itemName, attribute)
    local Toggle = Tabs.Stats:AddToggle(tabName, {Title = itemName, Default = false })

    Toggle:OnChanged(function(a)
        _G[attribute] = a
    end)
    Options.MyToggle:SetValue(false)

    spawn(function()
        while wait(.1) do
            pcall(function()
                if _G[attribute] then
                    local args = {
                        [1] = itemName,
                        [2] = 1
                    }

                    game:GetService("ReplicatedStorage").Remotes.UpStats:FireServer(unpack(args))
                end
            end)
        end
    end)
end

local toggles = {
    {"Melee", "Melee", "AutoMelee"},
    {"Weapon", "Weapon", "AutoWeapon"},
    {"Defense", "Defense", "AutoDefense"},
    {"DemonFruit", "DemonFruit", "AutoDemonFruit"},
}

for _, toggleInfo in ipairs(toggles) do
    SetupToggle(unpack(toggleInfo))
end

local Skil = Tabs.Skil:AddSection("Auto Skil")

    local Toggle = Tabs.Skil:AddToggle("Auto Skil Z", {Title = "Auto Skil Z", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoZ = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoZ then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)
    


    local Toggle = Tabs.Skil:AddToggle("Auto Skil X", {Title = "Auto Skil X", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoX = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoX then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)


    local Toggle = Tabs.Skil:AddToggle("Auto Skil C", {Title = "Auto Skil C", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoC = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoC then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)
 


    local Toggle = Tabs.Skil:AddToggle("Auto Skil V", {Title = "Auto Skil V", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoV = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoV then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)

local Fruit = Tabs.Fruit:AddSection("Auto Random Fruit")

    local Toggle = Tabs.Fruit:AddToggle("Auto Random Fruit [Beli]", {Title = "Auto Random Fruit [Beli]", Default = false })
    Toggle:OnChanged(function(Random)
        _G.Fruit1 = Random 
        while _G. Fruit1 do wait()
for i,v in pairs(game:GetService("Workspace").Shop:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(790.203735, 35.5073013, 1201.40369, 0.026754817, -8.37544611e-09, 0.999642015, 1.24128064e-07, 1, 5.05623188e-09, -0.999642015, 1.23948354e-07, 0.026754817)
                    end
                end
            end
        end)

    local Toggle = Tabs.Fruit:AddToggle("Auto Random fruit [Gem]", {Title = "Auto Random fruit [Gem]", Default = false })
    Toggle:OnChanged(function(Random)
        _G.Fruit2 = Random
        while _G.Fruit2 do wait()
for i,v in pairs(game:GetService("Workspace").Shop:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-741.048889, 43.4787788, -1933.82019, -0.0251465552, 7.8026531e-08, 0.999683797, -1.09866749e-09, 1, -7.80788483e-08, -0.999683797, -3.06173398e-09, -0.0251465552)
end
end
end
    end)


players = {}

for i, v in pairs(game:GetService("Players"):GetChildren()) do
    table.insert(players, v.Name)
end

local TP = Tabs.TP:AddSection("Teleport")

local DropdownPlayer = Tabs.TP:AddDropdown("Player", {
    Title = "Player",
    Values = players,
    Multi = false,
    Default = 1,
})

DropdownPlayer:SetValue("None")

DropdownPlayer:OnChanged(function(V)
    Select = V
end)

Tabs.TP:AddButton({
    Title = "Refresh",
    Description = "Refresh",
    Callback = function()
        Window:Dialog({
            Title = "Refresh",
            Content = "Refresh",
            Buttons = {
                {
                    Title = "Confirm",
                    Callback = function()
                        table.clear(players)
                        for i, v in pairs(game:GetService("Players"):GetChildren()) do
                            table.insert(players, v.Name)
                        end
                    end
                },
                {
                    Title = "Cancel",
                    Callback = function()
                        print("no")
                    end
                }
            }
        })
    end
})

Tabs.TP:AddButton({
    Title = "Teleport to Player",
    Description = "Teleport to the selected player",
    Callback = function()
        Window:Dialog({
            Title = "Teleport to Player",
            Content = "Teleport to the selected player",
            Buttons = {
                {
                    Title = "Confirm",
                    Callback = function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[Select].Character.HumanoidRootPart.CFrame
                    end
                },
                {
                    Title = "Cancel",
                    Callback = function()
                        print("no")
                    end
                }
            }
        })
    end
})




map = {}
for i ,v in pairs(game:GetService("Workspace").Locations:GetChildren()) do
table.insert(map,v.Name)
end

Tabs.TP:AddDropdown("island", {
        Title = "island",
        Values = map,
        Multi = false,
        Default = nil,
        Callback = function(mt)
        map = mt
       end
   })
   
        Tabs.TP:AddButton({
        Title = "TP To island",
        Description = "TP To island",
        Callback = function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.workspace.Locations[map].CFrame * CFrame.new(0,-100,0)
        end
    })


local Shop = Tabs.Shop:AddSection("Shop")

    shop = {}
for i ,v in pairs(game:GetService("Workspace").Shop:GetChildren()) do
table.insert(shop,v.Name)
end

Tabs.Shop:AddDropdown("shop", {
        Title = "shop",
        Values = shop,
        Multi = false,
        Default = nil,
        Callback = function(ma)
        shop = ma
       end
   })



        Tabs.Shop:AddButton({
        Title = "TP To Shop",
        Description = "",
        Callback = function()
      		for i,v in pairs(game:GetService("Workspace").Shop[shop]:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame * CFrame.new(0,5,0)
end
      end
        end
    })
    

        Tabs.Shop:AddButton({
        Title = "Go to Traveling merchant",
        Description = "Go to Traveling merchant",
        Callback = function()
            for i,v in pairs(game:GetService("Workspace").NPC["Traveling merchant"]:GetDescendants()) do

if v.ClassName == "ProximityPrompt" then

game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame * CFrame.new(0,3,0)

wait(.1)

fireproximityprompt(v,30)

end

      end
        end
    })



local Swords = {
  "Katana";
  "Cutlass";
  "Kashimo's Pole [Curse]";
  "Kashimo's Pole [Powerless]";
  "Saber";
  "Yoru";
  "Excalibur";
  "Cid's Sword";
  "Rimuru's Sword";
}

for s,sword in pairs(Swords) do
  spawn(function()
  	local StatusWeapon = Tabs.Inventory:AddParagraph({
    	Title = sword
		})
    spawn(function()
    while wait(0.1) do
        pcall(function()
            if game.Players.LocalPlayer.PlayerGui.MainUI.Interface.Inventory.WeaponFrame:FindFirstChild(sword) then
                StatusWeapon:SetTitle(sword.." : ✅")
            else
                StatusWeapon:SetTitle(sword.." : ❌")
            end
        end)
    end
end)
  end)
end

local Inventory = Tabs.Inventory:AddSection("item")

local items = {
    { name = "Dark Flame Fruit", path = "1Dark Flame" },
    { name = "God Light", path = "1GodLight" },
    { name = "Four Leaf Clover", path = "1Four Leaf Clover" },
    { name = "Tensa Zangetsu", path = "1Tensa Zangetsu" },
    { name = "Six Eyes", path = "1Six Eyes" },
    { name = "Busoshoku Haki Book", path = "2Busoshoku Haki Book" },
    { name = "Club Card", path = "2Club Card" },
    { name = "Heart Card", path = "2Heart Card" },
    { name = "Diamond Card", path = "2Diamond Card" },
    { name = "Infinity Orb", path = "2Infinity Orb" },
    { name = "Kenbunshoku Haki Book", path = "2Kenbunshoku Haki Book" },
    { name = "Lightning Orb", path = "2Lightning Orb" },
    { name = "Race Reroll", path = "2Race Reroll" },
    { name = "[Choso] Cursed Womb", path = "2[Choso] Cursed Womb" },
    { name = "Fishing Rod", path = "3Fishing Rod" },
    { name = "Haki Color Reroll", path = "3Haki Color Reroll" },
    { name = "Holy Grail", path = "3Holy Grail" },
    { name = "Sukuna Finger", path = "3SukunaFinger" },
}

for _, item in ipairs(items) do
    local paragraph = Inventory:AddParagraph({
        Title = item.name,
        Content = "0"
    })

    spawn(function()
        while wait() do
            pcall(function()
                local itemFrame = game:GetService("Players").LocalPlayer.PlayerGui.MainUI.Interface.Inventory.ItemsFrame[item.path]
                
                if itemFrame then
                    paragraph:SetDesc(item.name .. " " .. itemFrame.Frame.Number.Text)
                else
                    paragraph:SetDesc(item.name .. " 0") 
                end
            end)
        end
    end)
end
local Inventory = Tabs.Inventory:AddSection("Swords")



-- Addons:
-- SaveManager (Allows you to have a configuration system)
-- InterfaceManager (Allows you to have a interface managment system)

-- Hand the library over to our managers
SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

-- Ignore keys that are used by ThemeManager.
-- (we dont want configs to save themes, do we?)
SaveManager:IgnoreThemeSettings()

-- You can add indexes of elements the save manager should ignore
SaveManager:SetIgnoreIndexes({})

-- use case for doing it this way:
-- a script hub could have themes in a global folder
-- and game configs in a separate folder per game
InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")

InterfaceManager:BuildInterfaceSection(Tabs.Settings)
SaveManager:BuildConfigSection(Tabs.Settings)


Window:SelectTab(1)


-- You can use the SaveManager:LoadAutoloadConfig() to load a config
-- which has been marked to be one that auto loads!
SaveManager:LoadAutoloadConfig()
