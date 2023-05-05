This guide will explain how to start making your own mods for the game! Also, if you haven't already, be sure to install MelonLoader first which you can find from the sidebar or the home page.
# What you need to know
This guide assumes that you have some basic understanding of the C# programming language and the Unity game engine. If you have no idea what you're doing whatsoever, I'd recommend that you go and follow some tutorials and mess around with the Unity engine first. If you don't want to do that, then you'll probably just have to ask someone who knows what they are doing with C#, like me (Feel free to ping me in the discord server, I'll help you to the best of my ability)

# Installing some programs
## Microsoft Visual Studio 2022
I highly recommend Visual Studio because it is an amazingly powerful IDE, and makes developing mods so much easier. You can download Visual Studio 2022 [here](https://visualstudio.microsoft.com/vs/)

## dnSpy
dnSpy (Dotnet Spy) is a tool that is very helpful in looking through the code, but it doesn't do much that Visual Studio can't do, it's just slightly better. You can download it [here](https://github.com/dnSpy/dnSpy), dnSpy is no longer supported, but it still works well for what we need it for.

# Setting everything up
## Creating the project
First, open Visual Studio. You should be greeted with something that looks like this, but less stuff in the Open recent section

![visual studio startup](https://media.discordapp.net/attachments/1081383511153455217/1081473211297968178/image.png)

In the get started section, find the button that says "Create a new project", and click on it. Inside that window you should see a bunch of project templates. Click on the search bar and search for "Class Library", and click on the one called "Class Library (.NET Framework)" for C#

![Class Library](https://media.discordapp.net/attachments/1081383511153455217/1081475716337631302/image.png)

Once you have selected "Class Library (.NET Framework)", click next and you will be greeted with a screen titled "Configure your new project". Here you can set the name of your mod, set the location it will be put in, and set the version of .NET Framework you want to use. I'm going to name my project "Example Mod". For the version of the .NET Framework, select version 4.8, or you might encounter some problems.

![Configure your new project](https://media.discordapp.net/attachments/1081383511153455217/1081477347997392916/configure_your_new_project.png)

After you have everything set up correctly, click the create button in the bottom right. This will create your project, and it will open up. The first step is to add references to everything you will use in your mod. So, go to the solution explorer, and right click on references, and click "add reference"

![add reference](https://media.discordapp.net/attachments/1081383511153455217/1081478230042746910/image.png)

This will open up a window that looks like this

![reference manager](https://media.discordapp.net/attachments/1081383511153455217/1081478547379593246/image.png)

## Adding References
Click browse in the bottom left, and go to this file location: `[game installation directory]/MelonLoader`. I will now give you a list of a bunch of files to add as references, and their file locations (they will all be in this folder), and you will need to add each one as a reference.
* `0Harmony.dll`
* `MelonLoader.dll`
* `Managed/Assembly-CSharp.dll`
* `Managed/Il2Cppmscorlib`
* `Managed/UnhollowerBaseLib`
* `Managed/UnityEngine`
* `Managed/UnityEngine.CoreModule`
* `Managed/UnityEngine.InputLegacyModule`
* `Managed/UnityEngine.UI`
* `Managed/UnityEngine.UIElementsModule`
* `Managed/UnityEngine.UIModule`

And that should be everything that you will need, if you are missing something, in most cases Visual Studio will actually tell you when you try to reference it, so just add the file that it needs.

## Renaming your main class
Before you go on with the next step, you will need to rename the main class, which by default is just called "Class 1". Open it, and where it says `public class Class1`, replace `Class1` with basically whatever you think will be a suitable name for your main class. For my Debug Mod, I have it renamed to `ModMain`, but it doesn't really matter, as long as you know what it means. After you have renamed it in the code, you might want to rename the file, and you can do so by right clicking on it in the solution explorer, clicking rename and renaming it the same name.

## Setting up the AssemblyInfo

Now go back to visual studio. In the solution explorer, just above the references, you should see a collapsed region called "properties", open that and click on the file called `AssemblyInfo.cs`. It is here where you define the version, mod name, and game for your mod, and by default it should look something like this

![assemblyinfo](https://media.discordapp.net/attachments/1081383511153455217/1081481312768102420/image.png)

In this file you will need to add the following code. Anything that I put in braces (these: {}) you will replace with your own information.
At the top of the script add this:
```cs
using MelonLoader;
using {Your mod namespace};
```
and at the bottom. :
```cs
[assembly: MelonInfo(typeof({Your main mod class}), "{Name of your mod}", "{Version of your mod}", "{Author of the mod (your name)}")]
[assembly: MelonGame("Lychee Game Labs", "Patch Quest")]
```
The following is a snippet of code of how it should look:

```cs
using System.Reflection;
using System.Runtime.CompilerServices;
using System.Runtime.InteropServices;
using MelonLoader;
using Example_Mod;

// General Information about an assembly is controlled through the following
// set of attributes. Change these attribute values to modify the information
// associated with an assembly.
[assembly: AssemblyTitle("Example Mod")]
[assembly: AssemblyDescription("")]
[assembly: AssemblyConfiguration("")]
[assembly: AssemblyCompany("")]
[assembly: AssemblyProduct("Example Mod")]
[assembly: AssemblyCopyright("Copyright ©  2023")]
[assembly: AssemblyTrademark("")]
[assembly: AssemblyCulture("")]

// Setting ComVisible to false makes the types in this assembly not visible
// to COM components.  If you need to access a type in this assembly from
// COM, set the ComVisible attribute to true on that type.
[assembly: ComVisible(false)]

// The following GUID is for the ID of the typelib if this project is exposed to COM
[assembly: Guid("f7ea670f-7e01-4f32-ab16-dac0de56ab6a")]

// Version information for an assembly consists of the following four values:
//
//      Major Version
//      Minor Version
//      Build Number
//      Revision
//
// You can specify all the values or you can default the Build and Revision Numbers
// by using the '*' as shown below:
// [assembly: AssemblyVersion("1.0.*")]
[assembly: AssemblyVersion("1.0.0.0")]
[assembly: AssemblyFileVersion("1.0.0.0")]

[assembly: MelonInfo(typeof(ModMain), "Example Mod", "1.0.0", "Millimedia Games")]
[assembly: MelonGame("Lychee Game Labs", "Patch Quest")] 

```


# Beginning modding
Once you have done this, you are ready to start modding the game.
Head to your main mod class, and at the top write the following line of code
```cs
using MelonLoader;
```
Now, make your main class derive from `MelonMod`. This will give you access to a large amount of methods that you will want to use with your mod. Just keep in mind you can only have one class deriving from MelonMod, otherwise it will just be a part of a different mod.

Let's start with something very simple. Let's make it so that your mod sends a message into the console when it loads. To do this, you will want to override the function `OnInitializeMelon`, so make a new method called `public override void OnInitializeMelon()`, and inside it, simply write `LoggerInstance.Msg($"{whatever you want to write here}");`

So your final code should look something like this

```cs
using MelonLoader;

namespace Example_Mod
{
    public class ModMain : MelonMod
    {
        public override void OnInitializeMelon()
        {
            base.OnInitializeMelon();
            LoggerInstance.Msg("Hello, World!");
        }
    }
}
```

# Building the mod
Building the mod is a bit strange at the moment, I haven't worked out the best way to do it, but for now, this method works. At the top of visual studio, you should see a play button with text that says "start"

![start](https://media.discordapp.net/attachments/1081383511153455217/1081487277466849300/image.png)

If you click that and give it a while, it should give you the following error message

![error](https://media.discordapp.net/attachments/1081383511153455217/1081487521441140786/image.png)

That's completely fine, and is to be expected. Actually, you should be concerned if you don't get that error message. But after you do get it, you should be able to find the mod's .dll file in the following location
`[Your modding environment]/bin/Debug/[yourmodname].dll`
Then you can just copy this file, and paste it into Patch Quest's mod folder, and run the game. Keep an eye on the console, and it _should_ send whatever your message was in the console. If you can't see your console, try and alt-tab to it, because it usually appears behind patch quest.

![the image](https://media.discordapp.net/attachments/1081383511153455217/1081489665435123722/image.png)

# Going Forward
That's the basics of modding Patch Quest. You've created your first mod, and loaded it into the game. It doesn't actually do anything yet, but to learn how to get it to do more things, you can look at the MelonLoader wiki, for everything about how to use MelonLoader, and then this wiki will contain as much information as we can get on the code of Patch Quest, and will tell you what every function, class, and variable does. Hopefully.

If anything hasn't worked, feel free to ask questions, you can go to the modding thread which is currently located in the wiki progress channel in the patch quest discord server and ask whatever you want there, I'll help as best as I can. 

Also if any part of the guide doesn't actually make sense, be sure to tell me so I can modify it so it does. Thank you!

# ModdingUtilities
I have made a mod that you can use to make mods easier, you can find the documentation and downloads here: 
https://github.com/Millipede406/ModdingUtilities




