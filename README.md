dotfile-cabinet
===============
Responsibly manage your dotfiles.

The Gist
--------
**dotfile-cabinet** provides a simple utility for symlinking your dotfiles from Dropbox to your home directory. dotfile-cabinet coupled with Dropbox is extremely powerful, and allows your dotfiles to be automatically synced across all of your machines.

Quick Start
------------

Assuming you have Dropbox installed:

```bash
$ cd Dropbox/Apps                                               
$ mkdir dotfile-cabinet && cd dotfile-cabinet
$ curl -o df-cab https://raw.github.com/briangonzalez/dotfile-cabinet/master/df-cab
$ chmod +x df-cab
$ ./df-cab init
```

You can also call `./df-cab` to see the complete list of commands.

How it works
------------

Once you call `init`, a directory is created called `dotfiles`. This is where you should move your actual dotfiles to (`.bashrc`, `.bash_profile`, `.ackrc`, etc.). These will be symlinked into your home directory when you call `./df-cab link`, and backups will be created of any dotfiles that would be overwritten. Your folder structure should look like so:

```bash
~/Dropbox/Apps/dotfile-cabinet
  ├── df-cab                      # The executable.
  ├── dotfiles                    # Where your dotfiles live.
      └── .bashrc
      └── .ackrc
      └── ...
      └── .gitignore_global
```

Once your dotfiles are in the `dotfiles` directory, you should call `./df-cab link`, which symnlinks all of your dotfiles into your home directory. A zip folder is created with backups of any files that could be overwritten.

The beauty lies in the fact that *your dotfiles are symlinked to a Dropbox folder* -- so any machine that you've called `./df-cab link` will always have your latest dotfiles. It's black magic.

I'm Scared
----------

Ok, that's completely reasonable. These are your dotfiles we're talking about. You wouldn't want anything to go amiss.

You can test and observe exactly what `./df-cab link` is doing by creating a fake home directory somewhere on your machine, and call `./df-cab link < path/to/fake-home-dir >`. Do an `ls -la` on `path/to/fake-home-dir` to see how the symlinks have been setup. 


Which files are currently linked?
---------------------------------

You can run `./df-cab list` to see which files are symlinked. Here's an example output:

```bash
❯ ./df-cab list

[TASK]
Showing the following (14) dotfiles, some may not be symlinked:
☐ Not Symlinked:  .ackrc
☐ Not Symlinked:  .bash-prompt
☐ Not Symlinked:  .bash_history
☐ Not Symlinked:  .bash_profile
☐ Not Symlinked:  .bashrc
☐ Not Symlinked:  .config

[SUCCESS]
Completed command: list
```

CLI Options
-----------

`df-cab` knows the following commands:

```bash
link        # Symlink dotfiles and create backups
revert      # Put dotfile backups back in their place
list        # List dotfiles currently being tracked
init        # Create the required dotfile directory
purge       # Delete old backups
about       # More information
```

You can use a different home directory path (defaults to `~`) by supplying a second argument. For example, if you ran `./df-cab list path/to/home`, you would show all of the files symlinked from your dotfiles directory to `path/to/home`. The second argument always overrides the default home directory. Hopefully that's not too confusing.  

Update
------
Simply re-curl it:

```bash
$ cd Dropbox/Apps/dotfile-cabinet
$ curl -o df-cab https://raw.github.com/briangonzalez.org/df-cab 
```
