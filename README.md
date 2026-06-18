Jogadores locais = jogo:GetService("Players")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")

local Jogador = Jogadores. Jogador Local
PlayerGui local = PlayerLocal:WaitForChild ("PlayerGui")

local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "IrishHubGui"
screenGui.ResetOnSpawn = false

mainFrame local = Instance.new("Frame", screenGui)
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 270, 0, 190)
mainFrame.Position = UDim2.new(0.5, -135, 0.5, -95)
mainFrame.BackgroundColor3 = Color3.fromRGB(12, 12, 12)
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.Draggable = true
Instance.new ("UICorner", mainFrame). RaioCanto = UDim.new(0, 10)
Instance.new ("UIStroke", mainFrame). Espessura = 3

título local = Instance.new("TextLabel", mainFrame)
título. Texto = "CENTRO IRLANDÊS ANTI BAT"
título. Tamanho = UDim2.new(1, -20, 0, 30)
título. Posição = UDim2.new(0, 15, 0, 5)
título. ContextoTransparência = 1
título. TextColor3 = Color3.fromRGB(255, 255, 255)
título. fonte = enum.fonte.gothamneto
título. TamanhoTexto = 12
título. TextXAlignment = Enum.TextXAlignment.Left

local: statusDot = Instance.new("Frame", mainFrame)
statusDot.Size = UDim2.new(0, 7, 0, 7)
statusDot.Position = UDim2.new(0.92, 0, 0.08, 0)
statusDot.BackgroundColor3 = Color3.fromRGB(46, 204, 113)
Instance.new ("UICorner", statusDot). RaioCanto = UDim.new(1, 0)

função local createFeature (nome, yOffset)
 local frame = Instance.new("Frame", mainFrame)
 Enquadrar. Tamanho = UDim2.new(0.9, 0, 0, 60)
 Enquadrar. Posição = UDim2.new(0.05, 0, 0, yOffset)
 Enquadrar. BackgroundColor3 = Color3.fromRGB(60, 20, 20)
 Instance.new ("UICorner", frame). RaioCanto = UDim.new(0, 8)
 traço local = Instance.new("UIStroke", frame)
 AVC. Color = Color3.fromRGB(204, 46, 46)
 AVC. Espessura = 2
 etiqueta local = Instance.new("TextLabel", frame)
 Etiqueta. Texto = nome
 Etiqueta. Tamanho = UDim2.new(0,5, 0, 0,4, 0)
 Etiqueta. Posição = UDim2.new(0,05, 0, 0,15, 0)
 Etiqueta. ContextoTransparência = 1
 Etiqueta. TextColor3 = Color3.fromRGB(255, 255, 255)
 Etiqueta. fonte = enum.fonte.gothamneto
 Etiqueta. TamanhoTextoT= 13
 Etiqueta. TextXAlignment = Enum.TextXAlignment.Left
 status local = Instance.new("TextLabel", frame)
 status. Texto = "STATUS: INATIVO"
 status. Tamanho = UDim2.new(0,5, 0, 0,3, 0)
 status. Posição = UDim2.new(0,05, 0, 0,55, 0)
 status. ContextoTransparência = 1
 status. TextColor3 = Color3.fromRGB(204, 46, 46)
 status. fonte = enum.fonte.gothamneto
 status. TamanhoTextoT= 9
 status. TextXAlignment = Enum.TextXAlignment.Left
 local bg = Instance.new("Frame", frame)
 BG. Tamanho = UDim2.new(0, 38, 0, 19)
 BG. Posição = UDim2.new(0.8, 0, 0.3, 0)
 BG. CorBackground3 = Cor3.fromRGB(25, 25, 25)
 Instance.new ("UICorner", bg). RaioCanto = UDim.new(1, 0)
 botão local = Instance.new("Frame", bg)
 Bobagem. Tamanho = UDim2.new(0, 9, 0, 9)
 Bobagem. Posição = UDim2.new(0.15, 0, 0.25, 0)
 Bobagem. BackgroundColor3 = Color3.fromRGB(255, 255, 255)
 Instance.new ("UICorner", knob). RaioCanto = UDim.new(1, 0)
 local btn = Instance.new("TextButton", frame)
 BTN. Tamanho = UDim2.new(1, 0, 1, 0)
 BTN. ContextoTransparência = 1
 BTN. Texto = ""
 retorno btn, frame, stroke, status, knob
fim

local abBtn, abFrame, abStroke, abStatus, abKnob = createFeature("Anti Bat", 40)
local ijBtn, ijFrame, ijStroke, ijStatus, ijKnob = createFeature("Inf Jump", 110)

antiBatActive local, infJumpEnabled, antiBatConn = false, false, nil

local function updateUI(frame, stroke, status, knob, ativo)
 col local = ativo e Color3.fromRGB(40, 90, 50) ou Color3.fromRGB(60, 20, 20)
 bCol local = ativo e Color3.fromRGB(46, 204, 113) ou Color3.fromRGB(204, 46, 46)
 local pos = ativo e UDim2.new(0.65, 0, 0.25, 0) ou UDim2.new(0.15, 0, 0.25, 0)
 Enquadrar. Cor de Fundo3 = col
 AVC. Cor = bCol
 status. TextColor3 = bCol
 status. Texto = ativo e "STATUS: ATIVO" ou "STATUS: INATIVO"
 TweenService:Create(knob, TweenInfo.new(0.2), {Position = pos}):P lay()
fim

abBtn.MouseButton1Click:Connect(function()
 antiBatActive = não antiBatActive
 se antiBatActive então
 antiBatConn = RunService.Heartbeat:Connect(function()
 raiz local = LocalJogador.Personagem e LocalJogador.Personagem:EncontrarPrimeiroFilho("HumanoideRootPart")
 se raiz então 
 orig local = raiz. Velocidade
 Root. Velocidade = Vetor3.novo(1000, raiz. Velocity.Y, 1000)
 RunService.RenderStepped:Wait()
 Root. Velocidade = Vetor3.novo(orig. X, raiz. Velocity.Y, beleza. Z) -- Y-Achse hier unberührt lassen
 fim
 fim)
 senão
 se antiBatConn, então antiBatConn:Disconnect() antiBatConn = fim zero
 fim
 updateUI(abFrame, abStroke, abStatus, abKnob, antiBatActive)
fim)

ijBtn.MouseButton1Click:Connect(function()
 infJumpEnabled = não infJumpEnabled
 updateUI(ijFrame, ijStroke, ijStatus, ijKnob, infJumpEnabled)
fim)

UserInputService.JumpRequest:Connect(function()
 se infJumpEnabled então
 raiz local = LocalJogador.Personagem e LocalJogador.Personagem:EncontrarPrimeiroFilho("HumanoideRootPart")
 se a raiz então a raiz é a raiz. Velocidade = Vetor3.novo(raiz. Velocity.X, 50, raiz. Velocity.Z) fim
 fim
fim)
