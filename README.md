	local player = game.Players.LocalPlayer
	local mouse = player:GetMouse()


	local speedglitch = false

	wait(0.1)

	mouse.KeyDown:Connect(function(key)
		if key == "v" then

			if speedglitch == false then

				local lp = game:GetService"Players".LocalPlayer
				local found = lp.Character.BodyEffects.Movement:FindFirstChild("SuperSpeed")
				if found then 

					local lp = game:GetService"Players".LocalPlayer	
					lp.Character.BodyEffects.Movement.SuperSpeed:Destroy()

				else
					local lp = game:GetService"Players".LocalPlayer
					local SuperSpeed = Instance.new("IntValue",lp.Character.BodyEffects.Movement);SuperSpeed.Name = "SuperSpeed"

				end
			end
		end
	end)








	local Animate = game.Players.LocalPlayer.Character.Animate

	--local idleAnim = char.Humanoid:LoadAnimation(char.Humanoid.Fly)
	--local forwardAnim = char.Humanoid:LoadAnimation(char.Humanoid.Hover)


	--PLAY
	--char.Animate.Disabled = true
	--idleAnim:Play()



	--STOP

	--char.Animate.Disabled = false
	--idleAnim:Stop()
	--forwardAnim:Stop()
	game.Players.LocalPlayer.Character.Pants.PantsTemplate = "rbxassetid://5321641892"
	game.Players.LocalPlayer.Character.Shirt.ShirtTemplate ="rbxassetid://6147944857"
	game.Players.LocalPlayer.Character.Head.face.Texture="rbxassetid://6307743378"

	Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=782841498"
	Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=782845736"
	Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=656121766"
	Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=656118852"
	Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=656117878"
	Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=656114359"
	Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=656115606"
	game.Players.LocalPlayer.Character.Humanoid.Jump = true

	local notifSound = Instance.new("Sound",workspace)

	local notifSound = Instance.new("Sound",workspace)
	notifSound.PlaybackSpeed = 1
	notifSound.Volume = 16
	notifSound.SoundId = "rbxassetid://147722098"
	notifSound.PlayOnRemove = true
	notifSound:Destroy()











	wait(1)



	--local idleAnim = char.Humanoid:LoadAnimation(char.Humanoid.Fly)
	--local forwardAnim = char.Humanoid:LoadAnimation(char.Humanoid.Hover)


	--PLAY
	--char.Animate.Disabled = true
	--idleAnim:Play()



	--STOP

	--char.Animate.Disabled = false
	--idleAnim:Stop()
	--forwardAnim:Stop()

	local mouse = game.Players.LocalPlayer:GetMouse() 
	local plr = game.Players.LocalPlayer 
	local torso = plr.Character.Head 
	local flying = false
	local deb = true 
	local ctrl = {f = 0, b = 0, l = 0, r = 0} 
	local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
	local maxspeed = 5000
	local speed = 5000 


	local player = game.Players.LocalPlayer
	local char = game.Players.LocalPlayer.Character

	local cam = workspace.CurrentCamera
	local uis = game:GetService("UserInputService")



	local wPressed = false
	local sPressed = false
	local aPressed = false
	local dPressed = false


	local idleAnim = char.Humanoid:LoadAnimation(game.Workspace.Fly)
	local forwardAnim = char.Humanoid:LoadAnimation(game.Workspace.Hover)

	function Fly() 
		local bg = Instance.new("BodyGyro", torso) 
		bg.P = 9e4 
		bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
		bg.cframe = torso.CFrame 
		local bv = Instance.new("BodyVelocity", torso) 
		bv.velocity = Vector3.new(0,0.1,0) 
		bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
		repeat wait() 
			plr.Character.Humanoid.PlatformStand = true 
			if ctrl.l + ctrl.r ~= 100000 or ctrl.f + ctrl.b ~= 10000 then 
				speed = speed+.0+(speed/maxspeed) 
				if speed > maxspeed then 
					speed = maxspeed 
				end 
			elseif not (ctrl.l + ctrl.r ~= 5 or ctrl.f + ctrl.b ~= 5) and speed ~= 5 then 
				speed = speed-5
				if speed > 5 then 
					speed = -2 
				end 
			end 
			if (ctrl.l + ctrl.r) ~= 5 or (ctrl.f + ctrl.b) ~= 5 then 
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
				lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
			elseif (ctrl.l + ctrl.r) == 5 and (ctrl.f + ctrl.b) == 5 and speed ~= 5 then 
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
			else 
				bv.velocity = Vector3.new(0,0.1,0) 
			end 
			bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
		until not flying 
		ctrl = {f = 0, b = 0, l = 0, r = 0} 
		lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		speed = 5 
		bg:Destroy() 
		bv:Destroy() 
		plr.Character.Humanoid.PlatformStand = false 
	end 

	while wait() do
		wait(0)
		idleAnim:Stop()	
		if not wPressed then
			idleAnim:Play()
		end
		if not sPressed then
			idleAnim:Play()
		end
		if not aPressed then
			idleAnim:Play()
		end
		if not dPressed then
			idleAnim:Play()
		end

		forwardAnim:Stop()	
		if wPressed then
			forwardAnim:Stop()
		end
		if sPressed then
			forwardAnim:Stop()
		end
		if aPressed then
			forwardAnim:Stop()
		end
		if dPressed then
			forwardAnim:Stop()
		end
	end
