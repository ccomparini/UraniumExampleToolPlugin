Example Tool
============

This is an example tool plug-in for Uranium. Uranium is the underlying framework used in Ultimaker Cura and NinjaKittens.

The tool type plug-in is meant to allow the user to manipulate the scene. Each tool gets its own button in the tool panel. The tool plug-in mainly works via an event that happens in the scene. The tool itself may decide what events it wants to act on, such as a keyboard event, a mouse release event, and so on. And then it does something with it.

Usually the tool acts upon the current selection. For instance, it may transform the selected scene nodes or modify some properties of it. This example shows how it displays the names of the currently selected items.

Locating Your Configuration Folder
---------
Open Ultimake Cura and navigate to Help -> Show Configuration Folder

Testing
---------

To test your plugin, copy its directory to the "plugins" directory in your configuration folder and restart Cura.

Drag and drop should work, but I use the following script on OSX.

```
# Usage:
# <this script> [plugin source dir] [Cura configuration dir]
#
#  If [plugin source dir] is unspecified, uses the current directory.
#  [Cura configuration dir] defaults to the cura 5.8 configuration folder.

SOURCE_DIR=${1:-$PWD}  # default: install plugin from current dir
CONFIGURATION_FOLDER=${2:-"$HOME/Library/Application Support/cura/5.8"}

if [ -f ${SOURCE_DIR}/__init__.py ]
then
    rsync -avr --exclude '.git' "${SOURCE_DIR%/}" "$CONFIGURATION_FOLDER/plugins/"
else
    echo "${SOURCE_DIR}/__init__.py found - not attempting install"
fi
```

Packaging
---------

To package your plug-in, compress your plug-in folder in a .zip archive and rename that archive to get the `.plugin` extension. These .plugin files can be dropped into any Uranium application to be installed.
