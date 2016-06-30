
##目录
1. [补0](#补0)
2. [数字转换为大写金额](#数字转换为大写金额)

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
###数字转换为大写金额
 ```javascript
 var digitUppercase = function(n) {
    var fraction = ['角', '分'];
    var digit = [
        '零', '壹', '贰', '叁', '肆',
        '伍', '陆', '柒', '捌', '玖'
    ];
    var unit = [
        ['元', '万', '亿'],
        ['', '拾', '佰', '仟']
    ];
    var head = n < 0 ? '欠' : '';
    n = Math.abs(n);
    var s = '';
    for (var i = 0; i < fraction.length; i++) {
        s += (digit[Math.floor(n * 10 * Math.pow(10, i)) % 10] + fraction[i]).replace(/零./, '');
    }
    s = s || '整';
    n = Math.floor(n);
    for (var i = 0; i < unit[0].length && n > 0; i++) {
        var p = '';
        for (var j = 0; j < unit[1].length && n > 0; j++) {
            p = digit[n % 10] + unit[1][j] + p;
            n = Math.floor(n / 10);
        }
        s = p.replace(/(零.)*零$/, '').replace(/^$/, '零') + unit[0][i] + s;
    }
    return head + s.replace(/(零.)*零元/, '元')
        .replace(/(零.)+/g, '零')
        .replace(/^整$/, '零元整');
};
 
console.log(digitUppercase(7682.01)); //柒仟陆佰捌拾贰元壹分
console.log(digitUppercase(7682));  //柒仟陆佰捌拾贰元整
console.log(digitUppercase(951434677682.00)); //玖仟伍佰壹拾肆亿叁仟肆佰陆拾柒万柒仟陆佰捌拾贰元整
```

