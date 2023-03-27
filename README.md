local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()
local Camera = workspace.CurrentCamera

local Distance = 5 
local Height = 3 
local CameraOffset = CFrame.new(0, 0, -Distance) * CFrame.new(0, Height, 0) 

local function UpdateCamera()
    if Character and Character:FindFirstChild("HumanoidRootPart") then
        local RootPart = Character.HumanoidRootPart
        local TargetCFrame = RootPart.CFrame * CameraOffset
        Camera.CFrame = Camera.CFrame:Lerp(TargetCFrame, 0.1) 
        Camera.Focus = CFrame.new(RootPart.Position) 
    end
end

game:GetService("RunService").RenderStepped:Connect(UpdateCamera)
