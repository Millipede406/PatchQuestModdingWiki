In this guide I will explain how to **install** melon loader, install mods and edit mod config, which is basically everything you should need to know to start playing around with mods.

> Also, please note that this guide is based on **windows**, so if you use any other OS, you'll probably have to do some wacky stuff with Wine to get it to work.

# Installing MelonLoader
Luckily, installing MelonLoader is actually very simple, but I will go into detail about it just in case you have some issues. (If this guide doesn't solve the issues you should just ask in the modding thread (inside the wiki progress channel in the patch quest discord).
## Installing the Prerequisites
In order to run MelonLoader you will need to install the following programs
* [Microsoft .NET Framework 3.5 Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=21)
* [Microsoft .NET Framework 4.7.2 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net472)
* [Microsoft .NET Framework 4.8 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net48)

And then you will need either the x64 or x86 of the Microsoft Visual C++ 2015-2019 Redistributable
* [x86](https://aka.ms/vs/16/release/vc_redist.x86.exe)
* [x64](https://aka.ms/vs/16/release/vc_redist.x64.exe)

## Downloading MelonLoader
Once you have everything installed, you should now be able to install MelonLoader. So to start with you will need to download MelonLoader. You will need to install the MelonLoader.Installer.exe file from the github page which I will link [here](https://github.com/LavaGang/MelonLoader/releases/tag/v0.5.7).

Once you have opened this file, it should pop up with a GUI similar to the one shown below

![melonloader installer GUI](https://media.discordapp.net/attachments/1081383511153455217/1081386414555549736/image.png)

In the first field, you will need to find the folder where Patch Quest is installed. If you don't know where Patch Quest is installed, there will be a short guide below
## Locating the Patch Quest installation location
First you will need to open steam, and find Patch Quest in your games menu. This can either be done in the sidebar or through your home page, it doesn't really matter.

![Sidebar](https://media.discordapp.net/attachments/1081383511153455217/1081387253814792272/image.png)

![Home Page](https://media.discordapp.net/attachments/1081383511153455217/1081387331539447880/image.png)

You will then need to right click on Patch Quest and select properties, and a window like this should pop up

![Properties](https://media.discordapp.net/attachments/1081383511153455217/1081387781017833492/image.png)

![Properties Menu](https://media.discordapp.net/attachments/1081383511153455217/1081388051793707068/image.png)

Now navigate to the Local Files tab on the sidebar of the properties menu, and then you should find a button that says Browse... next to some text that tells you how large the game is on your hard drive

![Local Files](https://media.discordapp.net/attachments/1081383511153455217/1081388573946814555/image.png)

Then when you press browse, it should allow you copy the location like this

![Copy File Location](https://media.discordapp.net/attachments/1081383511153455217/1081388983621275699/image.png)

And then that is your Patch Quest installation location.


## Installing MelonLoader

Now that you have done that, you will need to fill out the properties in MelonLoader. You will put the folder that Patch Quest is located in (the folder the .exe is located in, please make sure that you aren't selecting any other folders), you will select the version (as latest most likely), and this is the most important step: **Make sure you set the Game Arch to x64**

And then you should simply be able to hit install, and then you will have installed MelonLoader.

You will now have to run the game, and it should open up with a new GUI, like the one shown in the screenshot below

![MelonLoader start up](https://media.discordapp.net/attachments/1081383511153455217/1081390247813853194/image.png)





# Modding
After you close the game again, you should find a bunch of extra folders have been generated. The main ones you will be using are `Mods`, `UserData`, and maybe `Plugins`.

* `Mods` is where you place your mods. When you download a mod, you should get a .dll file, which you will then place in the mods folder. Just be careful though! **Mods can actually contain viruses**, so just make sure you trust the person who is sending the mod.
* `UserData` is where all the config for your mods will be placed in. With MelonLoader, you will get a file called `MelonConfig.cfg` which is where most of your mod config will be stored. Other bigger mods with lots of config might place their config in a separate file. For example, with my DebugMod, you will find the config in `DebugMod.cfg`.
* And finally, `Plugins` is where you install plugins.

## Getting your hands on some MODS
At the moment we don't have a single place to find mods, but if the modding community gets large enough, at some point we will probably end up creating a new discord server. The best places to find mods will probably be the modding thread in the wiki channel in the patch quest server, and maybe also in the patch quest server forums.
For now, I'll link a page where you will be able to find all of the good mods, but we will probably move it somewhere in the future.
[Get Mods](https://github.com/Millipede406/PatchQuestModdingWiki/wiki/Get-Mods)

# Launching the Vanilla version of the game
Once you have installed mods, chances are that you'll want to play the vanilla game again at some point. And although you could do so by just uninstalling MelonLoader, there is actually a much easier and quicker solution.
First, navigate back to the properties menu (where you found the local files earlier in the guide) and click on the `General` tab

![general tab](https://media.discordapp.net/attachments/1081383511153455217/1081461547186016326/image.png)

Now, all you have to do is type `--no-mods` in the launch options text box as shown below

![--no-mods](https://media.discordapp.net/attachments/1081383511153455217/1081461596657815644/image.png)

It's that easy. And when you want to play with mods again you can just go and remove it.


