# Project Zomboid Patches
Patches for Project Zomboid, usefull for modders. <br>
The most use of these patches, is for servers.


## API Unlocker
This patch provide an full access of classes of game to make mods more easely.

To unlock all game api, it's very simple, just copy the file ``LuaJavaClassExposer.class`` to your game/server folder, into folder ``java/se/krka/kahlua/integration/expose/``, and restart te game.<br>
You can also make a backup by renaming the old file with the ``.bak`` extension. (if a problem appears in future)

Also to know if a game is unlocked, use write a test like this, in your mod file:
```lua
if fullApiAccess then
    -- Do things when we have access to entire game classes
    -- code....
else
    -- Do things when game is not patched
    -- code....
end
```

**Note:** Some classes and packages are ignored to avoid errors.
<details>
  <summary>Ignored things</summary>

  Ignored packages: <br>
    - org.lwjglx.opengl <br>
    - org.junit <br>
    - astar.tests <br>
    - zombie.iso <br>
    - zombie.core.opengl <br>

  Ignored classes: <br>
    - KahluaConverterManager <br>
    - LuaCompiler <br>
    - ActionContext <br>
    - PacketTypes <br>
    - CustomPerks <br>
    - ItemPickerJava <br>
    - GameWindow <br>
    - ServerGUI <br>
    - MainScreenState <br>
    - ModelManager <br>
    - SpawnRegions <br>
    - \*Test\*        *(all classes that contains the word "test")* <br>
</details>

## Pluginator
This patch allows you to load plugins. A plugin is a mod but only required for the server or client. <br>
Common use is for servers, to be able to execute code only on the server side (like synchronization, or security) or not to show what the server is doing to clients.

To install the pluginator, it's very simple, just copy the file ``LuaManager.class`` to your game/server folder, into folder ``java/zombie/Lua/``, and restart the game. <br>
You can also make a backup by renaming the old file with the ``.bak`` extension. (if a problem appears in future)

Plugins must be placed in folder ``media/lua/plugins/``, if it doesn't exist, create it.

**Note:** This tool makes the server believe that the plugins that have been loaded, have never been loaded. <br>
It is therefore not possible to reload the plugins with the ``reloadlua <filename>`` command, so you will have to restart the server for this.


## Disclaimer
I never played or paid the game, I just reverse engineered a long time to do these patches. <br>
So don't blame me if any problems arise after installing this. I am not responsible for any damage caused by its use.

I created these tools because I wanted a plugin to automatically shut down my friends' server when no one is connected, and I noticed that the API provided for modders was really poor. <br>
So I recompiled some classes to make modified versions.

And my conclusion is that the game is really poorly coded... Have a nice days PZ devs... =)
