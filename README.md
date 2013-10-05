dotfile-cabinet
---------------
Responsibly manage your dotfiles.

The Gist
========
**dotfile-cabinet** provides a simple utility for symlinking your dotfiles from Dropbox to your home directory. dotfile-cabinet coupled with Dropbox is extremely powerful, and allows your dotfiles to be automatically synced across all your machines.

Quick Start
============

Assuming you have Dropbox installed:

```bash
$ cd Dropbox/Apps/dotfile-cabinet                                                 
$ mkdir dotfile-cabinet && cd dotfile-cabinet
$ curl -o df-cab https://raw.github.com/briangonzalez.org/df-cab 
$ chmod +x df-cab
$ ./df-cab init
```

How it works
============

Once you call `init`, a directory is created called `dotfiles`. This is where you should place your actual dotfiles (`.bashrc`, `.bash_profile`, '.ackrc', etc.). These will be symlinked into your home directory when you call `./df-cab link`, and backups will be created or any dotfiles that would be overwritten.

```
├── dotfiles
    └── .bashrc
    └── .ackrc
    └── ...
    └── .gitignore_global
```

Once your dotfiles are in the `dotfiles` directory, you can call `./df-cab link`



Update
======
Simply re-curl it:

```bash
$ cd Dropbox/Apps/dotfile-cabinet
$ curl -o df-cab https://raw.github.com/briangonzalez.org/df-cab 
```
