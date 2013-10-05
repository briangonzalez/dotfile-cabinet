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

How it works
------------

Once you call `init`, a directory is created called `dotfiles`. This is where you should place your actual dotfiles (`.bashrc`, `.bash_profile`, `.ackrc`, etc.). These will be symlinked into your home directory when you call `./df-cab link`, and backups will be created or any dotfiles that would be overwritten.

```
├── dotfiles
    └── .bashrc
    └── .ackrc
    └── ...
    └── .gitignore_global
```

Once your dotfiles are in the `dotfiles` directory, you should call `./df-cab link`, which symnlinks all of your dotfiles into your home directory, responsibly backing up any files that could be overwritten.

The beauty lies in the fact that your dotfile are symlinked to a folder in your Dropbox directory -- so any machine that you've called `./df-cab link` will always have your latest dotfiles. It's magic.


Update
------
Simply re-curl it:

```bash
$ cd Dropbox/Apps/dotfile-cabinet
$ curl -o df-cab https://raw.github.com/briangonzalez.org/df-cab 
```
