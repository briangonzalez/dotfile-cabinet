dotfile-cabinet
===============
Responsibly manage your dotfiles.

The Gist
--------
**dotfile-cabinet** provides a simple utility for symlinking your dotfiles from Dropbox to your home directory. dotfile-cabinet coupled with Dropbox is extremely powerful, and allows your dotfiles to be automatically synced across all your machines.

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

Once you call `init`, a directory is created called `dotfiles`. This is where you should place your actual dotfiles (`.bashrc`, `.bash_profile`, `.ackrc`, etc.). These will be symlinked into your home directory when you call `./df-cab link`, and backups will be created or any dotfiles that would be overwritten. Your folder structure should look like so:

```bash
~/Dropbox/Apps/dotfile-cabinet
  ├── df-cab                      # The executable.
  ├── dotfiles                    # Where your dotfiles live.
      └── .bashrc
      └── .ackrc
      └── ...
      └── .gitignore_global
```

Once your dotfiles are in the `dotfiles` directory, you should call `./df-cab link`, which symnlinks all of your dotfiles into your home directory. A zip folder is created which backs up any files that could be overwritten.

The beauty lies in the fact that your dotfiles are symlinked to a Dropbox folder -- so any machine that you've called `./df-cab link` will always have your latest dotfiles. It's magic.

I'm Scared
----------

Ok--that's completely reasonable. These are your dotfile we're talking about.

You can test and observe exactly what dotfile-cabinet is doing by creating a fake home directory somewhere on your machine, and call `./df-cab link <path/to/fake-home-dir>`. Do an `ls -la` of `path/to/fake-home-dir` to see how the symlinks have been setup. 

CLI Options
-----------


Update
------
Simply re-curl it:

```bash
$ cd Dropbox/Apps/dotfile-cabinet
$ curl -o df-cab https://raw.github.com/briangonzalez.org/df-cab 
```
