-- XIRO Menu System
local XIRO = {
    Enabled = true,
    Tabs = {},
    CurrentTab = "Aimbot"
}

-- Services
local RunService = game:GetService("RunService")
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local HttpService = game:GetService("HttpService")

-- Variables
local LocalPlayer = Players.LocalPlayer
local Camera = workspace.CurrentCamera
local Mouse = LocalPlayer:GetMouse()

-- Settings
local Settings = {
    -- Aimbot Settings
    AimbotEnabled = true,
    AimType = "Mouse", -- Mouse, Camera
    StickyAim = false,
    TeamCheck = true,
    Smoothness = 0.15,
    FOV = 100,
    ShowFOV = true,
    FOVColor = Color3.fromRGB(0, 255, 0),
    FOVTransparency = 0.7,
    FOVThickness = 1,
    AimPart = "Head",
    VisibleCheck = true,
    Triggerbot = false,
    TriggerbotDelay = 0.1,
    
    -- ESP Settings
    ESPEnabled = false,
    BoxESP = true,
    Tracers = false,
    NameESP = false,
    DistanceESP = false,
    HealthBar = true,
    ESPTeamCheck = false,
    ESPTeamColor = true,
    ESPColor = Color3.fromRGB(0, 255, 0),
    TracerOrigin = "Bottom",
    TracerThickness = 1,
    BoxColor = Color3.fromRGB(0, 255, 0),
    TracerColor = Color3.fromRGB(0, 255, 0),
    NameColor = Color3.fromRGB(255, 255, 255),
    DistanceColor = Color3.fromRGB(255, 255, 255),
    
    -- Exploits Settings
    FlyEnabled = false,
    FlyType = "Velocity", -- Velocity, Position
    FlySpeed = 50,
    FlyKeybind = "X",
    WalkspeedEnabled = false,
    Walkspeed = 25,
    WalkspeedKeybind = "C",
    NoclipEnabled = false,
    NoclipKeybind = "V",
    VelocityWalkspeed = false,
    
    -- Misc Settings
    AntiCheatBypass = false,
    AutoUpdate = true,
    Notifications = true
}

-- Keybind System
local Keybinds = {
    Fly = Settings.FlyKeybind,
    Walkspeed = Settings.WalkspeedKeybind,
    Noclip = Settings.NoclipKeybind
}

-- Config System
local Configs = {
    Current = "Default",
    List = {"Default"}
}

-- Notification System
local Notifications = {}
local NotificationFrame = nil

-- Create Main GUI
function XIRO:CreateMenu()
    -- Main ScreenGui
    self.ScreenGui = Instance.new("ScreenGui")
    self.ScreenGui.Name = "XIROMenu"
    self.ScreenGui.Parent = game.CoreGui
    self.ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    self.ScreenGui.Enabled = true

    -- Main Frame
    self.MainFrame = Instance.new("Frame")
    self.MainFrame.Size = UDim2.new(0, 350, 0, 500) -- Increased size
    self.MainFrame.Position = UDim2.new(0.5, -175, 0.5, -250)
    self.MainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    self.MainFrame.BorderSizePixel = 0
    self.MainFrame.Active = true
    self.MainFrame.Draggable = true
    self.MainFrame.Parent = self.ScreenGui

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 8)
    UICorner.Parent = self.MainFrame

    -- Header
    local Header = Instance.new("Frame")
    Header.Size = UDim2.new(1, 0, 0, 40)
    Header.Position = UDim2.new(0, 0, 0, 0)
    Header.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    Header.BorderSizePixel = 0
    Header.Parent = self.MainFrame

    local HeaderCorner = Instance.new("UICorner")
    HeaderCorner.CornerRadius = UDim.new(0, 8)
    HeaderCorner.Parent = Header

    local Title = Instance.new("TextLabel")
    Title.Size = UDim2.new(1, 0, 1, 0)
    Title.BackgroundTransparency = 1
    Title.Text = "XIRO Private"
    Title.TextColor3 = Color3.fromRGB(0, 255, 0)
    Title.Font = Enum.Font.GothamBold
    Title.TextSize = 18
    Title.Parent = Header

    -- Tabs Container
    local TabsContainer = Instance.new("Frame")
    TabsContainer.Size = UDim2.new(1, -20, 0, 30)
    TabsContainer.Position = UDim2.new(0, 10, 0, 45)
    TabsContainer.BackgroundTransparency = 1
    TabsContainer.Parent = self.MainFrame

    -- Tabs
    self.AimbotTab = Instance.new("TextButton")
    self.AimbotTab.Size = UDim2.new(0.25, -5, 1, 0)
    self.AimbotTab.Position = UDim2.new(0, 0, 0, 0)
    self.AimbotTab.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    self.AimbotTab.Text = "Aimbot"
    self.AimbotTab.TextColor3 = Color3.fromRGB(0, 255, 0)
    self.AimbotTab.Font = Enum.Font.Gotham
    self.AimbotTab.TextSize = 12
    self.AimbotTab.Parent = TabsContainer

    local TabCorner1 = Instance.new("UICorner")
    TabCorner1.CornerRadius = UDim.new(0, 4)
    TabCorner1.Parent = self.AimbotTab

    self.VisualsTab = Instance.new("TextButton")
    self.VisualsTab.Size = UDim2.new(0.25, -5, 1, 0)
    self.VisualsTab.Position = UDim2.new(0.25, 5, 0, 0)
    self.VisualsTab.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    self.VisualsTab.Text = "Visuals"
    self.VisualsTab.TextColor3 = Color3.fromRGB(150, 150, 150)
    self.VisualsTab.Font = Enum.Font.Gotham
    self.VisualsTab.TextSize = 12
    self.VisualsTab.Parent = TabsContainer

    local TabCorner2 = Instance.new("UICorner")
    TabCorner2.CornerRadius = UDim.new(0, 4)
    TabCorner2.Parent = self.VisualsTab

    self.ExploitsTab = Instance.new("TextButton")
    self.ExploitsTab.Size = UDim2.new(0.25, -5, 1, 0)
    self.ExploitsTab.Position = UDim2.new(0.5, 5, 0, 0)
    self.ExploitsTab.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    self.ExploitsTab.Text = "Exploits"
    self.ExploitsTab.TextColor3 = Color3.fromRGB(150, 150, 150)
    self.ExploitsTab.Font = Enum.Font.Gotham
    self.ExploitsTab.TextSize = 12
    self.ExploitsTab.Parent = TabsContainer

    local TabCorner3 = Instance.new("UICorner")
    TabCorner3.CornerRadius = UDim.new(0, 4)
    TabCorner3.Parent = self.ExploitsTab

    self.MiscTab = Instance.new("TextButton")
    self.MiscTab.Size = UDim2.new(0.25, -5, 1, 0)
    self.MiscTab.Position = UDim2.new(0.75, 5, 0, 0)
    self.MiscTab.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    self.MiscTab.Text = "Misc"
    self.MiscTab.TextColor3 = Color3.fromRGB(150, 150, 150)
    self.MiscTab.Font = Enum.Font.Gotham
    self.MiscTab.TextSize = 12
    self.MiscTab.Parent = TabsContainer

    local TabCorner4 = Instance.new("UICorner")
    TabCorner4.CornerRadius = UDim.new(0, 4)
    TabCorner4.Parent = self.MiscTab

    -- Content Container
    self.ContentContainer = Instance.new("ScrollingFrame")
    self.ContentContainer.Size = UDim2.new(1, -20, 1, -85)
    self.ContentContainer.Position = UDim2.new(0, 10, 0, 80)
    self.ContentContainer.BackgroundTransparency = 1
    self.ContentContainer.ScrollBarThickness = 3
    self.ContentContainer.CanvasSize = UDim2.new(0, 0, 0, 0)
    self.ContentContainer.Parent = self.MainFrame

    local UIListLayout = Instance.new("UIListLayout")
    UIListLayout.Padding = UDim.new(0, 8)
    UIListLayout.Parent = self.ContentContainer

    -- Tab functionality
    self.AimbotTab.MouseButton1Click:Connect(function()
        self:SwitchTab("Aimbot")
    end)

    self.VisualsTab.MouseButton1Click:Connect(function()
        self:SwitchTab("Visuals")
    end)

    self.ExploitsTab.MouseButton1Click:Connect(function()
        self:SwitchTab("Exploits")
    end)

    self.MiscTab.MouseButton1Click:Connect(function()
        self:SwitchTab("Misc")
    end)

    -- Create content for all tabs
    self:CreateAimbotTab()
    self:CreateVisualsTab()
    self:CreateExploitsTab()
    self:CreateMiscTab()
    
    -- Show Aimbot tab by default
    self:SwitchTab("Aimbot")
    
    -- Create notification system
    self:CreateNotificationSystem()
