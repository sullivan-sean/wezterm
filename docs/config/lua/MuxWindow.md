# MuxWindow

*Since: nightly builds only*

`MuxWindow` represents a window that is managed by the multiplexer.

It has the following methods:

## `window:window_id()`

Returns the window id

## `window:get_workspace()`

Returns the name of the workspace to which the window belongs.

## `window:set_workspace("something")`

Changes the name of the workspace to which the window belongs.

## `window:spawn_tab{}`

Spawns a program into a new tab within this window, returning the
[MuxTab](MuxTab.md), [MuxPane](MuxPane.md) and
[MuxWindow](MuxWindow.md) objects associated with it:

```lua
local tab, pane, window = window:spawn_tab{}
```

When no arguments are passed, the default program is spawned.

The following parameters are supported:

### args

Specifies the argument array for the command that should be spawned.
If omitted the default program for the domain will be spawned.

```lua
window:spawn_tab{args={"top"}}
```

### cwd

Specify the current working directory that should be used for
the program.

If unspecified, follows the rules from [default_cwd](config/default_cwd.md)

```lua
window:spawn_tab{cwd="/tmp"}
```

### set_environment_variables

Sets additional environment variables in the environment for
this command invocation.

```lua
window:spawn_tab{set_environment_variables={"FOO"="BAR"}}
```

### domain

Specifies the multiplexer domain into which the program should
be spawned.  The default value is assumed to be `"CurrentPaneDomain"`,
which causes the domain from the currently active pane to be used.

You may specify the name of one of the multiplexer domains
defined in your configuration using the following:

```lua
window:spawn_tab{domain={DomainName="my.name"}}
```

