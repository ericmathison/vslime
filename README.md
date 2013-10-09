vslime
======

vslime is a Tmux script for interactively sending chunks of code from Vim to Pry
(a Ruby REPL). In that sense, it is similar to using Slime with Emacs (although
the fully dynamic nature of Slime is not reproduced here). It creates a split
window with Vim on top and Pry on the bottom.

Essentially, I'm attempting to automate the process described in this blog post:
http://antityping.com/2013/05/05/tmux-vim-slime-ruby-repl/.

Installation
------------
1. Install Tmux.
2. Install the vim-slime slime plugin (https://github.com/jpalardy/vim-slime).
3. Add `let g:slime_target = "tmux"` to your .vimrc so vim-slime knows to use
   Tmux.
4. Add the included vslime script into a directory that is in your $PATH.

vslime has a lot of moving parts and it isn't currently the easiest thing in the
world to set up. So if you have any problems please feel free to get in touch
with me.

Usage
-----
After installing vslime, running `vslime` at the terminal should start a Tmux
session containing a split window with Vim on top and Pry on the bottom.

If you type some Ruby code into Vim and visually select it, you can spit it into
the Pry REPL at the bottom by typing Control-c Control-c. Typing Control-c
Control-c without any selection in Vim will send the paragraph that the cursor
is on. I have a mapping in my .vimrc that is convenient for sending the entire
contents of the Vim window: `map <leader>s :%SlimeSend<cr>`. But you can, of
course, change `<leader>s` to anything you want.

To move back and forth between Vim and Pry you can type Control-b and then
either the up or down arrow depending on which direction you want to go.
Control-b is the default Tmux "prefix" key. If you've changed the default you
will need to use that instead of Control-b.

Hacking
-------
If you come up with ideas for improving vslime please let me know. I'd be
especially interested to find a way to elegantly bring all of the moving parts
together into a single installation. I'd also like to find a better alternative
to using the sleep method to wait for Vim to load.
