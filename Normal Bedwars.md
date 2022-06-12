local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

local Window = Library.CreateLib("Normal Bedwars", "Ocean")

local killauraswing = {["Enabled"] = true}

local killaurasound = {["Enabled"] = true}

local killaurahitdelay = {["Value"] = 2}

local killaurasoundval = {["Value"] = 1}

local speedval = {["Value"] = 1}

local testtogttt = {["Value"] = 20}

local ACC1

local ACC2

local antivoidtransparent = {["Value"] = 50}

local antivoidcolor = {["Hue"] = 0.93, ["Sat"] = 1, ["Value"] = 1}

local reachval = {["Value"] = 18}

local autoclick = {["Enabled"] = true}

local origC0 = game.ReplicatedStorage.Assets.Viewmodel.RightHand.RightWrist.C0

local killaurafirstpersonanim = {["Value"] = true}

local killauraanimval = {["Value"] = "Cool"}

Tab1Section:NewToggle("Speed Anticheat Bypasser", "click to activate", function(state)

	if state then

		BindToStepped("CFrameWalkSpeed", 1, function(time, delta)

			if entity.isAlive then

				local newpos = (lplr.Character.Humanoid.MoveDirection  * (speedval["Value"] - lplr.Character.Humanoid.WalkSpeed)) * delta

				local raycastparameters = RaycastParams.new()

				raycastparameters.FilterDescendantsInstances = {lplr.Character}

				local ray = workspace:Raycast(lplr.Character.HumanoidRootPart.Position, newpos, raycastparameters)

				if ray then newpos = (ray.Position - lplr.Character.HumanoidRootPart.Position) end

				lplr.Character.HumanoidRootPart.CFrame = lplr.Character.HumanoidRootPart.CFrame + newpos

			end

		end)

	else

		UnbindFromStepped("CFrameWalkSpeed")

	end

end)

Tab1Section:NewSlider("Speed 1-42", "Adjust CFrame speed", 42, 1, function(s)

	speedval["Value"] = s

end)

TabSection:NewToggle("KillAura", "Autoswing the sword if someone is near you", function(state)

	if state then

		BindToStepped("Killaura", 1, function()

			if entity.isAlive then

				KillauraRemote()

			end

		end)

	else

		UnbindFromStepped("Killaura")

	end

end)

Tab1Section:NewSlider("Distance 1-20", "Increase killaura distance", 20, 1, function(val)

	DistVal["Value"] = val

end)

Tab1Section:NewToggle("No Swing", "Disable killaura swing", function(state)

	if state then

		if killauraswing["Enabled"] == true then

			killauraswing["Enabled"] = false

		end

	else

		if killauraswing["Enabled"] == false then

			killauraswing["Enabled"] = true

		end

	end

end)

Tab1Section:NewSlider("Sound 1-0", "Adjust killaura sound", 1, 0, function(val)

	killaurasoundval["Value"] = val

end

Tab1Section:NewToggle("No Fall Damage", "click activate mo fall dmg", function(callback)

    local nofall = true

    if callback then

        if nofall then

            spawn(function()

                repeat

                    wait()

                    if nofall == false then

                        return end

                        game:GetService("ReplicatedStorage").rbxts_include.node_modules.net.out._NetManaged.GroundHit:FireServer()

                    until nofall == false

                end)

            end

    else

        local nofall = false

    end

end
