Linux users often need to use one command over and over again. Typing or copying the same command over and over again reduces your productivity and distracts you from what you are supposed to be doing.

You can save yourself some time by creating aliases for your most commonly used commands. Aliases are like custom shortcuts that represent a command (or set of commands) that can be executed with or without custom options. Chances are you are already using aliases on your Linux system without even knowing it.



**Listing all the current alias** 

syntax : `alias`


#### How to Create Aliases in Linux
There are two types of aliases - temporary and permanent


**Creating Temporary aliases in Linux**

syntax : `$ alias shortName="your custom command here"`

example : `$ alias wr=”cd /var/www/html”`

You can then use `"wr"` shortcut to go to the webroot directory. The problem with that alias is that it will only be available for your current terminal session.

If you open a new terminal session, the alias will no longer be available. If you wish to save your aliases across sessions you will need a permanent alias.

#### Creating Permanent Aliases in Linux

To keep **aliases** between sessions, you can save them in your user’s shell configuration profile file.

`Bash – ~/.bashrc
ZSH – ~/.zshrc
Fish – ~/.config/fish/config.fish

The syntax you should use is practically the same as creating a temporary alias. The only difference comes from the fact that you will be saving it in a file this time. So for example, in bash, you can open a .bashrc file with your favorite editor like this:

		$ vim ~/.bashrc
Find a place in the file, where you want to keep the aliases. For example, you can add them at the end of the file. For organization purposes, you can leave a comment before your aliases something like this:

#My custom aliases
			`alias wr="cd /var/www/html"`
alias ll="ls -alF"
Save the file. The file will be automatically loaded in your next session. If you want to use the newly defined alias in the current session, issue the following command:

$ source ~/.bashrc
To remove an alias added via the command line can be unaliased using the unalias command.

$ unalias alias_name
$ unalias -a [remove all alias]



