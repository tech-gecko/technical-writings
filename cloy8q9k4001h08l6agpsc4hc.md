---
title: "Introduction to Text Editors: Vi(m)"
datePublished: Tue Nov 14 2023 11:18:54 GMT+0000 (Coordinated Universal Time)
cuid: cloy8q9k4001h08l6agpsc4hc
slug: vim-text-editor
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/npxXWgQ33ZQ/upload/cbda89562f85839fc9cc624624d61385.jpeg
tags: linux, vim, shell, text-editors, vi

---

Before we dive deep into the topic, you must have wondered what "vi(m)" means. I wrote it that way because any command I would be teaching you would apply to both the ***vi*** and ***vim*** text editors. ***VIM*** stands for ***V***i ***Im***proved, so you get the gist.

The default editor bundled with the UNIX operating system is referred to as ***vi***, short for "***visual editor*"**. Other alternative editors for UNIX environments include [pico](https://en.wikipedia.org/wiki/Pico_(text_editor)) and [emacs](https://en.wikipedia.org/wiki/Emacs), which is a product of [GNU](https://en.wikipedia.org/wiki/GNU). The vi editor in UNIX operates in two modes:

1. ***Command mode***, where commands are entered to perform actions on the file.
    
2. ***Insert mode***, where typed text is inserted into the file.
    

In command mode, each character entered is a command affecting the text file, and typing a character might switch vi to insert mode. In insert mode, every typed character is added to the file, and pressing the ***&lt;Esc&gt;*** (Escape) key turns off insert mode.

Although there are numerous vi commands, beginners often find just a few essential commands sufficient. This article offers a selection of basic vi commands, with asterisks (\*) marking the most fundamental and useful ones. With practice, these commands should become second nature.

It is important to note that commands in vi(m) are ***case-sensitive***. Using an uppercase letter instead of lowercase can yield unexpected results.

### Basic Vi(m) Commands

Outlined in the table below are the basic vi/vim commands. Remember that "\*" is not part of the commands, but to tell you that the commands marked with asterisks are the fundamental and most useful commands.

| COMMAND | RESULT OF COMMAND |
| --- | --- |
| \* vi &lt;filename&gt; | edit ***filename***, starting from the first line. |
| vi -r &lt;filename&gt; | recover ***filename*** that was being edited when an error occurred. |
| \* :x, then &lt;Return/Enter&gt; | quits vi(m) and saves the file with the name specified before the edit is made. |
| :wq, then &lt;Return/Enter&gt; | quits vi(m) and saves the file with the name specified before the edit is made. |
| :q, then &lt;Return/Enter&gt; | quits vi(m) (gives an error if the latest changes of the file have not been saved). |
| \* :q!, then &lt;Return/Enter&gt; | quits vi(m) even though the latest changes of the file have not been saved. |
| \*j or &lt;Return/Enter&gt; or \[down-arrow\] | moves the cursor down one line. |
| \*k or \[up-arrow\] | moves the cursor up one line. |
| \*h or &lt;Backspace&gt; or \[left-arrow\] | moves the cursor left one character. |
| \*l(small letter L) or &lt;Space&gt; or \[right-arrow\] | moves the cursor right one character. |
| \*0 (zero) | moves the cursor to the start of the current line. |
| \*$ | moves the cursor to the end of the current line. |
| w | moves the cursor to the beginning of the next word. |
| b | moves the cursor to the beginning of the preceding word. |
| :0(zero), then &lt;Return/Enter&gt; or ***1G*** | moves the cursor to the first line in the file. |
| :n, then &lt;Return/Enter&gt; or ***nG*** | moves the cursor to line n in the file. |
| :$, then &lt;Return/Enter&gt; or **G** | moves the cursor to the last line in the file. |
| ^f | moves forward one screen(page). |
| ^b | moves backward one screen(page). |
| ^d | moves down (forward) one-half screen. |
| ^u | move up (backward) one-half screen. |
| ^l (small letter L) | redraws the screen. |
| ^r | redraws the screen, removing deleted lines. |
| \*u | undo whatever you just did. |
| \*i | inserts text before the cursor, until ***&lt;Esc&gt;*** is hit. |
| I (capital letter i) | inserts text at the beginning of the current line, until ***&lt;Esc&gt;*** is hit. |
| \*a | appends text after the cursor, until ***&lt;Esc&gt;*** is hit. |
| A | appends text to the end of the current line, until ***&lt;Esc&gt;*** is hit. |
| \*o(small letter) | opens and puts text in a new line below the current line, until ***&lt;Esc&gt;*** is hit. |
| O (capital letter) | opens and puts text in a new line above the current line, until ***&lt;Esc&gt;*** is hit. |
| \*r | replaces the single character under the cursor (no ***&lt;Esc&gt;*** needed). |
| R | replaces characters, starting with the current cursor position, until ***&lt;Esc&gt;*** is hit. |
| cw | changes the current word with new text, starting with the character under the cursor, until ***&lt;Esc&gt;*** is hit. |
| cNw | changes N words beginning with character under the cursor, until ***&lt;Esc&gt;*** is hit. For example, c3w changes 3 words. |
| C | changes (replaces) the characters in the current line, until ***&lt;Esc&gt;*** is hit. |
| cc | changes (replaces) the entire current line, stopping when ***&lt;Esc&gt;*** is hit. |
| Ncc or cNc | changes (replaces) the next N lines, starting with the current line, stopping when ***&lt;Esc&gt;*** is hit. |
| \*x | deletes the single character under the cursor. |

| Nx | deletes N characters, starting with the character under the cursor. |
| --- | --- |
| dw | deletes the single word beginning with the character under the cursor. |
| dNw | deletes N words, beginning with the character under the cursor. For example, d3w deletes 3 words. |
| D | deletes the remainder of the line, starting with the current cursor position. |
| \*dd | deletes the entire current line. |
| Ndd or dNd | deletes N lines, beginning with the current line. For example, 3dd deletes 3 lines. |
| yy | copies (yanks, cuts) the current line into the buffer. |
| Nyy or yNy | copies (yanks, cuts) the next N lines, including the current line, into the buffer. |
| p | pastes the line(s) in the buffer into the text space after the current line. |
| /string | searches forward for the occurrence of the string in the text. |
| ?string | searches backwards for the occurrence of the string in the text. |
| n | moves to the next occurrence of the search string. |
| N | moves to the next occurrence of the search string in the opposite direction. |
| :.= | returns the line number of the current line at the bottom of the screen. |
| := | returns the total number of lines at the bottom of the screen. |
| ^g | provides the current line number, along with the total number of lines, in the file at the bottom of the screen. |
| :r &lt;filename&gt; &lt;return&gt; | reads the file named ***filename*** and inserts after the current line. |
| :w &lt;return&gt; | writes the current contents to the file named in the original vi(m) call. |
| :w &lt;newfile&gt; &lt;return&gt; | writes current contents to a new file named ***newfile.*** |
| :12, 35w &lt;smallfile&gt; &lt;return&gt; | writes the contents of the lines numbered 12 through 35 to a new file named ***smallfile.*** |
| :w! &lt;prevfile&gt; &lt;return&gt; | writes current contents over a pre-existing file named ***prevfile.*** |

**Note Below:**

1. Unlike GUI editors, you cannot highlight and delete text here, you can only use commands.
    
2. The undo command acts like a toggle, undoing and redoing your last action. You cannot go back more than one step.
    
3. Unlike GUI editors, the mouse cannot move the cursor here. You must use the key commands outlined above. Arrow keys may also work for some UNIX shells but are better avoided because they may produce unwanted behaviour.
    
4. The cursor moves to the bottom of the screen whenever the ":" (semi-colon) is typed (when not in insert mode).
    
5. When you type "vi(m) ***filename***", the editor will open for you to start editing from the first line only when "***filename***" didn't previously exist. If it does, the editor will open to the first page of the already existing file.
    

***Are you lost? The link to the first topic of this series is embedded below.***

%[https://hashnode.com/post/cln8gyclp00020aml9jyg6v1o] 

### Conclusion

I hope you found this content as enjoyable to read as I did to write. If you are interested in more content like this, please navigate to my profile and follow me for more content of the same nature.

**Connect with Me**

Feel free to reach out [v](https://x.com/IAshimonye83170?source=about_page-------------------------------------)i[a](https://x.com/IAshimonye83170?source=about_page-------------------------------------) [X](https://x.com/IAshimonye83170) or [Lin](https://www.linkedin.com/in/ikechukwu-ashimonye-262944283)[kedIn](https://www.linkedin.com/in/ikechukwu-ashimonye-262944283) [](https://www.linkedin.com/in/ikechukwu-ashimonye-262944283/?source=about_page-------------------------------------)if [](https://www.linkedin.com/in/ikechukwu-ashimonye-262944283/?source=about_page-------------------------------------)[y](https://x.com/IAshimonye83170?source=about_page-------------------------------------)ou're interested in collaborating on projects or just want to chat about tech, design, or anything in-between. Let's create something amazing together!