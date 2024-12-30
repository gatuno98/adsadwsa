-- Script que exibe o nome dos outros jogadores na interface com a cor branca

-- Obtém o jogador local (o jogador que está executando o script)
local jogadorLocal = game.Players.LocalPlayer

-- Obtém a tela do jogador local
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = jogadorLocal:WaitForChild("PlayerGui")

-- Função que cria um label para exibir os nomes dos jogadores
local function criarNomeJogador(nome)
    local nomeLabel = Instance.new("TextLabel")
    nomeLabel.Parent = screenGui
    nomeLabel.Text = nome
    nomeLabel.TextColor3 = Color3.fromRGB(255, 255, 255) -- Cor branca
    nomeLabel.Size = UDim2.new(0, 200, 0, 50) -- Tamanho do label
    nomeLabel.Position = UDim2.new(0, 0, 0, 50 * #screenGui:GetChildren()) -- Posição dinâmica
    nomeLabel.BackgroundTransparency = 1 -- Sem fundo
    nomeLabel.TextScaled = true
end

-- Função que exibe os nomes dos jogadores
local function mostrarNomesDosJogadores()
    -- Itera sobre todos os jogadores no jogo
    for _, jogador in pairs(game.Players:GetPlayers()) do
        -- Ignora o jogador local (que não deve aparecer na lista de outros jogadores)
        if jogador ~= jogadorLocal then
            -- Cria um label para exibir o nome de cada jogador
            criarNomeJogador(jogador.Name)
        end
    end
end

-- Chama a função para mostrar os nomes dos outros jogadores
mostrarNomesDosJogadores()
