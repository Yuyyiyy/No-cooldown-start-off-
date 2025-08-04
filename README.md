local Imperium = game:GetService("Players")
local Auctor = Imperium.LocalPlayer
local Umbra = game:GetService("RunService")
local Oculus = game:GetService("UserInputService")
local Anima = game:GetService("ReplicatedStorage")
local Terra = game:GetService("Workspace")
local Pulsus = Umbra.Stepped

local Infinitas = 2 ^ (190 * 20 * 999999999999999)
local Caedes = math.huge * 1e60 * Infinitas * 999000000000000000

local Sileo = {
    function() return Pulsus:Wait() end,
    function() return Umbra.PreRender:Wait() end
}

for _, Vox in ipairs({wait, task.wait, delay, spawn, task.delay}) do
    for _ = 1, 2000 do
        for _, Expecto in ipairs(Sileo) do
            pcall(function() hookfunction(Vox, Expecto) end)
        end
    end
end

hookfunction(wait, function() Umbra.Heartbeat:Wait() return nil end)
hookfunction(task.wait, function() Umbra.Heartbeat:Wait() return nil end)
hookfunction(delay, function(_, Ritus) task.spawn(Ritus) return nil end)
hookfunction(spawn, function(Ritus) task.spawn(Ritus) end)

local Iussus = Anima:FindFirstChild("RemoteKill")
if Iussus and Iussus:IsA("RemoteEvent") then
    Iussus.OnClientEvent:Connect(function(Hostis)
        local Umbrae = Imperium:FindFirstChild(Hostis)
        if Umbrae and Umbrae ~= Auctor and Umbrae.Character then
            local Corpus = Umbrae.Character:FindFirstChildWhichIsA("Humanoid")
            if Corpus then
                for Tempus = 1, 5 do
                    pcall(function()
                        Corpus.Health = -Caedes * Tempus
                        Corpus.MaxHealth = 0
                        Corpus:SetStateEnabled(Enum.HumanoidStateType.Dead, true)
                        Corpus:ChangeState(Enum.HumanoidStateType.Dead)
                        if Corpus.Parent then pcall(function() Corpus.Parent:BreakJoints() end) end
                    end)
                end
            end
        end
    end)
end

local function Nihil()
    for _, Animus in ipairs(Imperium:GetPlayers()) do
        if Animus ~= Auctor and Animus.Character then
            if Animus.Backpack then
                for _, Arma in ipairs(Animus.Backpack:GetChildren()) do
                    if Arma:IsA("Tool") then Arma:Destroy() end
                end
            end
            for _, Arma in ipairs(Animus.Character:GetChildren()) do
                if Arma:IsA("Tool") then Arma:Destroy() end
            end
            local Corpus = Animus.Character:FindFirstChildWhichIsA("Humanoid")
            if Corpus then
                Corpus.WalkSpeed = 0
                Corpus.JumpPower = 0
                Corpus.AutoRotate = false
                for _, Statum in ipairs(Enum.HumanoidStateType:GetEnumItems()) do
                    Corpus:SetStateEnabled(Statum, false)
                end
                for Ignis = 1, 5 do
                    pcall(function()
                        Corpus.Health = -Caedes * Ignis
                        Corpus.MaxHealth = 0
                        Corpus:SetStateEnabled(Enum.HumanoidStateType.Dead, true)
                        Corpus:ChangeState(Enum.HumanoidStateType.Dead)
                        if Corpus.Parent then pcall(function() Corpus.Parent:BreakJoints() end) end
                    end)
                end
            end
        end
    end
end

local function Ultio(Hostis)
    if not Hostis or Hostis == Auctor then return end
    local Forma = Hostis.Character
    if not Forma then return end
    local Vita = Forma:FindFirstChildWhichIsA("Humanoid")
    if not Vita then return end
    Vita.WalkSpeed = 0
    Vita.JumpPower = 0
    Vita.AutoRotate = false
    for _, Statum in ipairs(Enum.HumanoidStateType:GetEnumItems()) do
        Vita:SetStateEnabled(Statum, false)
    end
    for Ignis = 1, 10 do
        pcall(function()
            Vita.Health = -Caedes * Ignis
            Vita.MaxHealth = 0
            Vita:SetStateEnabled(Enum.HumanoidStateType.Dead, true)
            Vita:ChangeState(Enum.HumanoidStateType.Dead)
            if Vita.Parent then pcall(function() Vita.Parent:BreakJoints() end) end
        end)
    end