end

function XIRO:SwitchTab(TabName)
    self.CurrentTab = TabName
    
    -- Update tab appearances
    self.AimbotTab.BackgroundColor3 = TabName == "Aimbot" and Color3.fromRGB(40, 40, 40) or Color3.fromRGB(30, 30, 30)
    self.VisualsTab.BackgroundColor3 = TabName == "Visuals" and Color3.fromRGB(40, 40, 40) or Color3.fromRGB(30, 30, 30)
    self.ExploitsTab.BackgroundColor3 = TabName == "Exploits" and Color3.fromRGB(40, 40, 40) or Color3.fromRGB(30, 30, 30)
    self.MiscTab.BackgroundColor3 = TabName == "Misc" and Color3.fromRGB(40, 40, 40) or Color3.fromRGB(30, 30, 30)
    
    self.AimbotTab.TextColor3 = TabName == "Aimbot" and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(150, 150, 150)
    self.VisualsTab.TextColor3 = TabName == "Visuals" and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(150, 150, 150)
    self.ExploitsTab.TextColor3 = TabName == "Exploits" and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(150, 150, 150)
    self.MiscTab.TextColor3 = TabName == "Misc" and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(150, 150, 150)
    
    -- Show/hide content
    self.AimbotContent.Visible = TabName == "Aimbot"
    self.VisualsContent.Visible = TabName == "Visuals"
    self.ExploitsContent.Visible = TabName == "Exploits"
    self.MiscContent.Visible = TabName == "Misc"
end

function XIRO:CreateToggle(Parent, Text, Default, Callback)
    local ToggleFrame = Instance.new("Frame")
    ToggleFrame.Size = UDim2.new(1, 0, 0, 25)
    ToggleFrame.BackgroundTransparency = 1
    ToggleFrame.Parent = Parent

    local ToggleButton = Instance.new("TextButton")
    ToggleButton.Size = UDim2.new(1, 0, 1, 0)
    ToggleButton.BackgroundTransparency = 1
    ToggleButton.Text = ""
    ToggleButton.Parent = ToggleFrame

    local ToggleText = Instance.new("TextLabel")
    ToggleText.Size = UDim2.new(0.7, 0, 1, 0)
    ToggleText.Position = UDim2.new(0, 0, 0, 0)
    ToggleText.BackgroundTransparency = 1
    ToggleText.Text = Text
    ToggleText.TextColor3 = Color3.fromRGB(255, 255, 255)
    ToggleText.Font = Enum.Font.Gotham
    ToggleText.TextSize = 12
    ToggleText.TextXAlignment = Enum.TextXAlignment.Left
    ToggleText.Parent = ToggleFrame

    local ToggleBack = Instance.new("Frame")
    ToggleBack.Size = UDim2.new(0, 40, 0, 20)
    ToggleBack.Position = UDim2.new(1, -40, 0.5, -10)
    ToggleBack.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    ToggleBack.BorderSizePixel = 0
    ToggleBack.Parent = ToggleFrame

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 10)
    UICorner.Parent = ToggleBack

    local ToggleDot = Instance.new("Frame")
    ToggleDot.Size = UDim2.new(0, 16, 0, 16)
    ToggleDot.Position = UDim2.new(0, Default and 22 or 2, 0, 2)
    ToggleDot.BackgroundColor3 = Default and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(100, 100, 100)
    ToggleDot.BorderSizePixel = 0
    ToggleDot.Parent = ToggleBack

    local UICorner2 = Instance.new("UICorner")
    UICorner2.CornerRadius = UDim.new(0, 10)
    UICorner2.Parent = ToggleDot

    local State = Default

    ToggleButton.MouseButton1Click:Connect(function()
        State = not State
        TweenService:Create(ToggleDot, TweenInfo.new(0.2), {
            BackgroundColor3 = State and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(100, 100, 100),
            Position = UDim2.new(0, State and 22 or 2, 0, 2)
        }):Play()
        Callback(State)
    end)

    return ToggleFrame
end

function XIRO:CreateSlider(Parent, Text, Min, Max, Default, Callback)
    local SliderFrame = Instance.new("Frame")
    SliderFrame.Size = UDim2.new(1, 0, 0, 50)
    SliderFrame.BackgroundTransparency = 1
    SliderFrame.Parent = Parent

    local SliderText = Instance.new("TextLabel")
    SliderText.Size = UDim2.new(1, 0, 0, 15)
    SliderText.Position = UDim2.new(0, 0, 0, 0)
    SliderText.BackgroundTransparency = 1
    SliderText.Text = Text .. ": " .. Default
    SliderText.TextColor3 = Color3.fromRGB(255, 255, 255)
    SliderText.Font = Enum.Font.Gotham
    SliderText.TextSize = 12
    SliderText.TextXAlignment = Enum.TextXAlignment.Left
    SliderText.Parent = SliderFrame

    local SliderBack = Instance.new("Frame")
    SliderBack.Size = UDim2.new(1, 0, 0, 5)
    SliderBack.Position = UDim2.new(0, 0, 0, 20)
    SliderBack.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    SliderBack.BorderSizePixel = 0
    SliderBack.Parent = SliderFrame

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 3)
    UICorner.Parent = SliderBack

    local SliderFill = Instance.new("Frame")
    SliderFill.Size = UDim2.new((Default - Min) / (Max - Min), 0, 1, 0)
    SliderFill.Position = UDim2.new(0, 0, 0, 0)
    SliderFill.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
    SliderFill.BorderSizePixel = 0
    SliderFill.Parent = SliderBack

    local UICorner2 = Instance.new("UICorner")
    UICorner2.CornerRadius = UDim.new(0, 3)
    UICorner2.Parent = SliderFill

    local SliderButton = Instance.new("TextButton")
    SliderButton.Size = UDim2.new(0, 15, 0, 15)
    SliderButton.Position = UDim2.new((Default - Min) / (Max - Min), -7.5, 0, -5)
    SliderButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    SliderButton.Text = ""
    SliderButton.Parent = SliderBack

    local UICorner3 = Instance.new("UICorner")
    UICorner3.CornerRadius = UDim.new(0, 7.5)
    UICorner3.Parent = SliderButton

    local Dragging = false

    SliderButton.MouseButton1Down:Connect(function()
        Dragging = true
    end)

    UserInputService.InputEnded:Connect(function(Input)
        if Input.UserInputType == Enum.UserInputType.MouseButton1 then
            Dragging = false
        end
    end)

    UserInputService.InputChanged:Connect(function(Input)
        if Dragging and Input.UserInputType == Enum.UserInputType.MouseMovement then
            local X = math.clamp(Mouse.X - SliderBack.AbsolutePosition.X, 0, SliderBack.AbsoluteSize.X)
            local Value = math.floor(Min + (X / SliderBack.AbsoluteSize.X) * (Max - Min))
            
            SliderButton.Position = UDim2.new(X / SliderBack.AbsoluteSize.X, -7.5, 0, -5)
            SliderFill.Size = UDim2.new(X / SliderBack.AbsoluteSize.X, 0, 1, 0)
            SliderText.Text = Text .. ": " .. Value
            
            Callback(Value)
        end
    end)

    return SliderFrame
