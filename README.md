-- Fast Mode Script for Blox Fruits

local FastMode = true -- Set to true to enable Fast Mode

if FastMode then
    game.Players.LocalPlayer.PlayerScripts.FastMode = true

    local function RemoveTexture(model)
        if model:IsA("Model") then
            for _, part in ipairs(model:GetDescendants()) do
                if part:IsA("BasePart") then
                    part.Material = Enum.Material.SmoothPlastic
                    part.Transparency = 1.0
                end
            end
        end
    end

    local function OptimizeModel(model)
        if model:IsA("Model") then
            for _, part in ipairs(model:GetDescendants()) do
                if part:IsA("BasePart") then
                    part.Material = Enum.Material.SmoothPlastic
                    part.Transparency = 1.0
                end
            end
        end
    end

    local function OptimizeCharacter(character)
        if character then
            for _, part in ipairs(character:GetDescendants()) do
                if part:IsA("BasePart") then
                    part.Material = Enum.Material.SmoothPlastic
                    part.Transparency = 1.0
                end
            end
        end
    end

    local function OptimizeWorld()
        for _, part in ipairs(game.Workspace:GetDescendants()) do
            if part:IsA("BasePart") then
                part.Material = Enum.Material.SmoothPlastic
                part.Transparency = 1.0
            end
        end
    end

    local function ApplyFastMode()
        OptimizeWorld()
        OptimizeCharacter(game.Players.LocalPlayer.Character)

        local function RemoveTextures(model)
            RemoveTexture(model)
            for _, child in ipairs(model:GetChildren()) do
                RemoveTextures(child)
            end
        end

        for _, folder in ipairs(game.Workspace:GetChildren()) do
            if folder.Name == "Decals" then
                folder:ClearAllChildren()
            end
        end

        for _, folder in ipairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
            if folder:IsA("Model") then
                RemoveTextures(folder)
            end
        end

        for _, folder in ipairs(game.Players.LocalPlayer.Character:GetChildren()) do
            if folder:IsA("Model") then
                RemoveTextures(folder)
            end
        end
    end

    ApplyFastMode()
end
