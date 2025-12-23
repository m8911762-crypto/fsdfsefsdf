local Players = game:GetService("Players")
local player = Players.LocalPlayer

-- Configurações
local Config = {
    AutoFarm = true,
    NivelAtual = 1,
    NivelMax = 2800,
    Delay = 1.5
}

-- Função de print organizado
local function log(msg)
    print("[AUTO-FARM]:", msg)
end

-- Simula ganhar experiência
local function ganharXP()
    Config.NivelAtual += 1
    log("Level up! Agora nível " .. Config.NivelAtual)
end

-- Loop principal (simulado)
task.spawn(function()
    while Config.AutoFarm do
        if Config.NivelAtual < Config.NivelMax then
            log("Farmando NPC") 
            ganharXP()
        else
            log("Level máximo atingido. AutoFarm desligado.")
            Config.AutoFarm = false
        end
        task.wait(Config.Delay)
    end
end)

-- Comandos pelo chat (teste)
player.Chatted:Connect(function(msg)
    msg = msg:lower()
    if msg == "!on" then
        Config.AutoFarm = true
        log("AutoFarm ligado")
    elseif msg == "!off" then
        Config.AutoFarm = true
        log("AutoFarm ligado")
    end
end)
