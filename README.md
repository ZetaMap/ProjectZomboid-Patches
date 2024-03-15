# Project Zomboid Patches
Patches for Project Zomboid, usefull for modders. <br>
The most use of these patches, is for servers.


## API Unlocker
This patch provide an full access of classes of game to make mods more easely.

To unlock all game api, it's very simple, just copy the file ``LuaJavaClassExposer.class`` to your game/server folder, into folder ``java/se/krka/kahlua/integration/expose/``, and restart the game.<br>
You can also make a backup by renaming the old file with the ``.bak`` extension. (if a problem appears in future)

Also to know if a game is unlocked, write a test like this, in your mod file:
```lua
if fullApiAccess then
    -- Do things when we have access to entire game classes
else
    -- Do things when game is not patched
end
```

A method has been created to unlock more java classes, with his path, for lua mods, if needed:
```lua
exposeClass("<java class path>")
-- E.g. exposeClass("java.io.File"), will expose and return the the class File.
-- Useful for managing files with mods.
```
With that, you can literally create your mod or plugin in java, and "import" it in a lua file.

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
    <li>\*Test\*        *(all classes that contains the word "test")*</li>
  </ul>
</details>

## Pluginator
This patch allows you to load plugins. A plugin is a mod but only required for one part, the server or the client, and not required for the other side. <br>
Common use is for servers, to be able to execute code only on the server side (like synchronization, or security) or not to show what the server is doing to clients.

To install the pluginator, it's very simple, just copy the file ``LuaManager.class`` to your game/server folder, into folder ``java/zombie/Lua/``, and restart the game. <br>
You can also make a backup by renaming the old file with the ``.bak`` extension. (if a problem appears in future)

Plugins must be placed in folder ``media/lua/plugins/``, if it doesn't exist, create it.

**Note:** This tool makes the server believe that the plugins that have been loaded, have never been loaded. <br>
It is therefore not possible to reload the plugins with the ``reloadlua <filename>`` command, so you will have to restart the server for this.


## Disclaimer
I never played the game, I just reverse engineered a long time to do these patches. <br>
So don't blame me if any problems arise after installing this. I am not responsible for any damage caused by its use.

I created these tools because I wanted a plugin to automatically shut down my friends' server when no one is connected, and I noticed that the API provided for modders was really poor. <br>
So I recompiled some classes to make modified versions.

And my conclusion is that the game is really poorly coded... Have a nice days PZ devs... =)