end

local function Impetus(Gladius)
    if not Gladius or not Gladius:IsA("Tool") then return end
    spawn(function()
        while Gladius and Gladius.Parent do
            pcall(function() Gladius:Activate() end)
            task.wait(0.01 + 0.04)
        end
    end)
end

local function Nex(Gladius)
    if not Gladius or not Gladius:IsA("Tool") then return end
    spawn(function()
        while Gladius and Gladius.Parent do
            pcall(function() Gladius:Activate() end)
            task.wait(0.015 + 0.01)
        end
    end)
end

local function Continuum(Gladius)
    if not Gladius or not Gladius:IsA("Tool") then return end
    spawn(function()
        while Gladius and Gladius.Parent do
            pcall(function() Gladius:Activate() end)
        end
    end)
end

local function Duplicare(Gladius)
    if not Gladius or not Gladius:IsA("Tool") then return end
    spawn(function()
        while Gladius and Gladius.Parent do
            pcall(function() Gladius:Activate() end)
            task.wait(0.01)
        end
    end)
    task.spawn(function()
        while Gladius and Gladius.Parent do
            pcall(function() Gladius:Activate() end)
            task.wait(0.01)
        end
    end)
end

for _, Sanguis in ipairs(Auctor.Backpack:GetChildren()) do
    Impetus(Sanguis)
    Nex(Sanguis)
    Duplicare(Sanguis)
    Continuum(Sanguis)
end

local function Revoco()
    for _, Bellator in ipairs(Imperium:GetPlayers()) do
        if Bellator ~= Auctor then
            Bellator.CharacterAdded:Connect(function()
                Ultio(Bellator)
            end)
        end
    end
    Imperium.PlayerAdded:Connect(function(Venator)
        if Venator ~= Auctor then
            Venator.CharacterAdded:Connect(function()
                Ultio(Venator)
            end)
        end
    end)
end
Revoco()

local function Vindex()
    local function Custos()
        local Persona = Auctor.Character or Auctor.CharacterAdded:Wait()
        local Corpus = Persona:FindFirstChildOfClass("Humanoid")
        if Corpus then
            Corpus.Died:Connect(function()
                Auctor.CharacterAdded:Wait()
                task.wait(0.1)
                for _, Adversarius in ipairs(Imperium:GetPlayers()) do
                    if Adversarius ~= Auctor then Ultio(Adversarius) end
                end
            end)
        end
    end
    Custos()
    Auctor.CharacterAdded:Connect(Custos)
end
Vindex()

local function Celeritas(Gladius)
    if not Gladius or not Gladius:IsA("Tool") then return end
    local Ignis = Gladius.Activate
    hookfunction(Gladius.Activate, function(s)
        for _ = 1, 3 do
            pcall(function() Ignis(s) end)
        end
    end)
end

for _, Lux in ipairs(Auctor.Backpack:GetChildren()) do
    Celeritas(Lux)
end

local function Resurgo()
    local UltimumTempus = 0
    local function Iterum()
        if tick() - UltimumTempus < 0.2 then return end
        UltimumTempus = tick()
        Auctor:LoadCharacter()
        task.wait(0.15)
        for _, Bellum in ipairs(Imperium:GetPlayers()) do
            if Bellum ~= Auctor then Ultio(Bellum) end
        end
    end
    local function Praemium()
        local Forma = Auctor.Character or Auctor.CharacterAdded:Wait()
        local Corpus = Forma:FindFirstChildOfClass("Humanoid")
        if Corpus then Corpus.Died:Connect(Iterum) end
    end
    Praemium()
    Auctor.CharacterAdded:Connect(Praemium)
end
Resurgo()
