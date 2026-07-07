local GameId = game.GameId
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local CoreGui = game:GetService("CoreGui")

repeat task.wait() until game:IsLoaded() and Players.LocalPlayer
local plr = Players.LocalPlayer

-- ============================================
-- MEU GRAU HUB - SENHA: 1234
-- ============================================

local GameList = {
    [994732206] = true,
    [7018190066] = true,
    [383310974] = true,
    [4777817887] = true,
    [5477548919] = true,
    [5750914919] = true,
    [3359505957] = true,
    [6167925365] = true,
    [5361032378] = true,
    [7709344486] = true,
    [7326934954] = true,
    [3149100453] = true,
    [5995470825] = true,
    [358276974] = true,
    [7541395924] = true,
    [6701277882] = true,
    [953622098] = true,
    [7200297228] = true,
    [7832036655] = true,
    [7061783500] = true,
    [9619492068] = true,
}

local jogoSuportado = false
for id, _ in pairs(GameList) do
    if id == GameId then
        jogoSuportado = true
    end
end

if _G.loadCustomId then
    jogoSuportado = true
end

-- ============================================
-- TELA DE SENHA - KEY: 1234
-- ============================================
local function criarTelaSenha()
    local MeuGrau = Instance.new("ScreenGui")
    MeuGrau.Name = "Meu_Grau_Hub"
    MeuGrau.ResetOnSpawn = false
    MeuGrau.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    MeuGrau.Parent = CoreGui
    
    -- Fundo escuro
    local Fundo = Instance.new("Frame")
    Fundo.Size = UDim2.new(1, 0, 1, 0)
    Fundo.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
    Fundo.BackgroundTransparency = 0.3
    Fundo.BorderSizePixel = 0
    Fundo.Parent = MeuGrau
    
    -- Painel central
    local Painel = Instance.new("Frame")
    Painel.Size = UDim2.new(0, 350, 0, 220)
    Painel.Position = UDim2.new(0.5, -175, 0.5, -110)
    Painel.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    Painel.BorderSizePixel = 0
    Painel.Parent = MeuGrau
    
    local BordaPainel = Instance.new("UICorner")
    BordaPainel.CornerRadius = UDim.new(0, 10)
    BordaPainel.Parent = Painel
    
    -- Título
    local Titulo = Instance.new("TextLabel")
    Titulo.Size = UDim2.new(1, 0, 0, 40)
    Titulo.Position = UDim2.new(0, 0, 0, 15)
    Titulo.BackgroundTransparency = 1
    Titulo.Text = "MEU GRAU HUB"
    Titulo.TextColor3 = Color3.fromRGB(255, 50, 50)
    Titulo.TextSize = 30
    Titulo.Font = Enum.Font.SourceSansBold
    Titulo.Parent = Painel
    
    -- Subtítulo
    local Subtitulo = Instance.new("TextLabel")
    Subtitulo.Size = UDim2.new(1, 0, 0, 20)
    Subtitulo.Position = UDim2.new(0, 0, 0, 55)
    Subtitulo.BackgroundTransparency = 1
    Subtitulo.Text = "DIGITE A SENHA PARA ENTRAR"
    Subtitulo.TextColor3 = Color3.fromRGB(180, 180, 180)
    Subtitulo.TextSize = 14
    Subtitulo.Font = Enum.Font.SourceSans
    Subtitulo.Parent = Painel
    
    -- Campo de senha
    local CampoSenha = Instance.new("TextBox")
    CampoSenha.Size = UDim2.new(0, 270, 0, 40)
    CampoSenha.Position = UDim2.new(0.5, -135, 0, 85)
    CampoSenha.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    CampoSenha.TextColor3 = Color3.fromRGB(255, 255, 255)
    CampoSenha.PlaceholderText = "SENHA..."
    CampoSenha.TextSize = 18
    CampoSenha.Font = Enum.Font.SourceSansBold
    CampoSenha.BorderSizePixel = 0
    CampoSenha.Parent = Painel
    
    local BordaCampo = Instance.new("UICorner")
    BordaCampo.CornerRadius = UDim.new(0, 5)
    BordaCampo.Parent = CampoSenha
    
    -- Botão entrar
    local BotaoEntrar = Instance.new("TextButton")
    BotaoEntrar.Size = UDim2.new(0, 270, 0, 45)
    BotaoEntrar.Position = UDim2.new(0.5, -135, 0, 140)
    BotaoEntrar.BackgroundColor3 = Color3.fromRGB(200, 30, 30)
    BotaoEntrar.TextColor3 = Color3.fromRGB(255, 255, 255)
    BotaoEntrar.Text = "ENTRAR"
    BotaoEntrar.TextSize = 20
    BotaoEntrar.Font = Enum.Font.SourceSansBold
    BotaoEntrar.BorderSizePixel = 0
    BotaoEntrar.Parent = Painel
    
    local BordaBotao = Instance.new("UICorner")
    BordaBotao.CornerRadius = UDim.new(0, 5)
    BordaBotao.Parent = BotaoEntrar
    
    -- Dica da senha
    local Dica = Instance.new("TextLabel")
    Dica.Size = UDim2.new(1, 0, 0, 20)
    Dica.Position = UDim2.new(0, 0, 0, 195)
    Dica.BackgroundTransparency = 1
    Dica.Text = "SENHA: 1234"
    Dica.TextColor3 = Color3.fromRGB(140, 140, 140)
    Dica.TextSize = 12
    Dica.Font = Enum.Font.SourceSans
    Dica.Parent = Painel
    
    -- ============================================
    -- VERIFICAÇÃO DA SENHA: 1234
    -- ============================================
    local function verificarSenha()
        if CampoSenha.Text == "1234" then
            -- SENHA CORRETA - Abre o painel principal
            MeuGrau:Destroy()
            criarPainelPrincipal()
        else
            -- SENHA ERRADA
            CampoSenha.Text = ""
            CampoSenha.PlaceholderText = "SENHA INCORRETA!"
            CampoSenha.PlaceholderColor3 = Color3.fromRGB(255, 80, 80)
            
            task.wait(2)
            CampoSenha.PlaceholderText = "SENHA..."
            CampoSenha.PlaceholderColor3 = Color3.fromRGB(170, 170, 170)
        end
    end
    
    BotaoEntrar.MouseButton1Click:Connect(verificarSenha)
    
    CampoSenha.FocusLost:Connect(function(enterPressed)
        if enterPressed then
            verificarSenha()
        end
    end)
