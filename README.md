# I-EDIT 

### Internet Editor

I-EDIT is a server based code editor that is
run on a web browser.

It is licensed as GNU GPL so you can hack the code. 

I-EDIT is a web app built around the "Ace" high performance code editor. 
It is was designed only for web app development. You install it on your web server. 
It is NOT a *WYSIWYG* editor it is a code editor. 
It supports coding in: HTML, Javascript, PHP, CSS, Text, and Markdown,
however, other languages can be added. Theme and syntax highlighting 
can be altered with slight changes.
File management, file upload, and links to many online tools are supported.

I-EDIT is a web app and therefore relies heavily on the
functionaity of the web browser. I-EDIT will work with any
Chromium based browser > version 24, and Firefox.
  
**Features built around the editor**
  
* Work in full-tab (editor only) or split-tab (editor and render frame) modes
* code search, find files, and find in files (grep)
* Simple text based code Clip management
* Key word to text-expander based on a JSON file
* Upload local files
* File System Access (on server)
  * create, copy, delete files and directories
* Text Compare, and Design tools
* Markdown capable

* Written with HTML, CSS, Javascript, PHP
* **Uses several powerful components:**
  * Ace editor [^1] - [learn more](https://ace.c9.io/ "Ace Editor Website")
  [^1]: Copyright (c) 2010, Ajax.org B.V. All rights reserved.
  * Parsedown - [learn more](https://github.com/erusev/parsedown/blob/master/README.md "Github")
  * highlight.js [^2] - [learn more](https://github.com/highlightjs/highlight.js "Github")
  [^2]: Copyright (c) 2006, Ivan Sagalaev All rights reserved.
  * myJS - my own downsized "_JQuerian_" library [overview](https://mldev.io/TArea/user/config/myJSref.html "mldev.io")
  * Pre-themed for HTML, JAVASCRIPT, PHP, CSS, JSON, and MARKDOWN languages

  For more details look at [Quick Help](https://mldev.io/TArea/user/ieditHelp.html)

### Screen Shots:

You can open browser tabs as all editor (iedit.html) or split editor and render frame (iedit2.html)
![I-EDIT](images/tabNOframe.png "All Editor")

![I-EDIT](images/tabwframe.png "Split Editor/Frame")

![I-EDIT](images/toolbar1.png "main navigation")

![I-EDIT](images/toolbar2.png "tool navigation")

code clips and links can all be changed

![I-EDIT](images/ClipsWindow.png "Clips")

![I-EDIT](images/gfilesys.png "Grep & Find")

![I-EDIT](images/designPage.png "Design Page")

# Installation

Your server:
  * LAMP (~~MySQL~~)
  
on your server:
  * create a home directory for I-EDIT
  * unzip i-edit.zip into that directory  
    some other folders will be created
  * make sure permissions are set correctly  
    for all the new files
    
from your browser:
  * .../home/iedit.html
    will launch the full page editor
  * .../home/iedit2.html
    will launch the split page editor
    
e n d