end

function XIRO:CreateDropdown(Parent, Text, Options, Default, Callback)
    local DropdownFrame = Instance.new("Frame")
    DropdownFrame.Size = UDim2.new(1, 0, 0, 25)
    DropdownFrame.BackgroundTransparency = 1
    DropdownFrame.ClipsDescendants = true
    DropdownFrame.Parent = Parent

    local DropdownButton = Instance.new("TextButton")
    DropdownButton.Size = UDim2.new(1, 0, 0, 25)
    DropdownButton.Position = UDim2.new(0, 0, 0, 0)
    DropdownButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    DropdownButton.Text = Text .. ": " .. Default
    DropdownButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    DropdownButton.Font = Enum.Font.Gotham
    DropdownButton.TextSize = 12
    DropdownButton.Parent = DropdownFrame

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 4)
    UICorner.Parent = DropdownButton

    local OptionsFrame = Instance.new("Frame")
    OptionsFrame.Size = UDim2.new(1, 0, 0, 0)
    OptionsFrame.Position = UDim2.new(0, 0, 0, 30)
    OptionsFrame.BackgroundTransparency = 1
    OptionsFrame.Parent = DropdownFrame

    local UIListLayout = Instance.new("UIListLayout")
    UIListLayout.Padding = UDim.new(0, 2)
    UIListLayout.Parent = OptionsFrame

    local Expanded = false

    for _, Option in pairs(Options) do
        local OptionButton = Instance.new("TextButton")
        OptionButton.Size = UDim2.new(1, 0, 0, 20)
        OptionButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
        OptionButton.Text = Option
        OptionButton.TextColor3 = Color3.fromRGB(255, 255, 255)
        OptionButton.Font = Enum.Font.Gotham
        OptionButton.TextSize = 12
        OptionButton.Parent = OptionsFrame

        local UICorner2 = Instance.new("UICorner")
        UICorner2.CornerRadius = UDim.new(0, 4)
        UICorner2.Parent = OptionButton

        OptionButton.MouseButton1Click:Connect(function()
            DropdownButton.Text = Text .. ": " .. Option
            Callback(Option)
            Expanded = false
            TweenService:Create(OptionsFrame, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, 0)
            }):Play()
            TweenService:Create(DropdownFrame, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, 25)
            }):Play()
        end)
    end

    DropdownButton.MouseButton1Click:Connect(function()
        Expanded = not Expanded
        if Expanded then
            TweenService:Create(OptionsFrame, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, #Options * 22)
            }):Play()
            TweenService:Create(DropdownFrame, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, 25 + #Options * 22 + 5)
            }):Play()
        else
            TweenService:Create(OptionsFrame, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, 0)
            }):Play()
            TweenService:Create(DropdownFrame, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, 25)
            }):Play()
        end
    end)

    return DropdownFrame
end

function XIRO:CreateKeybind(Parent, Text, Default, Callback)
    local KeybindFrame = Instance.new("Frame")
    KeybindFrame.Size = UDim2.new(1, 0, 0, 25)
    KeybindFrame.BackgroundTransparency = 1
    KeybindFrame.Parent = Parent

    local KeybindText = Instance.new("TextLabel")
    KeybindText.Size = UDim2.new(0.7, 0, 1, 0)
    KeybindText.Position = UDim2.new(0, 0, 0, 0)
    KeybindText.BackgroundTransparency = 1
    KeybindText.Text = Text
    KeybindText.TextColor3 = Color3.fromRGB(255, 255, 255)
    KeybindText.Font = Enum.Font.Gotham
    KeybindText.TextSize = 12
    KeybindText.TextXAlignment = Enum.TextXAlignment.Left
    KeybindText.Parent = KeybindFrame

    local KeybindButton = Instance.new("TextButton")
    KeybindButton.Size = UDim2.new(0.3, 0, 1, 0)
    KeybindButton.Position = UDim2.new(0.7, 0, 0, 0)
    KeybindButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    KeybindButton.Text = Default
    KeybindButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    KeybindButton.Font = Enum.Font.Gotham
    KeybindButton.TextSize = 12
    KeybindButton.Parent = KeybindFrame

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 4)
    UICorner.Parent = KeybindButton

    local Listening = false

    KeybindButton.MouseButton1Click:Connect(function()
        Listening = true
        KeybindButton.Text = "..."
        KeybindButton.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    end)

    local Connection
    Connection = UserInputService.InputBegan:Connect(function(Input)
        if Listening and Input.UserInputType == Enum.UserInputType.Keyboard then
            Listening = false
            local Key = Input.KeyCode.Name
            KeybindButton.Text = Key
            KeybindButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
            Callback(Key)
            Connection:Disconnect()
        end
    end)

    return KeybindFrame
end

function XIRO:CreateColorPicker(Parent, Text, Default, Callback)
    local ColorFrame = Instance.new("Frame")
    ColorFrame.Size = UDim2.new(1, 0, 0, 25)
    ColorFrame.BackgroundTransparency = 1
    ColorFrame.Parent = Parent

    local ColorText = Instance.new("TextLabel")
    ColorText.Size = UDim2.new(0.7, 0, 1, 0)
    ColorText.Position = UDim2.new(0, 0, 0, 0)
    ColorText.BackgroundTransparency = 1
    ColorText.Text = Text
    ColorText.TextColor3 = Color3.fromRGB(255, 255, 255)
    ColorText.Font = Enum.Font.Gotham
    ColorText.TextSize = 12
    ColorText.TextXAlignment = Enum.TextXAlignment.Left
    ColorText.Parent = ColorFrame

    local ColorButton = Instance.new("TextButton")
    ColorButton.Size = UDim2.new(0.3, 0, 1, 0)
    ColorButton.Position = UDim2.new(0.7, 0, 0, 0)
    ColorButton.BackgroundColor3 = Default
    ColorButton.Text = ""
    ColorButton.Parent = ColorFrame

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 4)
    UICorner.Parent = ColorButton

    ColorButton.MouseButton1Click:Connect(function()
        -- Simple color picker implementation
        local R = math.random(0, 255)
        local G = math.random(0, 255)
        local B = math.random(0, 255)
        local NewColor = Color3.fromRGB(R, G, B)
        ColorButton.BackgroundColor3 = NewColor
        Callback(NewColor)
    end)

    return ColorFrame
end

