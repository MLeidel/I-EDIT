
<a name="top"></a>
# myJS function Reference

1. [ DOM FUNCTIONS ](#dom)
1. [ ASYNC FUNCTIONS ](#async)
1. [ MISC FUNCTIONS ](#misc)
1. [ COOKIE FUNCTIONS ](#cook)
1. [ DATE FUNCTIONS ](#date)

Loading the script:
```html
<script type="text/javascript" src="../js/myJS-1.2.js"></script>
<!-- or -->
<script type="text/javascript" src="../js/myJS-1.2.min.js"></script>
```
-----
<a name="dom"></a>
## DOM FUNCTIONS [^](#top 'top')

### return CSS property value
**JS.gss(query, css)**
```Javascript
let val = JS.gss("#id", "color"); // returns color value
```
Specify the selection and CSS property to retrieve

-----

### change inline style
**JS.css(QuerySelect [,css])**
```Javascript
	JS.css(".content", "background: black; visibility: visible;")
	
	JS.css("textarea").background = "black";
	
	JS.css("#id").visibility = "visible";
```
Specify the selection and optionally the css statements.
Sets the style attribute value of an HTML tag.

-----

### return DOM object
**JS.doq(qs)**
```Javascript
let obj = JS.doq("#id");
```
Given a DOM query selector, return the
elements object handle.

-----

### add a class to an HTML element
**JS.addClass(qs, classname)**
```Javascript
JS.addClass("input", "myclass");
```
Classname must exist in the classlist.

-----

### remove a class from an HTML element
**JS.delClass(qs, classname)**
```Javascript
JS.delClass("input", "myclass");
```
Classname must exist in the classlist.

-----

### Set or Get innerHTML
**JS.htm(qs [,data])**
```Javascript
let val = JS.htm("#id"); // get
JS.htm("#id", val); // set

```

-----

### toggle 'display' property value
**JS.tod(qs, mode)**
```Javascript
JS.tod("#id", "block");
JS.tod(".msg1", "inline");
```
Toggles an element's display
property between block|inline and none.

-----

### make visible
**JS.show(qs)**
```Javascript
JS.show(".msgclass");
```
Set selected element to "visible".

-----

### make hidden
**JS.hide(qs)**
```Javascript
JS.hide(".msgclass");
```
Hide selected element.

-----

### get or set an _input_ value
**JS.val(qs [,data])**
```Javascript
let value = JS.val("#id");  // get value
JS.val("#id", value); // set value
```
Get or Set the form _input_ value
of the selection.

-----

### get or set a tag attribute
**JS.attr(qs, aname [,avalue])**
```Javascript
let value = JS.attr("#id", "size"); // get attr value
JS.attr("#id", "size", "35"); // set attr value
```
Get or set HTML tag attributes, like:
__size='35'__

-----

<a name="async"></a>
## ASYNC FUNCTIONS [^](#top 'top')

example:
```Javascript
JS.webpost("my.php", 1, `postvar1=${var1}&postvar2=${var2}`)
. . .
function webresponse(n, text) { 
  switch (n) {
    case 1:
      // do something with text ...
      break;
    case 2:
      // ... and so on
      break;
  }
}
```
The function 'webresponse' is used by all of the 
async functions and you have to code it.
All of the async functions execute a promise
which will call webresponse function upon
completion.


### read a text file
**JS.webget(url, n)**
```Javascript
JS.webget("myfile.txt", 1);
```
Send a request to return the 
contents of a text file
residing on the app server.
'webresponse' is called with n=1
after the file is read. see example above.

-----

### read a JSON file
**JS.webgetjson(url, n)**
```Javascript
JS.webgetjson("mydata.json", 1);
```
Send a request to return the 
contents of a JSON file
residing on the app server.
'webresponse' returns a JSON *object*.

-----

### send request and recieve reponse
**JS.webpost(url, n, qs)**
```Javascript
JS.webpost("handler.php", 1, `postvar1=${var1}&postvar2=${var2}`)
```
Probably the most useful - for getting dynamic updates
to your page.

-----

### send data to handler w/out response
**JS.websend(url, qs)**
```Javascript
JS.websend(url, `txt=${text2save}`);
```
NOTE: webresponse will not be called upon
completion of this one-way message.

-----

<a name="misc"></a>
## MISC FUNCTIONS [^](#top 'top')

### sleep
**JS.sleep( m )**
```Javascript
JS.sleep( 2000 ); // wait 2 seconds
```
processes milliseconds of time

-----
### jump to bottom of page
**JS.scrollBottom()**
```Javascript
JS.scrollBottom();
```
forces current page to scroll to bottom.

-----
### random number
**JS.rand( low, high )**
```Javascript
JS.rand( 1, 5 );
```
Returns a random number from *low*
to *high* inclusive.

-----

### selected list item
**JS.getOptionText( qs )**
```Javascript
let txt = JS.getOptionText("#mySelect");
```
Returns the currently selected text
from an HTML `<select>` element.

-----

### selected list index
**JS.getOptionIndex( qs )**
```Javascript
let num = JS.getOptionIndex( "#mySelect" );
```
Returns the currently selected index from
an HTML `<select>` element.

-----

### value of querystring name-value pair
**JS.getQvar( var )**
```Javascript
let val = JS.getQvar( "name" );
```
Returns the value in a querystring
name/value pair.

-----

### Title Case
**JS.titleCase( string )**
```Javascript
let msg = JS.titleCase( "hello GAL" ); // -> "Hello Gal"
```
Returns a string in title case.

-----

### copy string to system clipboard
**JS.setCB( s )**
```Javascript
JS.setCB( "put into clipbrd" );
```
Will request user's permissions according
to current standards.

-----

### paste clipboard contents
**JS.getCB()**
```Javascript
JS.getCB(); // uses callback
```
requires the following callback
that you must code:
```Javascript
function getCBtext(text) { 

  // do something with text
  
}
```
-----

### generate a notification
**JS.notify( string )**
```Javascript
JS.notify( "Good Morning" );
```
Creates a system notification -
Will request user's permissions according
to current standards.

-----

### format a decimal number
**JS.numfix( f, [p] )**
```Javascript
let f = 123.4567
let fd = JS.numfix( f ); // fd = 123.46
```
given a floating point 'f' convert  
to 'p' places; default is 2  
returns a float value

-----

<a name="cook"></a>
## COOKIE FUNCTIONS [^](#top 'top')

### set a cookie
**JS.setCookie( cname, cvalue [, exdays] )**
```Javascript
JS.setCookie("mycook", "valu", 30)
```
-----

### get a cookie 8-)
**JS.getCookie( cname )**
```Javascript
let cval = JS.getCookie( "mycook" );
```
-----

### delete cookie 8-(
**JS.deleteCookie( name )**
```Javascript
JS.deleteCookie( "mycook" );
```
-----

<a name="date"></a>
## DATE FUNCTIONS [^](#top 'top')

### day of week
**JS.todayDay([DateObj])**
```Javascript
let daynbr = JS.todayDay();
```
Returns digit 0..6  
where 0 is Sunday.

:Uses current _date_ object  
unless you provide one.

-----

### day of month
**JS.todayMon([DateObj])**
```Javascript
let mnbr = JS.todayMon();
```
Returns digit 1..12

-----

### year
**JS.todayYear([DateObj])**
```Javascript
let yrYYYY = JS.todayYear();
```
Returns 4 digit year like 1996.

-----

### date mm/dd/yyyy
**JS.getMDY([DateObj])**
```Javascript
let mdy = JS.getMDY();
```
-----

### date yyyy/mm/dd
**JS.getYMD([DateObj])**
```Javascript
let ymd = JS.getYMD();
```
-----

### Hours:Minutes
**JS.getHM()**
```Javascript
let hm = JS.getHM();
```
Returns time in HH:MM formatl

-----

### add days to date
**JS.addDays(n)**
```Javascript
let objDate = JS.addDays(15); // today + 15 days
```
Returns new date object.
-----

### Month (short)
**JS.getShortMon(n)**
```Javascript
let smonth = JS.getShortMon(n);
```
Returns 3 character month, like: Nov
n = the month number 1-12.

-----

### Month (long)
**JS.getLongMon(n)**
```Javascript
let month = JS.getLongMon(11);
```
Returns month spelled out, like: November
n = the month number 1-12.

-----

### Day (short)
**JS.getShortDay(n)**
```Javascript
let sday = JS.getShortDay(3); // Wed
```
Returns 3 character day of week.

-----

### Day (long)
**JS.getLongDay(n)**
```Javascript
let day = JS.getLongDay(3); // Wednesday
```
Returns day of week spelled out.

-----

```Javascript
//Examples of date output
JS.getMDY()                   // 08/29/2019
JS.getYMD()                   // 2019-08-29
JS.getHM()                    // 10
JS.todayMon()                 // 08
JS.todayDay()                 // 4
JS.getShortDay(JS.todayDay()) // Thu
JS.getLongDay(JS.todayDay())  // Thursday
JS.getShortMon(JS.todayMon()) // Aug
JS.getLongMon(JS.todayMon())  // Sepember
JS.todayYear();               // 2019
let mydate = JS.addDays(8);   // + 8 days
JS.getYMD(mydate)             // 2019-09-06
JS.getMDY(mydate)             // 09/06/2019
JS.getShortMon(JS.todayMon(mydate))
                            // Sep
JS.getLongDay(JS.todayDay(mydate));
                            // Friday
```



###### Here endith this document
