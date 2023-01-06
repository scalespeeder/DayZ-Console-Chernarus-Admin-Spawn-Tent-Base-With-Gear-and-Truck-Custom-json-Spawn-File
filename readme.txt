DayZ Chernarus "Admin Spawn Tent Base" For Console and PC json Custom Spawner Mod Instructions & Terms Of Use

This custom object spawner json file will spawn in an Admin Tent with truck & parts at 6616.05 / 9051.43 in Chernarus (South of Prud Lake, in the middle of the map).

Limited Testing on PC Chernarus Local Server DAYZ Version 1.19 Jan 2023.

Created by @scalespeeder. Please report bugs & errors to scalespeeder@gmail.com with screenshots.

Many Thanks To Inclement Dab for his amazing DayZ Editor that makes this all possible: https://steamcommunity.com/sharedfiles/filedetails/?id=2250764298

TERMS OF USE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS
OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN
AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH
THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Using these modded xml / json files and instructions could break the functioning of your DAYZ server, requiring a reinstall that would wipe
all player progress.

Using these modded files neccessitates increased regular restarts to prevent server crashing.

It is suggested you thoroughly test your server after applying these files to ensure proper
functioning of your server.

I always recomend you validate your files at: https://www.xmlvalidation.com/ and https://jsonformatter.curiousconcept.com/

There are four parts to implementing this base: Spawning the base; Editing The Truck types Entry; Editing the Admin Spawn Coordinates; removing it all when you're done.
I recommend you read all the instructions before proceeding.

--------------------------

Instructions To Spawn Base:

Click the "Code" button and "Download Zip" on the Github Repository and extract the files on your local PC for access.

(Optional: For advanced users I have included the original DayZ Editor Mod file "chernarusadminspawnbase.dze" which can be imported into DayZ Editor Mod on PC for customisation.)

Ensure your DayZ Server has activated the cfggameplay.json. For console users on Nitrado Servers, go to "General Settings" on your server and tick "Enable cfggameplay.json".

On PC Servers add the following line to your serverDZ.cfg:

enableCfgGameplayFile = 1;

(On some PC servers, including Nitrado, the serverDZ.cfg is "hidden", so you need to enable "expert mode" in settings,
then go to "expert settings", which is the serverDZ.cfg. Stop the server before making changes this way.)

