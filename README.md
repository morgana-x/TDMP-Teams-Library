# TDMP-Teams-Library
A library that adds teams to teardown, used in Ship wars

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

See wiki for more details
