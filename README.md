# -- Fix lag
local function removeEffectsAndTexturesFrom(object)
    for _, obj in pairs(object:GetDescendants()) do
        -- Các loại hiệu ứng thường gặp
        if obj:IsA("ParticleEmitter") or
           obj:IsA("Trail") or
           obj:IsA("Fire") or
           obj:IsA("Smoke") or
           obj:IsA("Sparkles") or
           obj:IsA("PointLight") or
           obj:IsA("SurfaceLight") or
           obj:IsA("SpotLight") then
            pcall(function() obj:Destroy() end)
        end

        
        if obj:IsA("SurfaceAppearance") or
           obj:IsA("Decal") or
           obj:IsA("Texture") then
            pcall(function() obj:Destroy() end)
        end
    end
end


local targets = {
    workspace,
    game:GetService("Lighting"),
    game:GetService("ReplicatedFirst"),
    game:GetService("ReplicatedStorage"),
    game:GetService("StarterGui"),
    game:GetService("StarterPack"),
    game:GetService("StarterPlayer"),
    game:GetService("Players"),
    game:GetService("Workspace").Terrain
}


for _, area in pairs(targets) do
    removeEffectsAndTexturesFrom(area)
end