Upload "chernarusadminspawnbase.json" from the extracted files to inside the "custom" folder of the mission directory on your server. This file places the tent and items on your map.
(If you haven't got a "custom" folder, create one.)

Open the cfggameplay.json file in the correct mission file for your server and look for the "objectSpawnersArr" line.

This file tells your server to access your custom file.

Edit it to look like this: 

	"objectSpawnersArr": ["custom/chernarusadminspawnbase.json"],
	
If you already are calling custom jsons to spawn items, seperate the files like this:

	"objectSpawnersArr": ["custom/chernarusadminspawnbase.json","custom/anotherfile.json","custom/differentfile.json"],
	
Save your changes & upload if you need to.

Restart your server and the "Admin Spawn Tent Base" will appear immediatly. When you have spawned in as admin and taken your gear(see below), remove the entry from the "objectSpawnersArr" line,

so it looks like 

"objectSpawnersArr": [""],

or

"objectSpawnersArr": ["custom/anotherfile.json","custom/differentfile.json"],

Then save and restart your server so that the base and it's contents despawn.

----------------------------------------------------------------

Instructions To Ensure Truck Doesn't De-Spawn On Server Restarts:

Open your types.xml file (it'll be in the db folder of your mission directory)

Find the "Truck_01_Covered" entry and replace it with the entry below:

<type name="Truck_01_Covered">
        <nominal>0</nominal>
        <lifetime>28800</lifetime> <!-- lifetime increased to prevent despawn on restart-->
        <restock>1800</restock>
        <min>0</min>
        <quantmin>-1</quantmin>
        <quantmax>-1</quantmax>
        <cost>100</cost>
        <flags count_in_cargo="0" count_in_hoarder="0" count_in_map="1" count_in_player="0" crafted="0" deloot="0"/>
    </type>
	
-------------------------------------------------	
	
Instructions To Make The Admin Spawn At The Base:

Tell your players that the server will be down for maintenance. Stop the server. Change the password (so other players can't get in). Make sure the base files have been uploaded & cfgameplay & types file edited. (See Above)

Find & open your cfgplayerspawnpoints.xml file.

Below <generator_posbubbles> insert the following line:

<pos x="6613.86" z="9054.93" /> <!-- player will spawn near admin tent base south of Prud -->

and "blank off" the rest of the coordinates by placing remark / comment brackets around the rest of the coordinates. The start of a remark / comment bracket is <!-- and the end is -->
so that part of the file should look like this: 

<!--<pos x="6052" z="1868" />
			<pos x="6218" z="2113" />
			<pos x="7080" z="2482" />
			<pos x="7430" z="2589" />
			<pos x="8285" z="2404" />
			<pos x="8659" z="2220" />
			<pos x="8491" z="2458" />
			<pos x="8830" z="2145" />
			<pos x="8212" z="2781" />
			<pos x="6133" z="2021" />
			<pos x="7173" z="2555" />
			<pos x="8340" z="2558" />
			<pos x="8294" z="2915" />
			<pos x="8391" z="2412" />
			<pos x="8057" z="2807" />
			<pos x="8572" z="2302" />
			<pos x="14263" z="13033" />
			<pos x="14339" z="12861" />
			<pos x="13207" z="10428" />
			<pos x="6116" z="1932" />
			<pos x="13227" z="10298" />
			<pos x="13190" z="10227" />
			<pos x="14586" z="13343" />
			<pos x="14410" z="13316" />
			<pos x="13244" z="10138" />
			<pos x="12978" z="9727" />
			<pos x="13084" z="9648" />
			<pos x="13087" z="8441" />
			<pos x="12917" z="9356" />
			<pos x="9193" z="1935" />
			<pos x="12930" z="9276" />
			<pos x="12899" z="9182" />
			<pos x="13000" z="9809" />
			<pos x="14499" z="13309" />
			<pos x="13053" z="9536" />
			<pos x="15135" z="13901" />
			<pos x="13001" z="9497" />
			<pos x="14326" z="13012" />
			<pos x="12997" z="9380" />
			<pos x="9107" z="1918" />
			<pos x="14326" z="13333" />
			<pos x="14606" z="13275" />
			<pos x="15017" z="13892" />
			<pos x="14749" z="13248" />
			<pos x="13048" z="8357" />
			<pos x="12929" z="8578" />
			<pos x="12991" z="8494" />
			<pos x="13082" z="8112" />
			<pos x="13311" z="7028" />
			<pos x="13262" z="7225" />
			<pos x="13488" z="6538" />
			<pos x="12868" z="9054" />
			<pos x="13076" z="8045" />
			<pos x="13542" z="6088" />
			<pos x="13427" z="5547" />
			<pos x="12954" z="8721" />
			<pos x="13429" z="6679" />
			<pos x="13227" z="7366" />
			<pos x="13374" z="6454" />
			<pos x="13536" z="6229" />
			<pos x="13300" z="7123" />
			<pos x="13127" z="8337" />
			<pos x="13169" z="7491" />
			<pos x="13531" z="6155" />
			<pos x="13485" z="5894" />
			<pos x="13528" z="6464" />
			<pos x="13426" z="5747" />
			<pos x="13440" z="5624" />
			<pos x="13439" z="5374" />
			<pos x="13441" z="5262" />
			<pos x="11846" z="3477" />
			<pos x="13587" z="6026" />
			<pos x="13485" z="5996" />
			<pos x="11824" z="3381" />
			<pos x="13084" z="7938" />
			<pos x="12889" z="8792" />
			<pos x="10917" z="2615" />
			<pos x="10427" z="1921" />
			<pos x="10567" z="2031" />
			<pos x="12004" z="3422" />
			<pos x="11083" z="2731" />
			<pos x="9529" z="1791" />
			<pos x="11085" z="2918" />
			<pos x="10820" z="2257" />
			<pos x="10875" z="2518" />
			<pos x="11914" z="3402" />
			<pos x="9691" z="1750" />
			<pos x="12480" z="3567" />
			<pos x="12215" z="3425" />
			<pos x="10862" z="2380" />
			<pos x="9814" z="1781" />
			<pos x="9875" z="1763" />
			<pos x="9621" z="1722" />
			<pos x="11049" z="2801" />
			<pos x="10647" z="2100" />
			<pos x="12354" z="3480" />-->
			
Save and then restart the server. Login, and kill your current character. You should re-spawn at the admin base. Take all the gear you want and fix the truck if necessary. Move away from the base.
Exit the game and stop the server. Open up cfgplayerspawnpoints.xml again, delete the base spawn coordinates & remove the remark / comments brackets from the rest of the comments. Remove the base 
reference from the objectspawnarray line in your cfggameplay.json. Change the password back to what it was. Tell your players that the server is coming out of maintenance mode.

When you restart the server the base will disapear but you'll have all your admin gear.

Enjoy! Thanks, Rob.

Thanks, Rob.
