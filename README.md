#pass-plugins
> git inspired subcommands for pass

This repos holds plugins for __pass - the unix password manager__ from [zx2c4.com](http://git.zx2c4.com/password-store/).

Right now plugins work only with a fork of pass located [here](https://github.com/flasheater/pwd-store). Should the plugin feature be merged into the mainline, I will post a notice here.

Plugins for pass are essentially scripts, that are accessible on the *PATH* and follow a naming scheme of

__pass-__*your_plugin*

Then typing

    $ pass your_plugin

will resolve to your script, which will be run with given arguments.
Users of git will find this familiar as it has a very similar feature called subcommands.
[flasheater]: # (link to docs anyone?)

## plugins
A short description of the plugins in this repo

 * **pass-trash**
Moves entries to a folder called *Recycle Bin*.
 * **pass-pk**
Inserts a private key into pass. Expects the path to the key and the name of the entry under which to store it. Accepts same options as ```pass insert```.
Example:

        $ pass pk path/to/my/key Keys/my-favorite-key -e
        Enter pass for my-favorite-key: encryption password goes here

This will generate a pass entry with the encryption password on the first line and the contents of the key file after.
 * **pass-grep2**
An experimental alternative to the ```pass grep``` command. This version decrypts and searches in parallel using multiple cores in the hopes to speed this command up.

## Installing
Until a ```make``` file is written, the recommended installation method is

1. Clone this git repo (*or even better, fork, then clone*)

        $ git clone https://github.com/flasheater/pass-plugins

2. Symlink the plugins you are interested in to a location, that is in your *PATH*

        $ ln -s path/to/pass-plugins/pass-* ~/bin/

## TODO
- [x] pass-trash
- [ ] pass-pk
- [ ] pass-grep2
- [ ] make install script
- [ ] Decide how to handle name collisions with builtin commands.
- [ ] Decide how to pass some global variables to plugins.
- [ ] Decide if it is worthwhile to break out built-in commands into plugins
