# Imitation
Imitation is a plugin for the [gedit](https://wiki.gnome.org/Apps/Gedit) text editor, that allows the user to edit a document in multiple places simultaneously, to aid repetitive programming tasks.

It is **_highly recommended_** you first watch the [demonstration video](http://code-tree.github.io/imitation/) to understand how Imitation works.

[![Demo](http://code-tree.github.io/imitation/demo_poster.png)](http://code-tree.github.io/imitation/)

## Warning
This plugin occasionally crashes when using find-and-replace at the same time.
Unfortunately, I am no longer able to maintain this project, as I have switched to using [Atom](https://atom.io/) as my text editor. If you would like to adopt this project, please let me know.

If you also want to switch to Atom, you can achieve similar functionality to this plugin with the following key-bindings in your `keymap.cson` (or just use Atom's defaults):

```
'atom-workspace atom-text-editor:not([mini])':
    # Multiple cursors
    'ctrl-pageup': 'editor:add-selection-above'
    'ctrl-pagedown': 'editor:add-selection-below'
    # Multiple cursors find
    'ctrl-shift-pageup': 'find-and-replace:select-undo'
    'ctrl-shift-pagedown': 'find-and-replace:select-next'
    'ctrl-shift-enter': 'find-and-replace:select-skip'
    'ctrl-shift-a': 'find-and-replace:select-all'
```

## Download
See [GitHub releases](https://github.com/code-tree/imitation/releases) for latest version (gedit 3.8+) or the [historic releases](http://code-tree.github.io/imitation/) (gedit 2 - 3.7).

### Packages (by other users)
Arch Linux: [imitation-gedit-plugin-git](https://aur.archlinux.org/packages/imitation-gedit-plugin-git/) in AUR (installs latest version)

## Manual Install
1. Install the GSettings schema (needed for config)
    1. Locate your system's gschema dir (e.g. /usr/share/glib-2.0/schemas)
    1. Place "org.gnome.gedit.plugins.imitation.gschema.xml" in there
    1. Apply changes via "glib-compile-schemas dir"
1. Install the plugin
    1. Identify gedit's plugin dir (e.g. /usr/lib/gedit/plugins)
    1. Place "imitation.plugin" (file) and "imitation" (folder) in there
        * Make sure they are readable by all
    1. Activate Imitation in gedit's preferences

## Usage
Imitation may seem a bit complex at first, but it is easy to learn, and powerful to use. There are two main aspects to Imitation: **marking** and **editing**.

### Marking
Before you can start editing in Imitation mode, you need to first mark the places you'd like to edit. Marking can be done in five different ways, depending on the key you press and whether you have selected any text or not.

* **Mark toggle** (`<Control>e`): This is the most basic way of placing marks. It toggles (add|remove) a mark at the cursor.
  * **Normal vertical marking** (`<Control>Page_Up|Down`)
    * **Without selection**: line mode
    * **With selection**: column mode
  * **Alternate vertical marking** (`<Control><Shift>Page_Up|Down`)
    * **Without selection**: word-offset mode (also sticks to end-of-lines if started from one)
    * **With selection**: matches mode selects the next match to selection (and the match number if multiple matches per line)

Unlike Multi-edit, Imitation's vertical marking will skip lines with less characters than the cursor's line offset. This is useful when there are blank lines between code segments.

**Clearing all marks**: Move the cursor (unless in sticky mode) or press Escape

**Sticky mode**: Using "mark toggle" will also trigger "sticky mode", where you can move your cursor around with marks staying in place. In vertical marking, they will be cleared as soon as you move your cursor, unless you enable sticky mode. Sticky mode stays enabled until you clear all marks.

### Editing
For the most part editing with Imitation is mostly similar to editing with a normal cursor. There are however a few differences:

* Your normal cursor will no longer work (only marks will preform edits)
* Delete is limited to plain Backspace and Delete keys (no modifiers like `<Control>` etc)
* You can insert incrementing values using (in order of mark placement):
  * **`<Control>0`**: Integers starting at zero
  * **`<Control>1`**: Integers starting at one
  * **`<Control>a`**: ASCII lowercase a-z
  * **`<Control><Shift>a`**: ASCII uppercase A-Z

## Config
Imitation relies on GSettings for configuration, and GSettings currently uses dconf as the default backend. So you can simply use dconf-editor, and edit settings at the GSettings path /org/gnome/gedit/plugins/imitation.

## Issues
Please contribute to these remaining issues if you are able:
* Packaging for various OSs
* Unicode chars are not inserted properly
* Enabling paste when text is selected
* Occasional crash when using find-and-replace at the same time

## History
To save some confusion over plugin names:
* **Multi-edit** (hyphen) was created by Jon for gedit 2
* **Multi Edit** (no hyphen) was based on Jon's work but created by **another author**
* **Imitation** is a sequel to Multi-edit created by Jon for gedit 3

## Author
Imitation is a [Code Tree](https://codetree.com.au/) project, created by Jon Walsh.
