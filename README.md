# Imitation
A plugin for the [gedit](https://wiki.gnome.org/Apps/Gedit) text editor, that allows the user to edit a document in multiple places simultaneously. Designed to aid repetitive programming tasks.

## Install
1. Install the GSettings schema (needed for config)
  1. Locate your system's gschema dir (e.g. /usr/share/glib-2.0/schemas)
  1. Place "org.gnome.gedit.plugins.imitation.gschema.xml" in there
  1. Apply changes via "glib-compile-schemas *dir*"
1. Install the plugin
  1. Identify gedit's plugin dir (e.g. /usr/lib/gedit/plugins)
  1. Place "imitation.plugin" (file) and "imitation" (folder) in there
    * Make sure they are readable by all
  1. Activate Imitation in gedit's preferences

## Help
See https://github.com/code-tree/imitation/
