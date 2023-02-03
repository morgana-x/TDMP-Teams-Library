# TDMP-Teams-Library
A library that adds teams to teardown

Paste this file in your tdmp api folder, and then include it like #include "tdmp/teams.lua"


# Getting Started

here is the basics of creating a team:
either paste this in the file that includes the teams.lua or inside of teams.lua

TEAM_RED = createTeam({
    name = "Red",
    description = "",
    color = {1,0,0}
})

The returned variable is the integer id of the team, you can change all the values there to whatever you like

You could then use SetDefaultTeam(TEAM_RED) to make this team the default team players get when they join


Here is some HUD functions that might come in handy when using this library

function drawHudCore()
     UiPush()
     UiFont("bold.ttf", 40)
     local col = TeamColor(GetTeam(TDMP_LocalSteamID)) or {1,1,1}
     UiColor(col[1],col[2],col[3])
     UiTranslate(20, UiHeight() - UiFontHeight())
     UiText( TeamName(GetTeam(TDMP_LocalSteamID)))
end

function drawPlayerInfo() -- wow coloured names for teams???
    if  ( GetBool("savegame.mod.tdmp.disableplayernicks") or GetBool("tdmp.forcedisablenicks") ) then return end 
    local cam = GetPlayerCameraTransform()
    local dir = GetAimDirection(cam)

    Ballistics:RejectPlayerEntities()
    local ply = TDMP_RaycastPlayer(cam.pos, dir, false, 3)
    
    if not ( ply and Player(ply):IsVisible())  then return end
    local col = TeamColor(GetTeam(ply)) or {1,1,1}
    if not col then return end
    UiPush()
            UiAlign("center middle")
            UiTranslate(UiCenter(), UiMiddle() + 18)
            UiColor(col[1], col[2], col[3], 1)
            UiFont("bold.ttf", 18)
            UiText( ply.nick)
    UiPop()
end