end

-- ============================================
-- PAINEL PRINCIPAL (APÓS SENHA CORRETA)
-- ============================================
function criarPainelPrincipal()
    local PainelPrincipal = Instance.new("ScreenGui")
    PainelPrincipal.Name = "Meu_Grau_Painel"
    PainelPrincipal.ResetOnSpawn = false
    PainelPrincipal.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    PainelPrincipal.Parent = CoreGui
    
    -- Botão para abrir/fechar
    local BotaoAbrir = Instance.new("TextButton")
    BotaoAbrir.Size = UDim2.new(0, 60, 0, 30)
    BotaoAbrir.Position = UDim2.new(0, 10, 0, 10)
    BotaoAbrir.BackgroundColor3 = Color3.fromRGB(200, 30, 30)
    BotaoAbrir.TextColor3 = Color3.fromRGB(255, 255, 255)
    BotaoAbrir.Text = "MEU GRAU"
    BotaoAbrir.TextSize = 12
    BotaoAbrir.Font = Enum.Font.SourceSansBold
    BotaoAbrir.BorderSizePixel = 0
    BotaoAbrir.Parent = PainelPrincipal
    
    local BordaBotao = Instance.new("UICorner")
    BordaBotao.CornerRadius = UDim.new(0, 5)
    BordaBotao.Parent = BotaoAbrir
    
    -- Painel principal
    local Painel = Instance.new("Frame")
    Painel.Size = UDim2.new(0, 400, 0, 500)
    Painel.Position = UDim2.new(0.5, -200, 0.5, -250)
    Painel.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    Painel.BorderSizePixel = 0
    Painel.Visible = false
    Painel.Parent = PainelPrincipal
    
    local BordaPainel = Instance.new("UICorner")
    BordaPainel.CornerRadius = UDim.new(0, 10)
    BordaPainel.Parent = Painel
    
    -- Barra superior
    local BarraSuperior = Instance.new("Frame")
    BarraSuperior.Size = UDim2.new(1, 0, 0, 40)
    BarraSuperior.BackgroundColor3 = Color3.fromRGB(200, 30, 30)
    BarraSuperior.BorderSizePixel = 0
    BarraSuperior.Parent = Painel
    
    local BordaBarra = Instance.new("UICorner")
    BordaBarra.CornerRadius = UDim.new(0, 10)
    BordaBarra.Parent = BarraSuperior
    
    -- Título do painel
    local TituloPainel = Instance.new("TextLabel")
    TituloPainel.Size = UDim2.new(0, 300, 0, 40)
    TituloPainel.Position = UDim2.new(0, 50, 0, 0)
    TituloPainel.BackgroundTransparency = 1
    TituloPainel.Text = "MEU GRAU HUB"
    TituloPainel.TextColor3 = Color3.fromRGB(255, 255, 255)
    TituloPainel.TextSize = 20
    TituloPainel.Font = Enum.Font.SourceSansBold
    TituloPainel.Parent = BarraSuperior
    
    -- Botão fechar
    local BotaoFechar = Instance.new("TextButton")
    BotaoFechar.Size = UDim2.new(0, 40, 0, 40)
    BotaoFechar.Position = UDim2.new(1, -40, 0, 0)
    BotaoFechar.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
    BotaoFechar.TextColor3 = Color3.fromRGB(255, 255, 255)
    BotaoFechar.Text = "X"
    BotaoFechar.TextSize = 18
    BotaoFechar.Font = Enum.Font.SourceSansBold
    BotaoFechar.BorderSizePixel = 0
    BotaoFechar.Parent = BarraSuperior
    
    -- Conteúdo do painel
    local Conteudo = Instance.new("Frame")
    Conteudo.Size = UDim2.new(1, -20, 1, -60)
    Conteudo.Position = UDim2.new(0, 10, 0, 50)
    Conteudo.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
    Conteudo.BorderSizePixel = 0
    Conteudo.Parent = Painel
    
    local BordaConteudo = Instance.new("UICorner")
    BordaConteudo.CornerRadius = UDim.new(0, 5)
    BordaConteudo.Parent = Conteudo
    
    -- Texto de boas-vindas
    local BoasVindas = Instance.new("TextLabel")
    BoasVindas.Size = UDim2.new(1, 0, 0, 40)
    BoasVindas.Position = UDim2.new(0, 0, 0, 20)
    BoasVindas.BackgroundTransparency = 1
    BoasVindas.Text = "BEM-VINDO AO MEU GRAU HUB!"
    BoasVindas.TextColor3 = Color3.fromRGB(255, 255, 255)
    BoasVindas.TextSize = 18
    BoasVindas.Font = Enum.Font.SourceSansBold
    BoasVindas.Parent = Conteudo
    
    -- ============================================
    -- BOTÕES DO PAINEL
    -- ============================================
    local Botao1 = Instance.new("TextButton")
    Botao1.Size = UDim2.new(0, 170, 0, 35)
    Botao1.Position = UDim2.new(0, 0, 0, 100)
    Botao1.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    Botao1.TextColor3 = Color3.fromRGB(255, 255, 255)
    Botao1.Text = "BOTÃO 1"
    Botao1.TextSize = 14
    Botao1.Font = Enum.Font.SourceSansBold
    Botao1.BorderSizePixel = 0
    Botao1.Parent = Conteudo
    
    local BordaBotao1 = Instance.new("UICorner")
    BordaBotao1.CornerRadius = UDim.new(0, 5)
    BordaBotao1.Parent = Botao1
    
    local Botao2 = Instance.new("TextButton")
    Botao2.Size = UDim2.new(0, 170, 0, 35)
    Botao2.Position = UDim2.new(0, 190, 0, 100)
    Botao2.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    Botao2.TextColor3 = Color3.fromRGB(255, 255, 255)
    Botao2.Text = "BOTÃO 2"
    Botao2.TextSize = 14
    Botao2.Font = Enum.Font.SourceSansBold
    Botao2.BorderSizePixel = 0
    Botao2.Parent = Conteudo
    
    local BordaBotao2 = Instance.new("UICorner")
    BordaBotao2.CornerRadius = UDim.new(0, 5)
    BordaBotao2.Parent = Botao2
    
    -- ============================================
    -- FUNÇÕES DOS BOTÕES
    -- ============================================
    BotaoAbrir.MouseButton1Click:Connect(function()
        Painel.Visible = not Painel.Visible
    end)
    
    BotaoFechar.MouseButton1Click:Connect(function()
        Painel.Visible = false
    end)
    
    Botao1.MouseButton1Click:Connect(function()
        print("Botão 1 clicado!")
    end)
    
    Botao2.MouseButton1Click:Connect(function()
        print("Botão 2 clicado!")
    end)
    
    -- Tornar painel arrastável
    local UserInputService = game:GetService("UserInputService")
    local arrastando = false
    local posicaoInicial
    local posicaoPainel
    
    BarraSuperior.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            arrastando = true
            posicaoInicial = input.Position
            posicaoPainel = Painel.Position
        end
    end)
    
    UserInputService.InputChanged:Connect(function(input)
        if arrastando and input.UserInputType == Enum.UserInputType.MouseMovement then
            local delta = input.Position - posicaoInicial
            Painel.Position = UDim2.new(
                posicaoPainel.X.Scale,
                posicaoPainel.X.Offset + delta.X,
                posicaoPainel.Y.Scale,
                posicaoPainel.Y.Offset + delta.Y
            )
        end
    end)
    
    UserInputService.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            arrastando = false
        end
    end)
end

-- Inicia a tela de senha
criarTelaSenha()
