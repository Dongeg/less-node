# less-node
less笔记

变量

```less
@nice-blue:#5B83AD;
body {
  color:@nice-blue;
}

```

mixin

```less
.bordered {
  border-top: dotted 1px black;
  border-bottom: solid 2px black;
}
#menu a {
  color: #111;
  .bordered;
}
```

带参mixin

```less
.border-radius (@radius) {
  border-radius: @radius;
  -moz-border-radius: @radius;
  -webkit-border-radius: @radius;
}
//带参数设置默认值
.div-width (@width: 300px) {
  width:300px;
}
#header {
  .border-radius(4px);
}

```
仅提供引用的属性集合

```less
.wrap () {
  text-wrap: wrap;
  white-space: pre-wrap;
  white-space: -moz-pre-wrap;
  word-wrap: break-word;
}
pre { .wrap }
//编译完成后不会显示.wrap
```

@arguments 参数集合

```less
.box-shadow (@x: 0, @y: 0, @blur: 1px, @color: #000) {
  box-shadow: @arguments;
  -moz-box-shadow: @arguments;
  -webkit-box-shadow: @arguments;
}
.box-shadow(2px, 5px)
```

//嵌套

和sass一样 ~_~

//运算符
在less中支持四则运算，且对其其有强化

例如

```less
@var: 1px + 5;

width:@var;
//编译完成
width:6px;
```

less提供了一系列颜色函数。以及Msth四舍五入，上去整下取整函数


作用域

less作用域同js相同

```less
@var: red;

#page {
  @var: white;
  #header {
    color: @var; // white
  }
}

#footer {
  color: @var; // red  
}
```

less引入同sass

```less
@import "lib.less";
@import "lib";
@import "lib.css";
```

less中还可以使用一些ja表达式

```
@str: "hello";
@var: ~`"@{str}".toUpperCase() + '!'`;
@height: `document.body.clientHeight`;
```

