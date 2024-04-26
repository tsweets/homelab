Linux Workstation Setup
==========================================

These notes are for Ubuntu based Distros (I mostly use PopOS for desktop) as I'm giving up on Redhat ones after the IBM clown show with CentOS.  

Step 1 - Init System with DotFiles
------------------------------------------
My Dotfiles  https://github.com/tsweets/dotfiles

Run Them:  
```$ chezmoi init --apply https://github.com/$GITHUB_USERNAME/dotfiles.git```


A better way that installs the chezmoi
```
export GITHUB_USERNAME=tsweets
sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply $GITHUB_USERNAME
``

Gold Standard is this guy  
https://github.com/logandonley/dotfiles  
https://www.youtube.com/watch?v=-RkANM9FfTM


