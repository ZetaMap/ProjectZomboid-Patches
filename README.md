# Project Zomboid Patches
Patches for Project Zomboid, usefull for modders.


## API Unlocker
This patch provide a full access of classes of game, to make mods more easely.

To unlock all game api: 
 * backup the old file by adding the ``.bak`` extension.
 * copy the file ``LuaJavaClassExposer.class`` into the folder ``java/se/krka/kahlua/integration/expose/`` (or ``se/krka/kahlua/integration/expose/`` for client)

To know if a game api is unlocked, write a simple test, like this, in your mod file:
```lua
if fullApiAccess then
    -- Do things when we have access to entire game classes
else
    -- Do things when game is not patched
end
```

A method has been created to unlock more classes, with his path:
```lua
exposeClass("<java class path>")
-- E.g. exposeClass("java.io.File"), will expose and return the the class 'File'.
-- Useful for managing files with mods.
```
With this you can, for example, create your mod in java, and "import" it into a lua file, by exposing its main class and calling the main function.

**Note:** Some classes and packages are ignored to avoid errors.
<details>
  <summary>Ignored things</summary>

  **Ignored packages:**
  <ul>
    <li>org.lwjglx.opengl</li>
    <li>org.junit</li>
    <li>astar.tests</li>
    <li>zombie.iso</li>
    <li>zombie.core.opengl</li>
  </ul>


  **Ignored classes:**
  <ul>
    <li>KahluaConverterManager</li>
    <li>LuaCompiler</li>
    <li>ActionContext</li>
    <li>PacketTypes</li>
    <li>CustomPerks</li>
    <li>ItemPickerJava</li>
    <li>GameWindow</li>
    <li>ServerGUI</li>
    <li>MainScreenState</li>
    <li>ModelManager</li>
    <li>SpawnRegions</li>
    <li>test  (all classes that contains the word "test")</li>
  </ul>
</details>


## Pluginator
This patch allows you to load plugins. A plugin is a mod but only required for one side, the server or the client. <br>
Common use is for servers, to be able to run private tasks, like players syncs or security stuff, without the client having the mod for it.

To install the pluginator:
 * backup the old file by adding the ``.bak`` extension.
 * copy the file ``LuaManager.class`` into the folder ``java/zombie/Lua/`` (or ``zombie/Lua/`` for client)

Plugins must be placed in folder ``media/lua/plugins/``. If the folder doesn't exist, create it.

**Note:** This tool makes the server believe that the plugins have never been loaded. <br>
It is therefore not possible to reload the plugins with the ``reloadlua <filename>`` command, you will need to restart the server for this.


## Disclaimer
I never played the game, I just reverse engineered a lonnng time to do these patches. <br>
So don't blame me if any problems arise after installing this. I am not responsible for any damage caused by its use.

Also, I will not provide the method used to decompile and recompile the game files, to avoid problems with this repository. <br>
So do your own research.


## Why these patches?
Because I wanted a plugin to automatically shut down my friends' server when no one is connected, and I noticed that the API provided for modders was really poor. <br>
So I recompiled some classes to make modified versions.

And my conclusion is that the game is really poorly coded... Have a nice days PZ devs... =)
