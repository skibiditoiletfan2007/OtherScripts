return function(ChanceToScare)
    local RunService = game:GetService("RunService")
    local ContentProvider = game:GetService("ContentProvider")

    local global = RunService:IsStudio() and shared or getgenv()

    if global.WitheredFoxyDebug then print(ChanceToScare) print("Loaded") end

    local Frames = {
        "rbxassetid://109884994076498";
        "rbxassetid://90429548630704";
        "rbxassetid://86242535481316";
        "rbxassetid://131913864658156";
        "rbxassetid://139552258458088";
        "rbxassetid://89278678784403";
        "rbxassetid://111707013964254";
        "rbxassetid://88678388051684";
        "rbxassetid://132910163580650";
        "rbxassetid://84243439192553";
        "rbxassetid://136108358012365";
        "rbxassetid://102856277494272";
        "rbxassetid://97253969720414";
    }

    local Scaring = false
    local ChanceToScare = ChanceToScare and tonumber(ChanceToScare) or 10000
    local function Jumpscare()
        if not Scaring then
            local DoScare = math.random(1, ChanceToScare)
            if DoScare == 1 then
                Scaring = true
                local Holder = RunService:IsStudio() and game.Players.LocalPlayer.PlayerGui or game.CoreGui
                local ScreenGui = Instance.new("ScreenGui", Holder)
                ScreenGui.IgnoreGuiInset = true
                local Image = Instance.new("ImageLabel", ScreenGui)
                Image.Size = UDim2.new(1, 0, 1, 0)
                Image.BackgroundTransparency = 1
                local Sound = Instance.new("Sound", Holder)
                Sound.SoundId = "rbxassetid://108297983346928"
                Sound.Volume = 5
                Sound:Play()
                game.Debris:AddItem(ScreenGui, 15)
                game.Debris:AddItem(Image, 15)
                game.Debris:AddItem(Sound, 15)
                task.wait(0.4)
                for i,v in Frames do
                    Image.Image = v
                    task.wait(0.03)
                end
                ScreenGui:Destroy()
                Image:Destroy()
                task.delay(1, function()
                    Scaring = false
                end)
            end
        end
    end

    ContentProvider:PreloadAsync(Frames)
    ContentProvider:PreloadAsync({"rbxassetid://108297983346928"})

    local LastTick = tick()
    if global.WitheredFoxy then global.WitheredFoxy:Disconnect() end
    global.WitheredFoxy = RunService.Heartbeat:Connect(function(DeltaTime)
        if tick() - LastTick >= 1 then
            Jumpscare()
            LastTick = tick()
        end
    end)
end
