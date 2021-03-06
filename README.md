# Halo Custom Edition

[![**Download Halo.zip**](https://raw.githubusercontent.com/HaloCustomEdition/Halo/master/page/Halo-Download.png)](http://54.171.67.203/Halo.zip)

The zip file includes these files and folders:

* **Example_Modded_Server** - Basic server setup.
* **Halo Medals** - Halo client medals.
* **server_scripts** - Lua scripts and sever configs.
* **sapp_ce** - Latest sapp server release.
* **Universal_UI_Version_1.1** - Latest release of the popular UI.
* **Halo Custom Edition.zip** - Halo version 1.10 with HAC 2 and Universal UI.
* **documentations** - Good documentations for Halo CE.

# Halo client

Extract the `Halo Custom Edition.zip` on your computer.

### medals, maps, and ui

Run `Halo Custom Edition v110\redist\msxmlenu.msi`.

Copy the custom maps files from your computer to `Halo Custom Edition\maps\`.

Create a shortcut on your desktop with this link

    "C:\Halo Custom Edition v110\haloce.exe" -vidmode 1920,1080,60 -console

Now run halo with the shortcut and create a game profile.

Then close halo and follow these next steps.

Copy the zip files from `Halo Medals` to `%USERPROFILE%\Documents\My Games\Halo CE\hac\packs\` (Create the folder packs if necessary).

Now start halo again.

Open the console with `§`.

In the console type `optic load haloreach` and `custom chat 1`.

### troubleshooting

**CD key error** - If you play Halo via LAN make sure to install a CD key by running the install batch.

    Halo Custom Edition v110\HALO CE CD KEYS\Install_Uninstall.bat

If you still experience this error, delete the `%USERPROFILE%\Documents\My Games\Halo CE\` folder.

**Invalid network adress** - This error occurs when starting halo without internet access. Simply ignore this error and click on the running Halo in the taskbar.

# Halo server

Install the Halo client.

Copy the folder content of `Example_Modded_Server\My Games\Halo CE\` to ` `%USERPROFILE%\Documents\My Games\Halo CE\`.

Copy the folder content of `Example_Modded_Server\Halo CE\` to `Halo Custom Edition v110`.

Finally copy the content of `sapp_ce\` to `Halo Custom Edition v110`.

Run the server with `haloceded.exe`.

### troubleshooting

**Halo client and server on the same machine** - If you run Halo client and server on the same machine make sure to use a different client port with the Halo client.

## mods and more

Remember:
* The sapp init file is located here `%USERPROFILE%\Documents\My Games\Halo CE\sapp\init.txt`.
* To enable Lua scripting make sure the `lua 1` option is in the sapp init file.

### map voting
Enable map voting.
Copy the file `server_scripts\mapvoting.txt` to `%USERPROFILE%\Documents\My Games\Halo CE\sapp\`.

Add `mapvote 1` to the sapp init file.

### Sprinting
Double tap the forward key to run faster. If you sprint for too long, you will become exhausted and run slower.

Copy the file `server_scripts\Sprinting\sprinting.lua` to `%USERPROFILE%\Documents\My Games\Halo CE\sapp\lua\`.

Add this line to the sapp init file:

    lua_load sprinting

### Combo Messages
This script does is the same thing that an events kill spree messages would do but, it sends it to the console instead and you can choose the alignment of spree or combo message that can be said.

Copy the script file `server_scripts\Combo Messages\combo_messages.lua` to `%USERPROFILE%\Documents\My Games\Halo CE\sapp\lua\`.

Add this line to the sapp init file:

    lua_load combo_messages

## server administration

Add the first user as admin with password halo and admin privileges level 4.

    admin add 1 "halo" 4

# Build

The Halo download package is build every 24 hours.

To make build on your own follow the steps below:

First install these programms:

* zip
* git-lfs

Clone the Halo repository.

    cd /usr/local/src/
    sudo git clone https://github.com/HaloCustomEdition/Halo.git

Edit the file.

    sudo vi /etc/cron.daily/halo-build.sh

And add these lines.

    #!/bin/sh

    sudo git -C /usr/local/src//Halo pull
    cd /usr/local/src/Halo
    sudo zip -FSr /var/www/54.171.67.203/Halo.zip . -x ".travis.yml" "*.git*" "gulpfile.js" "deploy.sh" "package.json" "*out*" "*node_modules*" "*page*"


And make it executable

    sudo chmod +x /etc/cron.daily/halo-build.sh

From now on your server updates the Halo repository and creates a new zip file daily.

### github pages

The Halo github page is updated with Travis CI.

[![Build Status](https://travis-ci.org/HaloCustomEdition/Halo.svg)](https://travis-ci.org/HaloCustomEdition/Halo)

# Source

http://xhalo.tk/  
http://opencarnage.net/index.php?/forum/50-halo-server-scripts/  
https://gist.github.com/domenic/ec8b0fc8ab45f39403dd  
http://www.spritecloud.com/2015/04/complete-setup-guide-for-ruby-cucumber-and-watir-on-windows/
