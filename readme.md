# I-Edit 

### Internet Code Editor

I-Edit is a server based code editor that runs in the browser.

It is licensed as GNU GPL so you can hack the code. 

I-Edit is a web app built around the "Ace" code editor. 
Install it on your web server. 
Themes, languages, and syntax highlighting can be altered with slight changes.
File management, file upload, and links to many online tools are supported.
I-Edit was used to build a better version of itself.

I-Edit is a web app and therefore relies heavily on Javascript/HTML5 and other functions of the web browser. 
  
**Features built around the editor**
  
* Work in full-tab (editor only) or split-tab (editor and render frame) modes
* code search, find files, and find in files (grep)
* Simple text based code Clip management
* Key word to text-expander based on a JSON file
* Upload local files
* File System Access (on server)
  * create, copy, delete files and directories
* Text Find and Replace (on server)
* Markdown capable for .md files

* Written with HTML, CSS, Javascript, PHP
* **Uses several powerful components:**
  * Ace editor [^1] - [learn more](https://ace.c9.io/ "Ace Editor Website")
  [^1]: Copyright (c) 2010, Ajax.org B.V. All rights reserved.
  * Parsedown - [learn more](https://github.com/erusev/parsedown/blob/master/README.md "Github")
  * highlight.js [^2] - [learn more](https://github.com/highlightjs/highlight.js "Github")
  [^2]: Copyright (c) 2006, Ivan Sagalaev All rights reserved.
  * myJS - my own downsized "_JQuerian_" library [overview](https://github.com/MLeidel/myJS "mldev.io")
  * Pre-themed for HTML, JAVASCRIPT, PHP, CSS, JSON, and MARKDOWN languages

  For more details look at [Quick Help](https://github.com/MLeidel/I-Edit/blob/master/ieditHelp.md)

### Screen Shots:

Open browser tabs as all editor (iedit.html) or split editor and render frame (iedit2.html)
![I-Edit](images/tabNOframe.png "All Editor")

![I-Edit](images/tabwframe.png "Split Editor/Frame")

![I-Edit](images/toolbar1.png "main navigation")

![I-Edit](images/toolbar2.png "tool navigation")

code clips and links can all be changed

![I-Edit](images/ClipsWindow.png "Clips")

![I-Edit](images/gfilesys.png "Grep & Find")

![I-Edit](images/designPage.png "Design Page")


[Explaining the Interface](iedithelp.md)


# Installation

---

Your server:
  
on your server:
  * unzip iedit onto a server directory  
    some additional folders will be created
  * make sure permissions are set correctly  
    for all the new files
        
e n d  12/18/2019

