local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "GodY Hub", HidePremium = false, SaveConfig = false, ConfigFolder = "GodY Hub"})

Premium = true

OrionLib:MakeNotification({
	Name = "GodY Hub",
	Content = "Thanks For Use My Script",
	Image = "rbxassetid://4483345998",
	Time = 5
})

local Tab = Window:MakeTab({
	Name = "LocalPlayer",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab:AddSection({
	Name = "LocalPlayer"
})

Tab:AddSlider({
	Name = "WalkSpeed",
	Min = 50,
	Max = 300,
	Default = game.Players.LocalPlayer.Character.Data.Speed.Value,
	Color = Color3.fromRGB(255,255,255),
	Increment = 5,
	ValueName = "SetWalkSpeed",
	Callback = function(SetWalkSpeed)
		game.Players.LocalPlayer.Character.Data.Speed:Destroy()
        local WalkSpeedCustom = Instance.new("IntValue")
        WalkSpeedCustom.Name = "Speed"
        WalkSpeedCustom.Value = SetWalkSpeed
        WalkSpeedCustom.Parent = game.Players.LocalPlayer.Character.Data
	end
})

Tab:AddSlider({
	Name = "SprintSpeed",
	Min = 85,
	Max = 500,
	Default = game.Players.LocalPlayer.Character.Data.SprintSpeed.Value,
	Color = Color3.fromRGB(255,255,255),
	Increment = 5,
	ValueName = "SetSprintSpeed",
	Callback = function(SetSprintSpeed)
		game.Players.LocalPlayer.Character.Data.SprintSpeed:Destroy()
        local SprintSpeedCustom = Instance.new("IntValue")
        SprintSpeedCustom.Name = "SprintSpeed"
        SprintSpeedCustom.Value = SetSprintSpeed
        SprintSpeedCustom.Parent = game.Players.LocalPlayer.Character.Data
	end
})

Tab:AddToggle({
	Name = "Auto Collect Wish",
	Default = false,
	Callback = function(AutoWish)
		getgenv().AutoCollectWish = AutoWish
	end
})



task.spawn(function()
    while getgenv().AutoCollectWish == true do
        task.wait(0.1)
        for i,v in pairs(game:GetService("Workspace").DroppedWisps:GetDescendants()) do
    if v:IsA("TouchTransmitter") then
        firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 0)
        firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 1)
    end
end
end
end)