function XIRO:CreateAimbotTab()
    self.AimbotContent = Instance.new("Frame")
    self.AimbotContent.Size = UDim2.new(1, 0, 1, 0)
    self.AimbotContent.Position = UDim2.new(0, 0, 0, 0)
    self.AimbotContent.BackgroundTransparency = 1
    self.AimbotContent.Parent = self.ContentContainer

    local AimbotLayout = Instance.new("UIListLayout")
    AimbotLayout.Padding = UDim.new(0, 8)
    AimbotLayout.Parent = self.AimbotContent

    -- Aimbot Toggles
    self:CreateToggle(self.AimbotContent, "Aimbot Enabled", Settings.AimbotEnabled, function(Value)
        Settings.AimbotEnabled = Value
    end)

    self:CreateDropdown(self.AimbotContent, "Aim Type", {"Mouse", "Camera"}, Settings.AimType, function(Value)
        Settings.AimType = Value
    end)

    self:CreateToggle(self.AimbotContent, "Sticky Aim", Settings.StickyAim, function(Value)
        Settings.StickyAim = Value
    end)

    self:CreateToggle(self.AimbotContent, "Team Check", Settings.TeamCheck, function(Value)
        Settings.TeamCheck = Value
    end)

    self:CreateToggle(self.AimbotContent, "Visible Check", Settings.VisibleCheck, function(Value)
        Settings.VisibleCheck = Value
    end)

    self:CreateToggle(self.AimbotContent, "Show FOV Circle", Settings.ShowFOV, function(Value)
        Settings.ShowFOV = Value
    end)

    self:CreateToggle(self.AimbotContent, "Triggerbot", Settings.Triggerbot, function(Value)
        Settings.Triggerbot = Value
    end)

    -- Sliders
    self:CreateSlider(self.AimbotContent, "Smoothness", 5, 100, Settings.Smoothness * 100, function(Value)
        Settings.Smoothness = Value / 100
    end)

    self:CreateSlider(self.AimbotContent, "FOV Size", 10, 300, Settings.FOV, function(Value)
        Settings.FOV = Value
    end)

    self:CreateSlider(self.AimbotContent, "Triggerbot Delay", 0, 500, Settings.TriggerbotDelay * 1000, function(Value)
        Settings.TriggerbotDelay = Value / 1000
    end)

    -- Hit Part Dropdown
    self:CreateDropdown(self.AimbotContent, "Aim Part", {
        "Head", "HumanoidRootPart", "UpperTorso", "LowerTorso", 
        "LeftArm", "RightArm", "LeftLeg", "RightLeg"
    }, Settings.AimPart, function(Value)
        Settings.AimPart = Value
    end)
end

function XIRO:CreateVisualsTab()
    self.VisualsContent = Instance.new("Frame")
    self.VisualsContent.Size = UDim2.new(1, 0, 1, 0)
    self.VisualsContent.Position = UDim2.new(0, 0, 0, 0)
    self.VisualsContent.BackgroundTransparency = 1
    self.VisualsContent.Visible = false
    self.VisualsContent.Parent = self.ContentContainer

    local VisualsLayout = Instance.new("UIListLayout")
    VisualsLayout.Padding = UDim.new(0, 8)
    VisualsLayout.Parent = self.VisualsContent

    -- Visuals Toggles
    self:CreateToggle(self.VisualsContent, "ESP Enabled", Settings.ESPEnabled, function(Value)
        Settings.ESPEnabled = Value
    end)

    self:CreateToggle(self.VisualsContent, "Box ESP", Settings.BoxESP, function(Value)
        Settings.BoxESP = Value
    end)

    self:CreateToggle(self.VisualsContent, "Tracers", Settings.Tracers, function(Value)
        Settings.Tracers = Value
    end)

    self:CreateToggle(self.VisualsContent, "Name ESP", Settings.NameESP, function(Value)
        Settings.NameESP = Value
    end)

    self:CreateToggle(self.VisualsContent, "Distance ESP", Settings.DistanceESP, function(Value)
        Settings.DistanceESP = Value
    end)

    self:CreateToggle(self.VisualsContent, "Health Bar", Settings.HealthBar, function(Value)
        Settings.HealthBar = Value
    end)

    self:CreateToggle(self.VisualsContent, "Team Check", Settings.ESPTeamCheck, function(Value)
        Settings.ESPTeamCheck = Value
    end)

    self:CreateToggle(self.VisualsContent, "Team Color", Settings.ESPTeamColor, function(Value)
        Settings.ESPTeamColor = Value
    end)

    -- Dropdowns and Sliders
    self:CreateDropdown(self.VisualsContent, "Tracer Origin", {
        "Bottom", "Top", "Mouse", "Center"
    }, Settings.TracerOrigin, function(Value)
        Settings.TracerOrigin = Value
    end)

    self:CreateSlider(self.VisualsContent, "Tracer Thickness", 1, 5, Settings.TracerThickness, function(Value)
        Settings.TracerThickness = Value
    end)

    -- Color Pickers
    self:CreateColorPicker(self.VisualsContent, "Box Color", Settings.BoxColor, function(Value)
        Settings.BoxColor = Value
    end)

    self:CreateColorPicker(self.VisualsContent, "Tracer Color", Settings.TracerColor, function(Value)
        Settings.TracerColor = Value
    end)

    self:CreateColorPicker(self.VisualsContent, "Name Color", Settings.NameColor, function(Value)
        Settings.NameColor = Value
    end)

    self:CreateColorPicker(self.VisualsContent, "Distance Color", Settings.DistanceColor, function(Value)
        Settings.DistanceColor = Value
    end)
end

function XIRO:CreateExploitsTab()
    self.ExploitsContent = Instance.new("Frame")
    self.ExploitsContent.Size = UDim2.new(1, 0, 1, 0)
    self.ExploitsContent.Position = UDim2.new(0, 0, 0, 0)
    self.ExploitsContent.BackgroundTransparency = 1
    self.ExploitsContent.Visible = false
    self.ExploitsContent.Parent = self.ContentContainer

    local ExploitsLayout = Instance.new("UIListLayout")
    ExploitsLayout.Padding = UDim.new(0, 8)
    ExploitsLayout.Parent = self.ExploitsContent

    -- Fly Toggle
    self:CreateToggle(self.ExploitsContent, "Fly Enabled", Settings.FlyEnabled, function(Value)
        Settings.FlyEnabled = Value
        if Value then
            EnableFly()
        else
            DisableFly()
        end
    end)

    -- Fly Type Dropdown
    self:CreateDropdown(self.ExploitsContent, "Fly Type", {"Velocity", "Position"}, Settings.FlyType, function(Value)
        Settings.FlyType = Value
        if Settings.FlyEnabled then
            DisableFly()
            EnableFly()
        end
    end)

    -- Fly Speed Slider
    self:CreateSlider(self.ExploitsContent, "Fly Speed", 1, 100, Settings.FlySpeed, function(Value)
        Settings.FlySpeed = Value
    end)

    -- Fly Keybind
    self:CreateKeybind(self.ExploitsContent, "Fly Keybind", Settings.FlyKeybind, function(Value)
        Settings.FlyKeybind = Value
        Keybinds.Fly = Value
    end)

    -- Walkspeed Toggle
    self:CreateToggle(self.ExploitsContent, "Walkspeed Enabled", Settings.WalkspeedEnabled, function(Value)
        Settings.WalkspeedEnabled = Value
        if Value then
            EnableWalkspeed()
        else
            DisableWalkspeed()
        end
    end)

    -- Walkspeed Slider
    self:CreateSlider(self.ExploitsContent, "Walkspeed", 16, 100, Settings.Walkspeed, function(Value)
        Settings.Walkspeed = Value
        if Settings.WalkspeedEnabled then
            EnableWalkspeed()
        end
    end)

    -- Walkspeed Keybind
    self:CreateKeybind(self.ExploitsContent, "Walkspeed Keybind", Settings.WalkspeedKeybind, function(Value)
        Settings.WalkspeedKeybind = Value
        Keybinds.Walkspeed = Value
    end)

    -- Velocity Walkspeed Toggle
    self:CreateToggle(self.ExploitsContent, "Velocity Walkspeed", Settings.VelocityWalkspeed, function(Value)
        Settings.VelocityWalkspeed = Value
    end)

    -- Noclip Toggle
    self:CreateToggle(self.ExploitsContent, "Noclip Enabled", Settings.NoclipEnabled, function(Value)
        Settings.NoclipEnabled = Value
        if Value then
            EnableNoclip()
        else
            DisableNoclip()
        end
    end)

    -- Noclip Keybind
    self:CreateKeybind(self.ExploitsContent, "Noclip Keybind", Settings.NoclipKeybind, function(Value)
        Settings.NoclipKeybind = Value
        Keybinds.Noclip = Value
    end)
