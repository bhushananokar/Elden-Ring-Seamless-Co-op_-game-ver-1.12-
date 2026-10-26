# Elden Ring Seamless Co-op Setup Guide

## Required Stuff

- Goldberg steam Emulator: https://mr_goldberg.gitlab.io/goldberg_emulator/
- Seamless Co-op mod (ver 1.7.2): https://github.com/yuiamoroll/EldenRingSeamlessCoopRelease/releases/tag/v1.7.2
- Elden-Ring ver 1.12
- Zero Tier: https://www.zerotier.com/download/
- Fix for seamless co.op: https://github.com/cfrBernard/Seamless-coop-fix
- Source for the steam_emu and appid files: https://github.com/K3V1991/How-to-install-Seamless-Co-Op-Mod-for-Elden-Ring

## Steps:

1. Make sure you have the ver 1.12 of the game above listed mod version works for that version of game only .
2. download the official seamless coop mod from the github mirror given above (file name:ersc.zip)
3. download the goldberg steam emulator latest version from the above link
4. donload zero tier on all the systems wich will be joining to play the game

## Zero Tier setup:

After download only one person has to login on the zero tier website

1. Login on the website
2. create an organization
3. provide the org id to users who want to connect
4. (on users side) in task bar hidden icons click on the zerotier logo
5. (on users side) Click join new network
6. (on users side) paste the 16 digit id you copied from the org there
7. (back to the website) authorize the users who tried to connect using your 16 digit code
8. the host (person who logged into the website) will also have to perform steps 4 to 7 for his system

**NOTE:** Ensure that broadcast is turned on for your org (under network -> your_org_name->settings->multicast->broadcast toggle)

## goldberg setup:

1. Download and extract goldberg at some location
2. go the the location of your eldenring.exe file.
3. here you will find a steam_api64.dll file rename it to steam_api.original(you can rename it to anything else , this is a backup dll for us)
4. in the extracted goldberg emu folder , you will find another steam_api64.dll copy it and paste it to the folder from step 2
5. now press windows + R and type %appdata% in it and hit enter, this will open  AppData/Roaming folder
6. here open folder named goldberg steamemu save in there open settings
7. open account_name.txt , here enter any account name you want
8. open user_steam_id.txt , you will have a number here change it a bit (ensure that every player has a different number)
9. ensure that the listen_port.txt says 47584
10. download steam_emu.ini, steam_appid.txt from Fix for seamless co.op from required stuff
11. go back to folder from step 2, add the steam_emu.ini, steam_appid.txt you just downloaded and steam_interfaces.txt(present in the files folder of this repo NOTE: this might not be necessary but add it to be on the safer side)  to it.
12. create a new folder named steam_settings in the same folder from the earlier step
13. inside this steam_settings folder add the custom_broadcast.txt file from the files folder of the repo
14. inside this file every player of every other player (no need to add your own ip) you will find the ips under your the zero tier org

## seamless coop setup

1. download and extract the seamless coop from the link given above
2. copy the extracted content and paste it to the folder containing your eldenring.exe file
3. now in the folder containing you eldenring.exe you will see 2 additional things (i. A folder named SeamlessCoop ii. an exe file named ersc_launcher.exe )
4. open seamlesscoop folder , there open the ersc_settings.ini file in notepad and set a password for your coop session (all players should have the same password).

## Firewall setting:

1. Open powershell as admin
2. run the following commands in it

```powershell
New-NetFirewallRule -DisplayName "Elden Ring UDP In" -Direction Inbound -Protocol UDP -LocalPort 47584 -Action Allow -Profile Any
New-NetFirewallRule -DisplayName "Elden Ring TCP In" -Direction Inbound -Protocol TCP -LocalPort 47584 -Action Allow -Profile Any
New-NetFirewallRule -DisplayName "Elden Ring UDP Out" -Direction Outbound -Protocol UDP -RemotePort 47584 -Action Allow -Profile Any
```

## bypassing old version check of ersc_launcher

1. download the file named LAUNCH HERE AS ADMIN.bat Fix for seamless co.op from required stuff
2. paste that file in the folder containing your ersc_launcher.exe (Note this should be the same folder which contains your eldenring.exe)\
3. run this file as admin(this should start the game)

## In-Game:

1. Complete the tutorial part, and get to first site of grace (the one infront of vaare)
2. Rest at this grace , this should give you all the items required for playing coop
3. the host must use tiny great pot item to open world for wanderers
4. others should use the Effigy of Malenia to join the session

---

## Credits & References

- **Goldberg Steam Emulator:** https://mr_goldberg.gitlab.io/goldberg_emulator/
- **Seamless Co-op Mod (v1.7.2):** https://github.com/yuiamoroll/EldenRingSeamlessCoopRelease/releases/tag/v1.7.2
- **ZeroTier:** https://www.zerotier.com/download/
- **Seamless Co-op Fix:** https://github.com/cfrBernard/Seamless-coop-fix
- **Configuration files and reference guide:** https://github.com/K3V1991/How-to-install-Seamless-Co-Op-Mod-for-Elden-Ring
