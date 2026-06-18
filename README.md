local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remote = ReplicatedStorage:WaitForChild("OpenDoor")

local porta = script.Parent

local fechada = porta.Position
local aberta = porta.Position + Vector3.new(0,10,0)

local usando = false

remote.OnServerEvent:Connect(function(player)

    if usando then return end
    usando = true

    for i = 1,25 do
        porta.Position = porta.Position:Lerp(aberta,0.15)
        task.wait(0.02)
    end

    task.wait(5)

    for i = 1,25 do
        porta.Position = porta.Position:Lerp(fechada,0.15)
        task.wait(0.02)
    end

    usando = false
end)