end

function XIRO:CreateMiscTab()
    self.MiscContent = Instance.new("Frame")
    self.MiscContent.Size = UDim2.new(1, 0, 1, 0)
    self.MiscContent.Position = UDim2.new(0, 0, 0, 0)
    self.MiscContent.BackgroundTransparency = 1
    self.MiscContent.Visible = false
    self.MiscContent.Parent = self.ContentContainer

    local MiscLayout = Instance.new("UIListLayout")
    MiscLayout.Padding = UDim.new(0, 8)
    MiscLayout.Parent = self.MiscContent

    -- Misc Toggles
    self:CreateToggle(self.MiscContent, "Anti-Cheat Bypass", Settings.AntiCheatBypass, function(Value)
        Settings.AntiCheatBypass = Value
    end)

    self:CreateToggle(self.MiscContent, "Auto Update", Settings.AutoUpdate, function(Value)
        Settings.AutoUpdate = Value
    end)

    self:CreateToggle(self.MiscContent, "Notifications", Settings.Notifications, function(Value)
        Settings.Notifications = Value
    end)

    -- Config System
    local ConfigFrame = Instance.new("Frame")
    ConfigFrame.Size = UDim2.new(1, 0, 0, 25)
    ConfigFrame.BackgroundTransparency = 1
    ConfigFrame.Parent = self.MiscContent

    local ConfigText = Instance.new("TextLabel")
    ConfigText.Size = UDim2.new(0.5, 0, 1, 0)
    ConfigText.Position = UDim2.new(0, 0, 0, 0)
    ConfigText.BackgroundTransparency = 1
    ConfigText.Text = "Config:"
    ConfigText.TextColor3 = Color3.fromRGB(255, 255, 255)
    ConfigText.Font = Enum.Font.Gotham
    ConfigText.TextSize = 12
    ConfigText.TextXAlignment = Enum.TextXAlignment.Left
    ConfigText.Parent = ConfigFrame

    local ConfigDropdown = Instance.new("TextButton")
    ConfigDropdown.Size = UDim2.new(0.5, 0, 1, 0)
    ConfigDropdown.Position = UDim2.new(0.5, 0, 0, 0)
    ConfigDropdown.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    ConfigDropdown.Text = Configs.Current
    ConfigDropdown.TextColor3 = Color3.fromRGB(255, 255, 255)
    ConfigDropdown.Font = Enum.Font.Gotham
    ConfigDropdown.TextSize = 12
    ConfigDropdown.Parent = ConfigFrame

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 4)
    UICorner.Parent = ConfigDropdown

    -- Config Buttons
    local ConfigButtonsFrame = Instance.new("Frame")
    ConfigButtonsFrame.Size = UDim2.new(1, 0, 0, 25)
    ConfigButtonsFrame.BackgroundTransparency = 1
    ConfigButtonsFrame.Parent = self.MiscContent

    local SaveButton = Instance.new("TextButton")
    SaveButton.Size = UDim2.new(0.3, -5, 1, 0)
    SaveButton.Position = UDim2.new(0, 0, 0, 0)
    SaveButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    SaveButton.Text = "Save"
    SaveButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    SaveButton.Font = Enum.Font.Gotham
    SaveButton.TextSize = 12
    SaveButton.Parent = ConfigButtonsFrame

    local LoadButton = Instance.new("TextButton")
    LoadButton.Size = UDim2.new(0.3, -5, 1, 0)
    LoadButton.Position = UDim2.new(0.35, 5, 0, 0)
    LoadButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    LoadButton.Text = "Load"
    LoadButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    LoadButton.Font = Enum.Font.Gotham
    LoadButton.TextSize = 12
    LoadButton.Parent = ConfigButtonsFrame

    local DeleteButton = Instance.new("TextButton")
    DeleteButton.Size = UDim2.new(0.3, -5, 1, 0)
    DeleteButton.Position = UDim2.new(0.7, 5, 0, 0)
    DeleteButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    DeleteButton.Text = "Delete"
    DeleteButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    DeleteButton.Font = Enum.Font.Gotham
    DeleteButton.TextSize = 12
    DeleteButton.Parent = ConfigButtonsFrame

    local UICorner2 = Instance.new("UICorner")
    UICorner2.CornerRadius = UDim.new(0, 4)
    UICorner2.Parent = SaveButton

    local UICorner3 = Instance.new("UICorner")
    UICorner3.CornerRadius = UDim.new(0, 4)
    UICorner3.Parent = LoadButton

    local UICorner4 = Instance.new("UICorner")
    UICorner4.CornerRadius = UDim.new(0, 4)
    UICorner4.Parent = DeleteButton

    -- Config functionality
    SaveButton.MouseButton1Click:Connect(function()
        SaveConfig(Configs.Current)
    end)

    LoadButton.MouseButton1Click:Connect(function()
        LoadConfig(Configs.Current)
    end)

    DeleteButton.MouseButton1Click:Connect(function()
        DeleteConfig(Configs.Current)
    end)
end

function XIRO:CreateNotificationSystem()
    NotificationFrame = Instance.new("Frame")
    NotificationFrame.Size = UDim2.new(0, 300, 0, 0)
    NotificationFrame.Position = UDim2.new(1, -320, 0.5, 0)
    NotificationFrame.BackgroundTransparency = 1
    NotificationFrame.Parent = self.ScreenGui

    local UIListLayout = Instance.new("UIListLayout")
    UIListLayout.Padding = UDim.new(0, 5)
    UIListLayout.Parent = NotificationFrame
end

function XIRO:AddNotification(Text, Duration)
    if not Settings.Notifications then return end
    
    local Notification = Instance.new("Frame")
    Notification.Size = UDim2.new(1, 0, 0, 40)
    Notification.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    Notification.Parent = NotificationFrame

    local UICorner = Instance.new("UICorner")
    UICorner.CornerRadius = UDim.new(0, 4)
    UICorner.Parent = Notification

    local NotificationText = Instance.new("TextLabel")
    NotificationText.Size = UDim2.new(1, -10, 1, -10)
    NotificationText.Position = UDim2.new(0, 5, 0, 5)
    NotificationText.BackgroundTransparency = 1
    NotificationText.Text = Text
    NotificationText.TextColor3 = Color3.fromRGB(255, 255, 255)
    NotificationText.Font = Enum.Font.Gotham
    NotificationText.TextSize = 12
    NotificationText.TextXAlignment = Enum.TextXAlignment.Left
    NotificationText.Parent = Notification

    table.insert(Notifications, Notification)

    task.delay(Duration or 5, function()
        if Notification and Notification.Parent then
            Notification:Destroy()
            for i, v in pairs(Notifications) do
                if v == Notification then
                    table.remove(Notifications, i)
                    break
                end
            end
        end
    end)
