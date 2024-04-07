# Learn [Neovim (nvim)](https://github.com/neovim/neovim)



---

# What is Neovim(nvim), really?
Neovim is a fork of vim which integrates LSP client and lua api for configuration and plugin creation. \
With the help of the lua integration, nvim's amazing community created a diverse [plugin ecosystem](https://github.com/rockerBOO/awesome-neovim) which feels designed right, robust, scalable and replaceable.

## I already know vim I just want to learn nvim
Great, you can skip half the guide :) \
Read [Chapter 8 - Personal Config vs Preconfigured Configuration](https://ofirgall.github.io/learn-nvim/chapters/08-advanced-config.html#personal-config-vs-preconfigured-configuration) go back to [Chapter 2](https://ofirgall.github.io/learn-nvim/chapters/02-basic-config.md) and then skip to [Chapter 8 - Basic Lua](https://ofirgall.github.io/learn-nvim/chapters/08-advanced-config.html#basic-lua).

# Why did I write this guide?
I started to use nvim in early 2022 after using sublime for about 6 years, I felt sublime was left behind pluginwise and it's not really competing with the features VSCode had to offer, I tried to use VSCode and after a week I understood it's not fitting for me, as it forced me to use my mouse more than often. I decided to give nvim a try, and it ended up as the best decision I made.

I didn't understand where to start from, should I learn vim first? how do I configure nvim? which plugins from the many many plugins do I need to use?

I wanted to make a guide that covers the basics of vim, gives the tools to learn vim (the fishing rod instead of the fish), and one that helps you to configure nvim.

---
# basic commands for ref 
# Vim basic commands

## A
- <kbd>a</kbd> Enter into insert mode after the character your cursor is on. 
- <kbd>A</kbd> Enter into insert mode at the end of the current line.

## B
- <kbd>b</kbd> Move cursor to first character of previous word.
- <kbd>B</kbd> Move cursor to first character of previous non-blank series of characters.
- <kbd>Ctrl</kbd>+<kbd>b</kbd> Scroll page backwards (move up in the file).

## C
c stands for “change” will not do anything on its own, but acts as a modifier to other commands. Here are some common commands handy for editing front end code.
- <kbd>cw</kbd> Stands for change word. This will delete the word your cursor is over and enter into insert mode. Note that if you are not on the first character of the word it will only change from where your cursor is until the end of the word. This might seem annoying at first but is actually an amazing feature once you understand movements.
- <kbd>cit</kbd> Change all text in between a set of tags i.e foo will delete foo and put you insert mode.
- <kbd>ci(</kbd> Change all text in between a set of parenthesis.
- <kbd>ci"</kbd> If your cursor is in between a set of quotes, this will delete everything inside those quotes and drop you into insert mode.
- <kbd>cat</kbd>  Change all text in around a set of tags i.e delete all of foo and enter into insert mode.
- <kbd>ca(</kbd> Change all text in around a set of parenthesis.
- <kbd>ca"</kbd> If your cursor is on or in between a set of quotes, this will delete those quotes and drop you into insert mode.
- <kbd>ct"</kbd> Change text til the quotes.
- <kbd>2ct"</kbd> Change text from cursor up til the 2nd quote in a line.
- <kbd>cF"</kbd> Change from cursor backwards finding and including the previous quote.
- <kbd>C</kbd> Delete until the end of the line and enter into insert mode.
- <kbd>ctrl</kbd>+</kbd>c</kbd> In Normal mode, any pending command is aborted. Also aborts current search.

## D
- <kbd>dd</kbd> Delete the current line.
- <kbd>3dd</kbd> Delete 3 lines.
- <kbd>D</kbd> Delete from cursor until the end of the line. Same as d$.
- <kbd>dw</kbd> Delete the word your cursor is on. Difference between this and cw is that you do not enter into insert mode and it will delete the trailing white space.
- <kbd>2dw</kbd> This will delete the word your cursor is on as well as the next one. You can replace 2 with any number.
- <kbd>d^</kbd> Delete from cursor to beginning of the line.
- <kbd>d/pattern</kbd> Deletes up to first matched pattern.
- <kbd>2df"</kbd> Delete from cursor to find the 2nd quote mark. This is inclusive so it will delete the second quote. This is a handy command for deleting attributes in html if your cursor is on the first letter of the attribute.
- <kbd>di"</kbd> Delete everything inside of a set of quotes quotes.
- <kbd>di(</kbd> Delete everything inside of a set of parantheses.
- <kbd>dit</kbd> Delete everything inside of a set of tags (like html markup for instance).
- <kbd>dat</kbd> Delete all text around a set of tags i.e. delete all of foo and enter into insert mode.
- <kbd>da(</kbd> Delete all text around a set of parenthesis.
- <kbd>da"</kbd> Delete contents inbetween quotes as well as the quotes themselves.
- <kbd>ctrl</kbd>+<kbd>d</kbd> Scroll half page (in this case “d” is a mnemonic for “down”).
- <kbd>:%d</kbd> Deletes all lines in a file.
- <kbd>:2,8d</kbd> Deletes lines two through eight.

## E
- <kbd>e</kbd> Jumps to the end of the next word.
- <kbd>E</kbd> Jumps to the end of the next non-blank series of characters.
- <kbd>ge</kbd> Jumps to the end of the previous word.
- <kbd>:ea 5m</kbd> Jump to five minutes ago. Seriously.
- <kbd>:ea 1h</kbd> Jump to 1 hour ago.
- <kbd>:ea 14h 30m</kbd> Jump to 14 hours and 30 minutes ago. Ok you get the point.
- <kbd>:e filename</kbd> Open file in the current window.
- <kbd>:e .</kbd> Open file explorer in current directory.

## F
f is for finding things so it doesn’t do anything on it’s own. It will jump to the next character you type after f. It can be combined with c,d,y to change, cut, and copy sections of text.
- <kbd>fr</kbd> Jumps to the next r on the (same line only).
- <kbd>ft</kbd> Jumps to the next t on the (same line only).
- <kbd>f,</kbd> Jumps to the next , on the (same line only).
- <kbd>Fr</kbd> Jumps to the previous r (same line only).
- <kbd>Ft</kbd> Jumps to the previous t (same line only).
- <kbd>F,</kbd> Jumps to the previous , (same line only).
- <kbd>2df"</kbd> delete from cursor through two occurences of “.
- <kbd>ctrl</kbd>+<kbd>f</kbd> Scrolls one full page forward.

## G
- <kbd>gx</kbd> Go to url under your cursor in a browser.
- <kbd>gf</kbd> Go open file under your cursor in the current window.
- <kbd>g;</kbd> Go to the last place you edited text.
- <kbd>g,</kbd> Go forward in the change list.
- <kbd>4g,</kbd> Go forward 4 spots on the change list.
- <kbd>gg=G</kbd> or <kbd>1G=G</kbd> format the entire file.
- <kbd>gn</kbd> Grab the next match from last search and visually select it.
- <kbd>gi</kbd> Go into insert mode at the end of the last insert you did.
- <kbd>ge</kbd> Go to the end of the previous word.
- <kbd>gp</kbd> Pastes just like p but leave the cursor after the pasted text.
- <kbd>gP</kbd> Pastes just like P but leave the cursor after the pasted text.
- <kbd>gv</kbd> Reselects most recent visual selection.
- <kbd>gv$A</kbd> Reselects most recent visual selection then moves to the end of the line, and enters insert mode.
- <kbd>g~~</kbd> Switch case of all characters in current line.
- <kbd>gq</kbd> Format selected text.

## H
- <kbd>h</kbd> Move cursor one character to the left.
- <kbd>4h</kbd> Move cursor four characters to the left.
- <kbd>dh</kbd> Delete character to the left of cursor.
- <kbd>:h</kbd> Opens up vim help in a new window.
- <kbd>:h</kbd> a Opens vim help to documentation on the a key.
- <kbd>:h i_CTRL-R</kbd> Opens vim help to documentation on pressing control and r while in insert mode.
- <kbd>H</kbd> Move cursor to first (highest) line in window.

## I
i Enter insert mode where your cursor is. Any text you insert will be inserted before the character your cursor was over.
- <kbd>I</kbd> Insert text at the very beginning of the line.

## J
- <kbd>j</kbd> Moves cursor down one line.
- <kbd>32j</kbd> Moves the cursor down 32 lines.
- <kbd>J</kbd> Joins two lines removing indent.

## K
- <kbd>k</kbd> Moves cursor up one line.
- <kbd>8k</kbd> Moves cursor up 8 lines.
- <kbd><C-w>K</kbd> Rotates window to horizontal split.
- <kbd>dk</kbd> Delete current line and line above cursor.

## L
- <kbd>l</kbd> Move cursor right one character.
- <kbd>dl</kbd> Delete character under cursor. Same as x.
- <kbd>L</kbd> Move cursor to last line in window.

## M
- <kbd>m</kbd> is for marking spots (which you can think of as bookmarks in your files). It does not do anything by itself.
- <kbd>mk</kbd> Mark spot as k.
- <kbd>'k</kbd> Return the cursor to the spot you marked as “k”.
- <kbd>d'k</kbd> Delete from the cursor’s position to the spot you marked as “k”.
- <kbd>c'k</kbd> Change from the cursor’s position to the spot you marked as “k”.
- <kbd>y'k</kbd> yank/copy from the cursor’s position to the spot you marked as “k”.
- <kbd>M</kbd> Move cursor to middle of window.

## N
- <kbd>n</kbd> Moves forward to next match of a search pattern.
- <kbd>N</kbd> Moves backwards to previous match of a search pattern.
- <kbd>gn</kbd> Search forward for the last used search pattern.

## O
- <kbd>o</kbd> Opens a new line below where your cursor is and places you in insert mode.
- <kbd>O</kbd> Opens a new line above where your cursor is and places you in insert mode.
- <kbd>CTRL-o</kbd> Go backwards in the jumplist (list of where your cursor has been). Trust me this is like movement steroids.
- <kbd>12CTRL-o</kbd> You can also pass it a count so this will go backwards in the jumplist 12 spots.
- <kbd>:only</kbd> Closes all splits except for the current one.

## P
Paste is a pretty big deal when you are dealing with code. So p should be one of your best friends.
- <kbd>p</kbd> Pastes in the last thing you yanked or deleted (copied or cut) after the cursor.
- <kbd>P</kbd> Pastes in the last thing you yanked or deleted (copied or cut) before the cursor.
- <kbd>2p</kbd> Pastes in the last thing you yanked or deleted (copied or cut) twice.
- <kbd>xp</kbd> This will swap two characters. Technically it just deletes the character under your cursor, then pastes it back in. This is the equivalent of dlp.
- <kbd>"*p</kbd> Pastes in text from your system clipboard.
- <kbd>"2p</kbd> This will paste in text from the second register. You will use this all of the time. Most useful when you delete something you want to paste, then delete something else. Move to the place where you want to paste text, hit p and go “doh”. Just remember "2p.
- <kbd>"%p</kbd> Pastes in the name of the current file.
- <kbd>:212pu</kbd> Pastes in last copy or delete on line 212. 212 can be any line number.
- <kbd>:42pu *</kbd> Pastes in system clipboard text at line 42.
- <kbd>"/p</kbd> Pastes in your last search pattern.
- <kbd>:<c-r>/</kbd> Pastes in your last search pattern when you are on the command line.
- <kbd>"ap</kbd> Pastes in the contents of register a. To see a list of registers and what they have in them, do :reg or :registers.
- <kbd>"= 8*8<CR>p</kbd> Pastes in evaluation of the expression 8*8. This could be any maths you want. = is the expression register, which allows you to do calculations. From normal mode you can launch it by hitting "=.

## Q
q records things - so it doesn’t do much on its own. You need to tell it what register to store the recorded sequence in.

- <kbd>qa</kbd> Begins recording into register a. Enter in keystrokes you want to save, then hit q to end the recording.
- <kbd>@a</kbd> Will play back what you just recorded into register a.

If you wanted to increment a set of numbers in a line of text like .icon-1 { background-image:url(img-1.png); } you could do. qa0yyp/\d<CR><c-x>n<c-x>0q now if we run @a and our cursor is on the line with code we want incremented, it will copy that line. and bump both of those numbers up to 2. And if we run it again with @@ it will increment all the twos to threes on a new line. Or we could give it a count with 99@a and get all the numbers up to 100.

- <kbd>:q</kbd> quits file only if you have no unsaved changes.
- <kbd>:q!</kbd> quits file without writing any of your changes.
- <kbd>:wq</kbd> saves and quits file.
- <kbd>:12,42wq</kbd> saves lines 12 to 42 and quits file.
- <kbd>:wqa</kbd> saves and quits all files in buffer.

## R
- kbd>r</kbd> Replaces character under cursor with next input i.e.
- <kbd>ra</kbd> Replaces the character under the cursor with a.
- <kbd>R</kbd> Enter “replace mode” which is like insert mode except you will overwrite characters instead of insert between them.
- <kbd>:r filename</kbd> Read the contents of filename and place into the current buffer.
- <kbd>:r !ls</kbd> Pastes in the output of ls. ! calls an external process in vim. So this can be pretty userful.
- <kbd>:r !cd -;</kbd> ls Pastes in the directory listing of the last directory you were in.
- <kbd>:r !w3m -dump http://somewebsite.com</kbd> Pastes in the content from somewebsite.com without any of the markup. Must have w3m installed. WHICH YOU SHOULD :) If you have homebrew installed you can simply run brew install w3m.
- <kbd>:r !tree</kbd> Pastes in the output from running tree on a directory.
- <kbd>:reg</kbd> or <kbd>:registers</kbd> Print out a list of available registers and their contents. Registers are like a multi-shelf clipboard. But it also stores all of your recent deletes. In vim delete behaves more like cut than a true delete.

## S
- <kbd>s</kbd> Deletes the character your cursor is on and enters into insert mode.
- <kbd>S</kbd> Deletes the whole line you are on and enters into insert mode.
- <kbd>:sp</kbd> This will split the current window horizontally. Sp is short for split.
- <kbd>:sp file.txt</kbd> This will split the current window horizontally with a file named file.txt.
- <kbd>:vsp file.txt</kbd> This will split the current window vertically. vsp stands for vertical split.
- <kbd>s</kbd> Is how you do find and replace, so let’s just say it is all of the important.
- <kbd>:s/foo/bar</kbd> replaces foo with bar on the current line for the first occurance of foo.
- <kbd>:12,42s/foo/bar</kbd> replaces foo with bar on lines 12,42 for the first occurance of foo in each line.
- <kbd>:12,42s/foo/bar/g</kbd> replaces all occurances of foo with bar on lines 12,42.
- <kbd>:%s/foo/bar/g</kbd> replaces all occurances of foo with bar for the entire file.
- <kbd>:'<,'>s/foo/bar/g</kbd> replaces all occurances of foo with bar for the last visual selection.
- <kbd>:%~</kbd> Repeat last substitute with same substitute string but with last used search pattern across the entire file.
- <kbd>:%s/\ class=".*"//g"</kbd> Delete all classes in markup for the current file.
- <kbd>:%s/\ id=".*"//g"</kbd> Delete all ids in markup for the current file.
- <kbd>:bufdo %s/\ class=".*"//ge | update</kbd> Delete all classes in markup for all files in buffer.
- <kbd>:tabdo %s/\ class=".*"//ge | update</kbd> Delete all classes in markup for all files in the current tab.
- <kbd>:%s/\s\+$//e</kbd> Removes trailing whitespace.

## T
t means ‘til’ so it doesn’t do anything on its own. It is very similar to f but f is inclusive. T is exclusive meaning it will stop before the character you are finding.
- <kbd>tf</kbd> put cursor one character before the next occurance of f.
- <kbd>;</kbd> repeat latest f, F, t, or T.
- <kbd>,</kbd> repeat it in the opposite direction.
- <kbd>dt<</kbd> Delete up until the next <. This is handy in the markup world.
- <kbd>dt"</kbd> Delete from cursor until next “.
- <kbd>dT}</kbd> Delete backwards from cursor until previous }.

## U
- <kbd>u</kbd> Undo changes.
- <kbd>U</kbd> Undo all latest changes on one line, the line where the latest change was made.
- <kbd>ctrl</kbd>+</kbd>r</kbd> Redo changes.
- <kbd>ctrl</kbd>+</kbd>u</kbd> Scroll window upwards to the amount set by the “scroll” option. Default is half a screen.
- <kbd>:undol</kbd> List all the history points in your tree of changes.

## V
- <kbd>v</kbd> Start visual mode on a per character basis.
- <kbd>V</kbd> Starts visual mode linewise (selects whole lines).
- <kbd>CTRL</kbd>+<kbd>v</kbd> Starts visual mode blockwise (very favorite).
- <kbd>gv</kbd> Reselect last visual selection.
- <kbd>vat</kbd> Select html elements
- <kbd>vit</kbd> Select the content between html elements

## W
- <kbd>w</kbd> Moves to the next word.
- <kbd>3w</kbd> Moves to the third word.
- <kbd>:w</kbd> Save

## X
- <kbd>x</kbd> delete character under your cursor.
- <kbd>X</kbd> this will delete a character before the cursor. Same as dh.
- <kbd>3x</kbd> Delete 3 characters.

## Y
y stands for copy, I mean yank. It doesn’t do anything by itself. It is very similar to c and d in how it can be used.
- <kbd>yy</kbd> Copies current line.
- <kbd>"xyy</kbd> Copies current line into register x.
- <kbd>"jY</kbd> Copies current line into register j. If you like “Y” to work from the cursor to the end of line (which is more logical, but not Vi-compatible) use “:map Y y$”.
- <kbd>:12,112y</kbd> Copies lines 12 through 112.
- <kbd>mk { motion } y'k</kbd> Mark a spot k, navigate to a new spot and then copies from mark k to the current position of your cursor.
- <kbd>yt"</kbd> Copies from current cursor postion to the next quote on the same line.
- <kbd>yt></kbd> Copies from current cursor postion to the next > on the same line.
- <kbd>yT></kbd> Copies from current cursor postion to the previous > on the same line.
- <kbd>yf></kbd> Copies from current cursor postion up to and including the next > on the same line.
- <kbd>yF></kbd> Copies from current cursor postion up to and including the previous > on the same line.
- <kbd>ctrl</kbd>+<kbd>y</kbd> Scroll up by 1 line.
- <kbd>12</kbd><kbd>ctrl</kbd>+<kbd>y</kbd> Scroll up 12 lines.

## Z
- <kbd>z<CR></kbd> Redraws the screen so that your cursor line is at the top of the window. Same as zt.
- <kbd>z-</kbd> Redraws the screen so that your cursor line is at the bottom of the window. Same as zb.
- <kbd>zz</kbd> Redraws the screen so that your cursor line is at the middle of the window.

## Search
- <kbd>*</kbd> search forward for the word under cursor in current file. Super useful for finding common hex codes in css. And other things.
- <kbd>#</kbd> search backward for the word under cursor in current file.
- <kbd>/</kbd> Forward search for things.
- <kbd>/&lt;p&gt;</kbd> Forward search for the next opening paragraph tag.
- <kbd>/&#92;</kbd> Forward search for the next space.
- <kbd>/^}</kbd> Forward search for closing bracket of a css class, if the css class is closed at the beginning of a new line i.e.
- <kbd>?</kbd> Backwards search.
- <kbd>?http</kbd> Search backwards for the string http.

## Misc
- <kbd>$</kbd> Go to the end of the line.
- <kbd>^</kbd> Go to the beginning.
- <kbd>==</kbd> Format current line of code.
- <kbd>>></kbd> Indent current line.
- <kbd>.</kbd> Repeat last change.
- <kbd>@:</kbd> Repeat last command line.
- <kbd>:set paste</kbd> Set this if you are pasting in content from the system clipboard. Trust me.
- <kbd>:set paste!</kbd> Using ! at the end of any set reverses the current setting. This is useful so that you only have to remember one command and you never have to remember current state. For instance to be able to see line numbers you can do :set nu or :set number. To undo these commands, you would set :set nonu or :set nonumber. This seems like a lot to remember. An alternative is using ! like so :set nu! This will reverse whatever state set number currently resolves to. If line numbers are currently shown, they will be hidden. If they are hidden, they will become revealed. I use this pattern a lot when changing settings of file.

## Ranges
- <kbd>:12,54=</kbd> Format lines 12 through 54.
- <kbd>:56,99></kbd> Indent lines 56 through 99.
- <kbd>:52,84y</kbd> Yank / copy lines 52 through 84.
- <kbd>12>></kbd> Indent 12 lines including the line you are on.

## Page scrolling
Remember <C- means the control key. So <C-b> would translate to pressing control and b at the same time.
- <kbd>ctrl</kbd>+<kbd>b</kbd> Scroll backwards one full screen.
- <kbd>ctrl</kbd>+<kbd>u</kbd> Scroll backwards or ‘up’ a half screen.
- <kbd>ctrl</kbd>+<kbd>d</kbd> Scroll forwards or ‘down’ a half screen.
- <kbd>ctrl</kbd>+<kbd>f</kbd> Scroll forwards.
- <kbd>ctrl</kbd>+<kbd>y</kbd> Scroll backwards count lines (defaults to one).
- <kbd>ctrl</kbd>+<kbd>e</kbd> Scroll forwards one full line.
- <kbd>ctrl</kbd>+<kbd>y</kbd> Scroll backwards one full line.

## Folding
Before use folding in Vim, you need to enable this feature:
```viml
" In your .vimrc
set foldmethod=indent
```
- <kbd>zR</kbd> Open all
- <kbd>zM</kbd> Close all
- <kbd>za</kbd> Open fold under cursor
- <kbd>zo</kbd> Close fold under cursor

# The book
If you find mistakes while reading make sure to let me know at the [issues section](https://github.com/ofirgall/learn-nvim/issues) or create a PR and become a contributor!

## [Start reading here](https://ofirgall.github.io/learn-nvim/)
