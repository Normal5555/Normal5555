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

TabSection:NewSlider("Distance 1-20", "Increase killaura distance", 20, 1, function(val)

	DistVal["Value"] = val

end)

TabSection:NewToggle("No Swing", "Disable killaura swing", function(state)

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

TabSection:NewSlider("Sound 1-0", "Adjust killaura sound", 1, 0, function(val)

	killaurasoundval["Value"] = val

end