end

-- Fly functionality
local flyConnection
local bodyVelocity
local bodyGyro
local flyToggled = false

function EnableFly()
    if flyConnection then flyConnection:Disconnect() end
    
    local character = LocalPlayer.Character
    if not character then return end
    
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end
    
    if Settings.FlyType == "Velocity" then
        -- Velocity fly
        bodyVelocity = Instance.new("BodyVelocity")
        bodyVelocity.Velocity = Vector3.new(0, 0, 0)
        bodyVelocity.MaxForce = Vector3.new(10000, 10000, 10000)
        bodyVelocity.Parent = character:FindFirstChild("HumanoidRootPart") or character:WaitForChild("HumanoidRootPart")
        
        flyConnection = RunService.Heartbeat:Connect(function()
            if not character or not humanoid then
                DisableFly()
                return
            end
            
            local rootPart = character:FindFirstChild("HumanoidRootPart")
            if not rootPart then return end
            
            local camera = workspace.CurrentCamera
            local lookVector = camera.CFrame.LookVector
            local rightVector = camera.CFrame.RightVector
            
            local velocity = Vector3.new(0, 0, 0)
            
            if UserInputService:IsKeyDown(Enum.KeyCode.W) then
                velocity = velocity + lookVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.S) then
                velocity = velocity - lookVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.D) then
                velocity = velocity + rightVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.A) then
                velocity = velocity - rightVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.Space) then
                velocity = velocity + Vector3.new(0, 1, 0)
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.LeftShift) then
                velocity = velocity - Vector3.new(0, 1, 0)
            end
            
            if velocity.Magnitude > 0 then
                velocity = velocity.Unit * Settings.FlySpeed
            end
            
            bodyVelocity.Velocity = velocity
        end)
    else
        -- Position fly
        flyConnection = RunService.Heartbeat:Connect(function()
            if not character or not humanoid then
                DisableFly()
                return
            end
            
            local rootPart = character:FindFirstChild("HumanoidRootPart")
            if not rootPart then return end
            
            local camera = workspace.CurrentCamera
            local lookVector = camera.CFrame.LookVector
            local rightVector = camera.CFrame.RightVector
            
            local movement = Vector3.new(0, 0, 0)
            
            if UserInputService:IsKeyDown(Enum.KeyCode.W) then
                movement = movement + lookVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.S) then
                movement = movement - lookVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.D) then
                movement = movement + rightVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.A) then
                movement = movement - rightVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.Space) then
                movement = movement + Vector3.new(0, 1, 0)
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.LeftShift) then
                movement = movement - Vector3.new(0, 1, 0)
            end
            
            if movement.Magnitude > 0 then
                movement = movement.Unit * Settings.FlySpeed / 10
                rootPart.CFrame = rootPart.CFrame + movement
            end
        end)
    end
end

function DisableFly()
    if flyConnection then
        flyConnection:Disconnect()
        flyConnection = nil
    end
    
    local character = LocalPlayer.Character
    if character then
        if bodyVelocity then
            bodyVelocity:Destroy()
            bodyVelocity = nil
        end
        if bodyGyro then
            bodyGyro:Destroy()
            bodyGyro = nil
        end
    end
end

-- Walkspeed functionality
local walkspeedConnection

function EnableWalkspeed()
    if walkspeedConnection then walkspeedConnection:Disconnect() end
    
    local character = LocalPlayer.Character
    if not character then return end
    
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end
    
    if Settings.VelocityWalkspeed then
        -- Velocity walkspeed
        local bodyVelocity = Instance.new("BodyVelocity")
        bodyVelocity.Velocity = Vector3.new(0, 0, 0)
        bodyVelocity.MaxForce = Vector3.new(10000, 0, 10000)
        bodyVelocity.Parent = character:FindFirstChild("HumanoidRootPart") or character:WaitForChild("HumanoidRootPart")
        
        walkspeedConnection = RunService.Heartbeat:Connect(function()
            if not character or not humanoid then
                DisableWalkspeed()
                return
            end
            
            local rootPart = character:FindFirstChild("HumanoidRootPart")
            if not rootPart then return end
            
            local camera = workspace.CurrentCamera
            local lookVector = camera.CFrame.LookVector
            local rightVector = camera.CFrame.RightVector
            
            local velocity = Vector3.new(0, 0, 0)
            
            if UserInputService:IsKeyDown(Enum.KeyCode.W) then
                velocity = velocity + lookVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.S) then
                velocity = velocity - lookVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.D) then
                velocity = velocity + rightVector
            end
            if UserInputService:IsKeyDown(Enum.KeyCode.A) then
                velocity = velocity - rightVector
            end
            
            if velocity.Magnitude > 0 then
                velocity = velocity.Unit * Settings.Walkspeed
            end
            
            bodyVelocity.Velocity = velocity
        end)
    else
        -- Normal walkspeed
        humanoid.WalkSpeed = Settings.Walkspeed
        
        walkspeedConnection = character.ChildAdded:Connect(function(child)
            if child:IsA("Humanoid") then
                child.WalkSpeed = Settings.Walkspeed
            end
        end)
    end
end

function DisableWalkspeed()
    if walkspeedConnection then
        walkspeedConnection:Disconnect()
        walkspeedConnection = nil
    end
    
    local character = LocalPlayer.Character
    if character then
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid.WalkSpeed = 16 -- Default walkspeed
        end
    end
end

-- Noclip functionality
local noclipConnection
local noclipToggled = false

function EnableNoclip()
    if noclipConnection then noclipConnection:Disconnect() end
    
    local character = LocalPlayer.Character
    if not character then return end
    
    noclipConnection = RunService.Stepped:Connect(function()
        if not character then
            DisableNoclip()
            return
        end
        
        for _, part in pairs(character:GetDescendants()) do
            if part:IsA("BasePart") then
                part.CanCollide = false
            end
        end
    end)
end

function DisableNoclip()
    if noclipConnection then
        noclipConnection:Disconnect()
        noclipConnection = nil
    end
    
    local character = LocalPlayer.Character
    if character then
        for _, part in pairs(character:GetDescendants()) do
            if part:IsA("BasePart") then
                part.CanCollide = true
            end
        end
    end
end

-- Config System
function SaveConfig(Name)
    local configData = {
        Settings = Settings,
        Keybinds = Keybinds
    }
    
    local json = HttpService:JSONEncode(configData)
    writefile("xiro_" .. Name .. ".cfg", json)
    
    if not table.find(Configs.List, Name) then
        table.insert(Configs.List, Name)
    end
    
    XIRO:AddNotification("Config saved: " .. Name)
end

function LoadConfig(Name)
    if not isfile("xiro_" .. Name .. ".cfg") then
        XIRO:AddNotification("Config not found: " .. Name)
        return
    end
    
    local json = readfile("xiro_" .. Name .. ".cfg")
    local configData = HttpService:JSONDecode(json)
    
    Settings = configData.Settings
    Keybinds = configData.Keybinds
    Configs.Current = Name
    
    XIRO:AddNotification("Config loaded: " .. Name)
end

