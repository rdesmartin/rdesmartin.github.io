---
tags:
  - tools
  - programming
season: spring
toc: true
---

# Delete until specified character

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

# Select Current Paragraph (in visual mode)

`vip`

Very useful when [[Useful Imandra Tips|developing with Imandra]], to copy and paste the lemma you're currently editing into the terminal running Imandra CLI. 

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

[source](https://stackoverflow.com/a/57945096/8725263)

# Using Marks
**`mx`** tells Vim to add a mark called _x_.

**`` `x ``** tells Vim to return to the line and column for mark x.

**`'x`** tells Vim to return to the beginning of the line where mark x is set.

**`` `. ``** moves the cursor to the line and column where the last edit was made.

**`'.`** moves the cursor to the line where the last edit was made.

**`'"`** moves the cursor to the last position of the cursor when you exited the previous session.

**`:marks`** shows all marks set.

**`:marks x`** shows the mark named x.

**`:jumps`** shows the jumplist.

**`Ctrl-o`** moves the cursor to the last jump.

**`Ctrl-i`** moves the cursor to the previous jump.

**`H`** moves the cursor to the top of the screen or viewport.

**`M`** moves the cursor to the middle of the screen or viewport.

**`L`** moves the cursor to the bottom of the screen or viewport.

[source](https://www.linux.com/news/vim-tips-moving-around-using-marks-and-jumps/)