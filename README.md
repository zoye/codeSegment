
##目录
1. [补0](#补0)

###补0
 ```javascript
   function leftpad (str, len, ch) {
      str = String(str);
      var i = -1;
      if (!ch && ch !== 0) ch = ' ';
      len = len - str.length;
      while (++i < len) {
      str = ch + str;
      }
      return str;
   }
   leftpad(9,3,0) //009
   leftpad('foo',5,0) //00foo
 ```
