# gitpod-dotfiles-with-oh-my-zshell
Show how dotfiles can be set for oh-my-zshell in Gitpod

This project is cloned into every Gitpod workspace I spawn so every terminal feels the same

`install.sh`:  
Script that Gitpod automatically runs in every new workspace. 
  - Its purpose is to:
    - install `oh-my-zshell`   
    - symlink the files in `home_files/` dir
  
(A full list of script names can be see here https://www.gitpod.io/docs/configure/user-settings/dotfiles )

## Important
Gitpod natively provides a `.gitconfig` in every workspace. Since I want my custom aliases like `git s`, my `.gitconfig` will override the provided one, so I need to make sure to include this section:

```
[credential]
    helper = /usr/bin/gp credential-helper
```
The helper sets git to use Gitpod cli for authing to Gitlab instead an ssh key or username/pw


oh-my-zshell plugin `git` doesn't work out of the box because of the gitpod-cli `gp`. `gp` is also a git alias provided by the git plugin so the two collide. A work around is to override the `git` plugin as documented here https://github.com/ohmyzsh/ohmyzsh/wiki/Customization#overriding-and-adding-plugins