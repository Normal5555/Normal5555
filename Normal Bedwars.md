local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

local Window = Library.CreateLib("Normal Bedwars", "Ocean")


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
