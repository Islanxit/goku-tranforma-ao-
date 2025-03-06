# goku-tranforma-ao-
-- Este script vai transformar o jogador em Goku e adicionar dinheiro ao jogador de maneira justa

local player = game:GetService("Players").LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local money = player:WaitForChild("leaderstats"):WaitForChild("Money")  -- Supondo que você tenha uma variável 'Money' no leaderboard

-- Função para transformar o personagem em Goku
local function transformIntoGoku()
    -- Adiciona o modelo de Goku no personagem
    local gokuModel = game.ReplicatedStorage:WaitForChild("GokuModel"):Clone()
    gokuModel.Parent = character
    gokuModel:SetPrimaryPartCFrame(character.HumanoidRootPart.CFrame)

    -- Modificar o visual do personagem para o Goku
    humanoid:ChangeState(Enum.HumanoidStateType.Physics)
    character:WaitForChild("Head").MeshId = "rbxassetid://[ID_Do_Modelo_Goku]"  -- Substitua pelo ID correto
    -- Outros ajustes no modelo, como roupas ou acessórios, podem ser feitos aqui
end

-- Função para recompensar o jogador com dinheiro
local function giveMoney(amount)
    money.Value = money.Value + amount
end

-- Lógica de PlaceId e transformação
if game.PlaceId == 2753915549 then
    -- Mundo 1
    transformIntoGoku()  -- Torna o personagem Goku
    giveMoney(100)       -- Dá 100 de "dinheiro" ao jogador
elseif game.PlaceId == 4442272183 then
    -- Mundo 2
    transformIntoGoku()  -- Torna o personagem Goku
    giveMoney(200)       -- Dá 200 de "dinheiro" ao jogador
elseif game.PlaceId == 7449423635 then
    -- Mundo 3
    transformIntoGoku()  -- Torna o personagem Goku
    giveMoney(300)       -- Dá 300 de "dinheiro" ao jogador
else
    -- Se não for um dos mundos suportados
    player:Kick("Do not Support, Please wait...")
end