function DeleteConfig(Name)
    if Name == "Default" then
        XIRO:AddNotification("Cannot delete default config")
        return
    end
    
    if isfile("xiro_" .. Name .. ".cfg") then
        delfile("xiro_" .. Name .. ".cfg")
        
        for i, configName in pairs(Configs.List) do
            if configName == Name then
                table.remove(Configs.List, i)
                break
            end
        end
        
        if Configs.Current == Name then
            Configs.Current = "Default"
        end
        
        XIRO:AddNotification("Config deleted: " .. Name)
    else
        XIRO:AddNotification("Config not found: " .. Name)
    end
end

-- Keybind System
UserInputService.InputBegan:Connect(function(Input)
    if Input.UserInputType == Enum.UserInputType.Keyboard then
        local Key = Input.KeyCode.Name
        
        -- Toggle menu with P key
        if Key == "P" then
            XIRO.ScreenGui.Enabled = not XIRO.ScreenGui.Enabled
        end
        
        -- Fly keybind
        if Key == Keybinds.Fly then
            Settings.FlyEnabled = not Settings.FlyEnabled
            if Settings.FlyEnabled then
                EnableFly()
                XIRO:AddNotification("Fly enabled")
            else
                DisableFly()
                XIRO:AddNotification("Fly disabled")
            end
        end
        
        -- Walkspeed keybind
        if Key == Keybinds.Walkspeed then
            Settings.WalkspeedEnabled = not Settings.WalkspeedEnabled
            if Settings.WalkspeedEnabled then
                EnableWalkspeed()
                XIRO:AddNotification("Walkspeed enabled")
            else
                DisableWalkspeed()
                XIRO:AddNotification("Walkspeed disabled")
            end
        end
        
        -- Noclip keybind
        if Key == Keybinds.Noclip then
            Settings.NoclipEnabled = not Settings.NoclipEnabled
            if Settings.NoclipEnabled then
                EnableNoclip()
                XIRO:AddNotification("Noclip enabled")
            else
                DisableNoclip()
                XIRO:AddNotification("Noclip disabled")
            end
        end
    end
end)

-- Initialize menu
XIRO:CreateMenu()

-- FOV Circle
local FOVCircle = Drawing.new("Circle")
FOVCircle.Visible = Settings.ShowFOV
FOVCircle.Color = Settings.FOVColor
FOVCircle.Transparency = Settings.FOVTransparency
FOVCircle.Thickness = Settings.FOVThickness
FOVCircle.Filled = false
FOVCircle.Radius = Settings.FOV
FOVCircle.Position = Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2)

-- Update FOV Circle
RunService.RenderStepped:Connect(function()
    FOVCircle.Visible = Settings.ShowFOV
    FOVCircle.Radius = Settings.FOV
    FOVCircle.Color = Settings.FOVColor
    FOVCircle.Transparency = Settings.FOVTransparency
    FOVCircle.Thickness = Settings.FOVThickness
    FOVCircle.Position = Vector2.new(UserInputService:GetMouseLocation().X, UserInputService:GetMouseLocation().Y)
end)

-- ESP System
local espCache = {}
local newVector2, newColor3, newDrawing = Vector2.new, Color3.new, Drawing.new
local tan, rad = math.tan, math.rad
local round = function(...) 
    local a = {} 
    for i,v in next, table.pack(...) do 
        a[i] = math.round(v) 
    end 
    return unpack(a) 
end

local wtvp = function(...) 
    local a, b = Camera.WorldToViewportPoint(Camera, ...) 
    return newVector2(a.X, a.Y), b, a.Z 
end

local function createEsp(player)
    local drawings = {}
    
    -- Box ESP
    drawings.box = newDrawing("Square")
    drawings.box.Thickness = 1
    drawings.box.Filled = false
    drawings.box.Color = Settings.BoxColor
    drawings.box.Visible = false
    drawings.box.ZIndex = 2

    drawings.boxoutline = newDrawing("Square")
    drawings.boxoutline.Thickness = 3
    drawings.boxoutline.Filled = false
    drawings.boxoutline.Color = newColor3()
    drawings.boxoutline.Visible = false
    drawings.boxoutline.ZIndex = 1
    
    -- Healthbar
    drawings.healthbar = newDrawing("Square")
    drawings.healthbar.Thickness = 1
    drawings.healthbar.Filled = true
    drawings.healthbar.Color = Color3.fromRGB(0, 255, 0)
    drawings.healthbar.Visible = false
    drawings.healthbar.ZIndex = 3
    
    drawings.healthbarOutline = newDrawing("Square")
    drawings.healthbarOutline.Thickness = 1
    drawings.healthbarOutline.Filled = false
    drawings.healthbarOutline.Color = newColor3()
    drawings.healthbarOutline.Visible = false
    drawings.healthbarOutline.ZIndex = 2
    
    -- Tracer
    drawings.tracer = newDrawing("Line")
    drawings.tracer.Thickness = Settings.TracerThickness
    drawings.tracer.Color = Settings.TracerColor
    drawings.tracer.Visible = false
    drawings.tracer.ZIndex = 4
    
    -- Name and Distance text
    drawings.name = newDrawing("Text")
    drawings.name.Size = 13
    drawings.name.Center = true
    drawings.name.Outline = true
    drawings.name.Color = Settings.NameColor
    drawings.name.Visible = false
    drawings.name.ZIndex = 5
    
    drawings.distance = newDrawing("Text")
    drawings.distance.Size = 13
    drawings.distance.Center = true
    drawings.distance.Outline = true
    drawings.distance.Color = Settings.DistanceColor
    drawings.distance.Visible = false
    drawings.distance.ZIndex = 5

    espCache[player] = drawings
end

local function removeEsp(player)
    if rawget(espCache, player) then
        for _, drawing in next, espCache[player] do
            drawing:Remove()
        end
        espCache[player] = nil
    end
end

