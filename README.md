# Vagrantfile's I Start With

These are the vagrant files I start with for each new project.  File names/paths should be indicative of what they are.  Feel free to add criticisms, comments, and clairvoyances.

**Current output of `tree .`**  
```
├── README.md
└── centos7
    ├── Vagrantfile
    ├── meteor
    │   └── Vagrantfile
    └── nodejs
        └── Vagrantfile

3 directories, 4 files
```
_[see overviews](#vagrantfile-overviews)_

_I wonder if I should list these as boxes..._  I mean I suppose I _should_, but I don't think I'm going to until I'm certain they are awesome.  Until that point, I want to be able to freely change them with wild reckless abandon.  Github feels like a slightly better place for that.  So I'm going to keep this here.


### A little on what vagrant is:

Vagrant is a program that allows you to run just about anytype of OS inside a virtual machine on your development machine.  This is super useful, because it allows you to have an environment from which to actually run your development code that is extremely close (or identical) to what the code runs on in a production context.  It is an insanely useful tool to have when developing for multiple projects.

These virtual environments are referred to as **vagrant boxes**.  They are defined by `Vagrantfile`s, and these are the ones I have collected as good starting places.

**NOTE:** that one of the excellent features of vagrant boxes are shared directories.  Everything in your VM's `/vagrant` directory shows up in real time in the directory that contains the `Vagrantfile`.  This means that you can use the full capability of your host machine to actually write/edit code, and the VM to run it.  I highly reccomend you DO THIS.  It's rather nice to be able to use the mouse and your favorite IDE without any annoying porting or anything.  Not to mention it keeps your environment that's actually running the code clear of unnecessary programs, etc.  (I still put vim on mine, in case I need to make a quick change to a file that's not in my git repo... sensitive information, and the like.)


### To get a vagrant box up and running

```Install vagrant on your dev machine```

Just use google.  It's easier for all involved.  (Particularly when this link is no longer applicable https://www.vagrantup.com/docs/installation/)

```mkdir project-directory-name```

I always create a project directory to house these endeavors for my own sanity.

```cp path-to-desired-starting-file/Vagrantfile project-directory-name/Vagrantfile```

Double check your paths...  I made some assumptions about directory structure for the example.  Really you just need to copy the text of the desired starting _Vagrantfile_ and stick it your project directory in a file named `Vagrantfile`.

```vagrant up```

This will get things kicking.  It will do a lot of magic if this is the first time its being run in the directory where the VagrantFile lives.

| Other Useful Commands |  |
| ----------------- | ----------------- |
| `vagrant status`  | as expected, reports on the state of the vagrant box in the current directory |
| `vagrant ssh`     | will connect you to the vagrant box in the current directory |
| `vagrant suspend` | saves the current running state of the VM and then stops it. (This still eats disk space) |
| `vagrant halt`    | gracefully shuts down the VM's OS, and stops the VM (more time, no disk space) |
| `vagrant destroy` | removes all trace of the VM from the host (leaves the Vagrantfile though) |


---


## Vagrantfile Overviews

```
├── README.md
└── centos7
    ├── Vagrantfile
    ├── meteor
    │   └── Vagrantfile
    └── nodejs
        └── Vagrantfile

3 directories, 4 files
```

#### centos7

Currently using the base box: **chef/centos-7.0**

_By Default Installs_

 - vim
 - git

##### nodejs

Currently using nodejs LTS 4x version

##### meteor

Also currently using nodjs LTS 4x version

Currently using the latest meteor via: https://install.meteor.com/.

**TODO -** _Meteor has some issues seeing things inside the `/vagrant` folder on the VM (which is where you want your project files so you can edit them via your host machine).  See http://stackoverflow.com/questions/25712468/cant-create-working-meteor-js-project-on-a-vagrant-box for an explanation/solution.  But this **TODO** is about coming up with a way to do this automatically.  Hopefully without waiting until the meteor project is created, but if that doesn't seem feasible, provide a bash command/function that does it with a param of the project-directory-name or some such thing._



