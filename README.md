local espEnabled = true

local function createESP(player)
    if player.Character and player.Character:FindFirstChild("Head") then
        local head = player.Character.Head

        local box = Instance.new("Frame")
        box.Name = "ESPBox"
        box.Size = UDim2.new(0, 100, 0, 100)
        box.Position = UDim2.new(0, -50, 0, -50)
        box.BackgroundColor3 = Color3.fromRGB(255, 255, 0)
        box.BackgroundTransparency = 0.5
        box.BorderSizePixel = 2
        box.Parent = game.CoreGui

        local UICornerBox = Instance.new("UICorner")
        UICornerBox.CornerRadius = UDim.new(0, 12)
        UICornerBox.Parent = box
        
        local function updateBoxPosition()
            local headPosition = head.Position
            box.Position = UDim2.new(0, headPosition.X - 50, 0, headPosition.Y + 2)
        end

        local nameLabel = Instance.new("TextLabel")
        nameLabel.Name = "ESPName"
        nameLabel.Size = UDim2.new(0, 120, 0, 50)
        nameLabel.Position = UDim2.new(0, -60, 0, -60)
        nameLabel.BackgroundTransparency = 1
        nameLabel.Text = player.Name
        nameLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
        nameLabel.TextSize = 16
        nameLabel.TextStrokeTransparency = 0.8
        nameLabel.TextStrokeColor3 = Color3.fromRGB(255, 255, 255)
        nameLabel.Parent = game.CoreGui
        
        game:GetService("RunService").Heartbeat:Connect(function()
            if espEnabled then
                updateBoxPosition()
                box.Visible = true
                nameLabel.Visible = true
            else
                box.Visible = false
                nameLabel.Visible = false
            end
        end)
    end
end

game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function()
        createESP(player)
    end)
end)

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer.PlayerGui

local backgroundButton = Instance.new("Frame")
backgroundButton.Size = UDim2.new(0, 300, 0, 50)
backgroundButton.Position = UDim2.new(0, 10, 0, 10)
backgroundButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
backgroundButton.Parent = screenGui

local UICornerBackground = Instance.new("UICorner")
UICornerBackground.CornerRadius = UDim.new(0, 15)
UICornerBackground.Parent = backgroundButton

local UIBorderBackground = Instance.new("UIBorder")
UIBorderBackground.BorderSizePixel = 3
UIBorderBackground.BorderColor3 = Color3.fromRGB(0, 0, 0)
UIBorderBackground.Parent = backgroundButton

local purplePart = Instance.new("Frame")
purplePart.Size = UDim2.new(0, 150, 1, 0)
purplePart.Position = UDim2.new(0.5, 0, 0, 0)
purplePart.BackgroundColor3 = Color3.fromRGB(128, 0, 128)
purplePart.Parent = backgroundButton

local UICornerPurplePart = Instance.new("UICorner")
UICornerPurplePart.CornerRadius = UDim.new(0, 15)
UICornerPurplePart.Parent = purplePart

local toggleButtonText = Instance.new("TextLabel")
toggleButtonText.Size = UDim2.new(1, 0, 1, 0)
toggleButtonText.Position = UDim2.new(0, 0, 0, 0)
toggleButtonText.Text = "Fz4 Esp 🤝 15M Leaks"
toggleButtonText.TextSize = 18
toggleButtonText.BackgroundTransparency = 1
toggleButtonText.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleButtonText.TextStrokeTransparency = 0.8
toggleButtonText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
toggleButtonText.Parent = backgroundButton

local toggleButton = Instance.new("TextButton")
toggleButton.Size = UDim2.new(0, 300, 0, 50)
toggleButton.Position = UDim2.new(0, 10, 0, 70)
toggleButton.Text = "Ativar/Desativar ESP"
toggleButton.TextSize = 18
toggleButton.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleButton.Parent = screenGui

local UICornerButton = Instance.new("UICorner")
UICornerButton.CornerRadius = UDim.new(0, 15)
UICornerButton.Parent = toggleButton

local UIBorderButton = Instance.new("UIBorder")
UIBorderButton.BorderSizePixel = 3
UIBorderButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
UIBorderButton.Parent = toggleButton

toggleButton.MouseButton1Click:Connect(function()
    espEnabled = not espEnabled
    if espEnabled then
        toggleButton.Text = "Desativar ESP"
    else
        toggleButton.Text = "Ativar ESP"
    end
end)