local function updateEsp(player, esp)
    local character = player and player.Character
    if character then
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
        
        if not humanoid or not humanoidRootPart or humanoid.Health <= 0 then
            for _, drawing in pairs(esp) do
                drawing.Visible = false
            end
            return
        end
        
        local position, visible, depth = wtvp(humanoidRootPart.Position)
        
        -- Update visibility based on settings
        esp.box.Visible = visible and Settings.ESPEnabled and Settings.BoxESP
        esp.boxoutline.Visible = visible and Settings.ESPEnabled and Settings.BoxESP
        esp.healthbar.Visible = visible and Settings.ESPEnabled and Settings.HealthBar
        esp.healthbarOutline.Visible = visible and Settings.ESPEnabled and Settings.HealthBar
        esp.tracer.Visible = visible and Settings.ESPEnabled and Settings.Tracers
        esp.name.Visible = visible and Settings.ESPEnabled and Settings.NameESP
        esp.distance.Visible = visible and Settings.ESPEnabled and Settings.DistanceESP

        if visible then
            -- Box ESP
            local scaleFactor = 1 / (depth * tan(rad(Camera.FieldOfView / 2)) * 2) * 1000
            local width, height = round(4 * scaleFactor, 5 * scaleFactor)
            local x, y = round(position.X, position.Y)
            
            local boxPosition = newVector2(round(x - width / 2, y - height / 2))
            local boxSize = newVector2(width, height)

            esp.box.Size = boxSize
            esp.box.Position = boxPosition
            esp.box.Color = Settings.ESPTeamColor and player.TeamColor.Color or Settings.BoxColor

            esp.boxoutline.Size = boxSize
            esp.boxoutline.Position = boxPosition
            
            -- Healthbar
            if Settings.HealthBar then
                local healthbarWidth = 2
                local healthbarOffset = 1
                
                local healthPercent = humanoid.Health / humanoid.MaxHealth
                
                local healthbarPosition = newVector2(
                    boxPosition.X - healthbarWidth - healthbarOffset,
                    boxPosition.Y
                )
                
                local healthbarSize = newVector2(
                    healthbarWidth,
                    boxSize.Y
                )
                
                local healthbarFillSize = newVector2(
                    healthbarWidth,
                    boxSize.Y * healthPercent
                )
                
                local healthbarFillPosition = newVector2(
                    healthbarPosition.X,
                    healthbarPosition.Y + boxSize.Y - healthbarFillSize.Y
                )
                
                esp.healthbarOutline.Position = healthbarPosition
                esp.healthbarOutline.Size = healthbarSize
                
                esp.healthbar.Position = healthbarFillPosition
                esp.healthbar.Size = healthbarFillSize
                
                local healthColor = Color3.fromRGB(
                    math.floor(255 * (1 - healthPercent)),
                    math.floor(255 * healthPercent),
                    0
                )
                esp.healthbar.Color = healthColor
            end
            
            -- Tracer
            if Settings.Tracers then
                local originPoint
                
                if Settings.TracerOrigin == "Bottom" then
                    originPoint = newVector2(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y)
                elseif Settings.TracerOrigin == "Top" then
                    originPoint = newVector2(Camera.ViewportSize.X / 2, 0)
                elseif Settings.TracerOrigin == "Mouse" then
                    originPoint = newVector2(UserInputService:GetMouseLocation().X, UserInputService:GetMouseLocation().Y)
                else -- Center
                    originPoint = newVector2(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2)
                end
                
                esp.tracer.From = originPoint
                esp.tracer.To = newVector2(x, y)
                esp.tracer.Color = Settings.ESPTeamColor and player.TeamColor.Color or Settings.TracerColor
                esp.tracer.Thickness = Settings.TracerThickness
            end
            
            -- Name and Distance
            if Settings.NameESP then
                esp.name.Position = newVector2(x, y - height / 2 - 15)
                esp.name.Text = player.Name
                esp.name.Color = Settings.ESPTeamColor and player.TeamColor.Color or Settings.NameColor
            end
            
            if Settings.DistanceESP then
                local distance = (LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")) and 
                               (humanoidRootPart.Position - LocalPlayer.Character.HumanoidRootPart.Position).Magnitude or 0
                esp.distance.Position = newVector2(x, y + height / 2 + 5)
                esp.distance.Text = math.floor(distance) .. "m"
                esp.distance.Color = Settings.ESPTeamColor and player.TeamColor.Color or Settings.DistanceColor
            end
        end
    else
        for _, drawing in pairs(esp) do
            drawing.Visible = false
        end
    end
end

-- Initialize ESP
for _, player in next, Players:GetPlayers() do
    if player ~= LocalPlayer then
        createEsp(player)
    end
end

Players.PlayerAdded:Connect(function(player)
    createEsp(player)
end)

Players.PlayerRemoving:Connect(function(player)
    removeEsp(player)
end)

-- Aimbot functionality
local function IsPartVisible(Part)
    if not Settings.VisibleCheck then return true end
    
    local Character = LocalPlayer.Character
    if not Character then return false end
    
    local Head = Character:FindFirstChild("Head")
    if not Head then return false end
    
    local Origin = Head.Position
    local Direction = (Part.Position - Origin).Unit * (Origin - Part.Position).Magnitude
    local RaycastParams = RaycastParams.new()
    RaycastParams.FilterType = Enum.RaycastFilterType.Blacklist
    RaycastParams.FilterDescendantsInstances = {Character, Part.Parent}
    
    local Result = workspace:Raycast(Origin, Direction, RaycastParams)
    return Result == nil or Result.Instance:IsDescendantOf(Part.Parent)
end

local function GetClosestPlayer()
    local ClosestPlayer = nil
    local ShortestDistance = Settings.FOV

    for _, Player in pairs(Players:GetPlayers()) do
        if Player ~= LocalPlayer and Player.Character and Player.Character:FindFirstChild("Humanoid") and 
           Player.Character:FindFirstChild("HumanoidRootPart") and Player.Character.Humanoid.Health > 0 then
            
            if Settings.TeamCheck and Player.Team == LocalPlayer.Team then
                continue
            end

            local Character = Player.Character
            local AimPart = Character:FindFirstChild(Settings.AimPart)
            if not AimPart then continue end
            
            if not IsPartVisible(AimPart) then continue end

            local ScreenPosition, OnScreen = Camera:WorldToViewportPoint(AimPart.Position)
            
            if OnScreen then
                local MousePosition = UserInputService:GetMouseLocation()
                local Distance = (Vector2.new(MousePosition.X, MousePosition.Y) - Vector2.new(ScreenPosition.X, ScreenPosition.Y)).Magnitude
                
                if Distance < ShortestDistance then
                    ShortestDistance = Distance
                    ClosestPlayer = Player
                end
            end
        end
    end
    
    return ClosestPlayer
end

local function AimAt(Player)
    if not Player or not Player.Character then
        return
    end
    
    local Character = Player.Character
    local AimPart = Character:FindFirstChild(Settings.AimPart)
    if not AimPart then return end
    
    local ScreenPosition, OnScreen = Camera:WorldToViewportPoint(AimPart.Position)
    
    if OnScreen then
        local MousePosition = UserInputService:GetMouseLocation()
        local TargetPosition = Vector2.new(ScreenPosition.X, ScreenPosition.Y)
        
        -- Calculate smooth movement
        local Delta = TargetPosition - MousePosition
        local SmoothedDelta = Delta * Settings.Smoothness
        
        -- Move mouse
        mousemoverel(SmoothedDelta.X, SmoothedDelta.Y)
    end
end

-- Triggerbot functionality
local triggerbotConnection

function EnableTriggerbot()
    if triggerbotConnection then triggerbotConnection:Disconnect() end
    
    triggerbotConnection = RunService.RenderStepped:Connect(function()
        if not Settings.Triggerbot then return end
        
        local Character = LocalPlayer.Character
        if not Character then return end
        
        local MouseTarget = Mouse.Target
        if MouseTarget and MouseTarget.Parent then
            local Player = Players:GetPlayerFromCharacter(MouseTarget.Parent)
            if Player and Player ~= LocalPlayer then
                if Settings.TeamCheck and Player.Team == LocalPlayer.Team then
                    return
                end
                
                mouse1click()
                wait(Settings.TriggerbotDelay)
            end
        end
    end)
end

function DisableTriggerbot()
    if triggerbotConnection then
        triggerbotConnection:Disconnect()
        triggerbotConnection = nil
    end
end

-- Main Loop
RunService.RenderStepped:Connect(function()
    -- Update ESP
    for player, drawings in next, espCache do
        if Settings.ESPTeamCheck and player.Team == LocalPlayer.Team then
            continue
        end

        if drawings and player ~= LocalPlayer then
            updateEsp(player, drawings)
        end
    end
    
    -- Aimbot
    if Settings.AimbotEnabled and UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton2) then
        local ClosestPlayer = GetClosestPlayer()
        if ClosestPlayer then
            AimAt(ClosestPlayer)
        end
    end
    
    -- Triggerbot
    if Settings.Triggerbot then
        if not triggerbotConnection then
            EnableTriggerbot()
        end
    else
        if triggerbotConnection then
            DisableTriggerbot()
        end
    end
end)

-- Initial notification
XIRO:AddNotification("XIRO Menu loaded! Press P to toggle.")
