---
tags: tools snippets
season: spring
---

# Delete until specified charcter

> Use `dtc`, where c is any character, e.g. for you, you want `dt"`
> This will delete upto but not including c.
> If you had:
> 
> `delete until exclamation point!`
> 
> And the cursor was at the first space and you typed `dt!`, you would get:
> 
> `delete!`
> 
> Also `dfc`.
> 
> This will delete upto and including c.
> 
> Using `df!` on the same example above would give you:
> 
> `delete`
> 
> Just about any "motion" can be used for the d, c, y and similar commands.

[source](https://askubuntu.com/questions/64833/vi-shortcut-to-delete-until-the-next-x-character)

# Find and replace within specified line range

Example: replace all occurences of `foo` with `bar` between lines 3 and 10:
```
:3,10s/foo/bar/g
```

To perform find and replace in the whole document:
```
:%s/foo/bar/g
```

The dot `.` represents the current line and the dollar sign `$` the last lign. 

[source](https://linuxize.com/post/vim-find-replace/)

# Install Vundle package manager for NVim

Quick Guide For Vundle packages installation - In short:

    Open terminal and edit the vimrc file (using vim ~/.vimrc)

    paste the name of package according to the documentation, paste it between
    vundle#begin() and vundle#end.

    call vundle#begin()
    Plugin 'PluginAuthor/PluginName'
    call vundle#end()

for example:

```
call vundle#begin()

Plugin 'VundleVim/Vundle.vim'
Plugin 'Valloric/YouCompleteMe'
Plugin 'airblade/vim-gitgutter'
Plugin 'dracula/vim'
Plugin 'tpope/vim-fugitive'

call vundle#end()    
```


There might be additional installation steps (compilation, run a script, etc.) See the plugin's home page for details.

    open Terminal and open vim (just vim ) and Type :VundleInstall , On packages installation window, Wait until Vundle installer is getting finished.

(source)[https://stackoverflow.com/a/57945096/8725263)