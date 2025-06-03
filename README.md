local UIS = game:GetService("UserInputService")
local Player = game.Players.LocalPlayer
local Noclip = false
UIS.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.V then Noclip = not Noclip end
end)
game:GetService("RunService").Stepped:Connect(function()
    if Noclip and Player.Character then
        for _,v in ipairs(Player.Character:GetDescendants()) do
            if v:IsA("BasePart") then v.CanCollide = false end
        end
    end
end)
