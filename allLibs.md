<a name="top"></a>
# Php Libraries for Web Dev

1. [ Create an HTML `<select>` List ](#list)
1. [ Create an HTML Table ](#table)
1. [ Encryption Decryption ](#crypt)
1. [ Compression Decompression ](#press)
1. [ console_log for PHP ](#log)

---
---
<a name="list"></a>
## createList [^](#top 'top')

include "libs/createList.php";

Used to build a formatted HTML select list.

---

### function: createList(array,string,bool,string,bool)
1.  array or csv string
1.  the SELECT id (string)
1.  [onchange code] or FALSE
1.  [first option text] or FALSE
1.  [size value] or FALSE

Examples:
```php
/*
  createList is a Php function
*/

echo createList(
      $array,
      "ID",
      false,
      "select one",
      false);

echo createList(
      $myArr,
      "SEL",
      "alert(this.options[this.selectedIndex].text)",
      false,
      5);
```
---
---
<a name="table"></a>
## Tblrows [^](#top 'top')


include "libs/Tblrows.php";

Helps format data into an HTML a table.
Formats HTML table one row at a time.
The row can be in the form of: a string
with comma delimited values; an
array; or a row returned from
a database resultset. These
functions will not create the HTML
`<table>` and `</table>` tags. That and
any styling are left to the coder.

  *[Optionally, the 1st column of the
  constructed HTML table may contain
  a link to a Javascript function
  whose single parameter value is determined
  by the last column value of the input
  array or resultset row. When this
  option is used do not include the 
  column NAME for that column in 
  the table heading. You will have to
  provide the actual Javascript 
  function in your rendered page.]*

---
### Class: Tblrow(string)

Constructor sets the column formats:
* **>**     left justify column data
* **d**     format to *.99 and right justify
* **\>**    right justify column data
* **\-**    center column data

Example: 
```php
$tbl = new Tblrow("<,<,d,>,<");  // no optional link column
$tbl = new Tblrow("<,<,d,>,<", "alert");  // link function name
```

### function: tblhead(array|string)

The HTML table heading may be provided in one of two ways:
* string with comma delimited values
* array of string values

Examples:
```php
$tbl->tblhead("Name,Email,Amount,Account,Type");  // string with csv
$tbl->tblhead( array("Name","Email","Amount","Account","Type") );  // array
```
By using an array for headings you can add more functionality as shown below.
```
$ahead = array(
  "<a onclick='alert(0);'>Memory, of</a>",
  "<a onclick='alert(1);'>Amount</a>",
  "<a onclick='alert(2);'>Remarks</a>",
  "<a onclick='alert(\"Three\", 3);'>Attended</a>"
  );
echo $Trow->tblhead($ahead);  // array

```
---
### function: tblrow(array | csv)

Example:
```php
tbl->tblrow($Data); // array or row from resultset or csv string
tbl->tblrow(array("John Doe","abc@hello.com",123.99,"01001234","active"));  // array
tbl->tblrow("John Doe,abc@123.com,100.90,01001234,closed");  //  simple csv string
```
Below is an example for coding and SQL query result.
This example uses the optional function name in the constructor
which will create a column 1 of function links whose parameter
value will be the last column value of the resultset rows. In
this example that value would be the database column `member_rowid`.
```php
include "libs/Tblrows.php";

$db = new SQLite3('savetest.db');

$sql = "SELECT in_mem_honor, amount_paid, remarks, attended, member_rowid
from tbldonation
where in_mem_honor <> ''";  // the query string

$results = $db->query($sql);  // query database
$ar = $results->fetchArray(SQLITE3_NUM); // get the 1st row (array)
if (!$ar) {
	die("No rows returned");
}

//  instantiate a Tblrow class object
$Trow = new Tblrow("<,d,<,-", "alert");  // using optional function name

//  print the open table tag
echo "<table cellspacing=0 cellpadding=4 border=1>\n";  

//  create the table headings row with the tblhead method
echo $Trow->tblhead("Memory of,Amount,Remarks,Attended");  // 1 string arg

//  loop through resultset outputting each formatted table row
do {
  
  echo $Trow->tblrow($ar); // each row of resultset is an array

} while ( $ar = $results->fetchArray(SQLITE3_NUM) );

echo "</table>\n";  // print the close table tag

```

<table cellspacing=0 cellpadding=4 border=1>
<tr><th>^</th><th>Memory of</th><th>Amount</th><th>Remarks</th><th>Attended</th></tr>
<tr><td><a onclick="alert(12);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>mom</td><td align='right'>1,000.00</td><td></td><td align='center'></td></tr>
<tr><td><a onclick="alert(49);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Antony and Cleopatra</td><td align='right'>11.00</td><td>Testing</td><td align='center'></td></tr>
<tr><td><a onclick="alert(5);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Sponsor</td><td align='right'>250.00</td><td></td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(36);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Sponsor</td><td align='right'>250.00</td><td></td><td align='center'></td></tr>
<tr><td><a onclick="alert(9);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Sponsor</td><td align='right'>300.00</td><td></td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(50);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Sponsor</td><td align='right'>300.00</td><td>';sql injection</td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(54);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Chocolate Factory</td><td align='right'>22.22</td><td>Irish Cats Love
Chocolate</td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(54);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>sponsor</td><td align='right'>250.00</td><td></td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(58);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>The Star</td><td align='right'>250.00</td><td>Test</td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(60);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Jack Black</td><td align='right'>250.00</td><td>KOOL</td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(137);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Edward Pierce (Father)</td><td align='right'>100.00</td><td></td><td align='center'>1</td></tr>
<tr><td><a onclick="alert(151);">&nbsp;&nbsp;&raquo;&nbsp;&nbsp;</a></td><td>Jon Steele</td><td align='right'>1,500.00</td><td></td><td align='center'>0</td></tr>
</table>

User codes the `<table...>` and `</table>` tags manually.

<small>end of document</small>

---
---

<a name="crypt"></a>
## Cryptoo [^](#top 'top')

`include "libs/Cryptoo.php";`

Encryption for Php using Sodium.

### class: Cryptoo

no constructor

```php
$cry = new Cryptoo();
```
---
### function: encrypt(string)

Example:
```php
$enc = $cry->encrypt("text to be encrypted...");
```
---
### function: decrypt(encrypted string)

Example:
```php
$ptext = $cry->decrypt($enc);
```
---
### function: setKey()

`setKey()` creates a key using `sodium_crypto_secretbox_keygen()`.
While your Cryptoo object is instantiated it keeps the key generated with
`setKey()` in memory. If you encrypt **and** decrypt _without using this function_
Cryptoo will use a static pre-generated key. Without using
`setKey()` your text is still encrypted but there is
overall _much less security_ because of the 
unchanging static key. However, in situations where this
may be appropriate you can do encryption without having
to store or transfer a key between object instantiations. 

Example:
```php
$cry->setKey();
```
---
### function: delKey()

zeroes out the Cryptoo key buffer memory

Example:
```php
$cry->delKey();
```
---
### function: exportKey()

After using `setKey()` you can obtain a text version
of the key with this function.

Example:
```php
$key = $cry->exportKey();
```
---
### function: importKey()

Rather than using `setKey()` you can use
this function to import (set) a previously
exported key.

Example:
```php
$cry->importKey($key);
```
---
---

<a name="press"></a>
## Arcgz [^](#top 'top')

`include "libs/Arcgz.php";`

File compression & decompression.

### class: Arcgz

```php
$z = new Arcgz();
```
---
### function: putgz(string, string)

Create a compressed .gz file from another file.

Example:
```php
$z->putgz("audit.txt", "audit1.gz");
```
---
### function: readgz(string)

Returns the uncompressed contents of a
compressed (gz) file.

Example:
```php
echo $z->readgz("audit3.gz");
```
---
### function: putungz(string, string)

Create an uncompressed file from
a compressed (gz) file.

Example:
```php
$z->putungz("audit2.gz", "audit.txt");
```
---
---

<a name="log"></a>
## Console_Log for PHP [^](#top 'top')

Lifted code from php.net documentation

<small>console_log.php contains the following code:</small>
```php
function console_log( $data ) {
  echo '<script>';
  echo 'console.log('. json_encode( $data ) .')';
  echo '</script>';
}
```

Sample usage:
```php
include "../images/console_log";

$aryvar = array(1,2,3);
$a = "some string value";
$b = 1231.21;

console_log($a);
console_log("var \$a = " . $a);
console_log( $aryvar );
console_log( [$a, $b, $aryvar] );
```

Output in the console:

![alttext](../images/console.png "title")

---
---
---
