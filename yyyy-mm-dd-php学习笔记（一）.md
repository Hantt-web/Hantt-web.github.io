---
layout:     post
title:     php学习笔记
subtitle:   小白的学习笔记
date:       2021-1-25
author:    Hantt
header-img: img/the-first.png
catalog:   true
tags:
    - 往事如烟
---
#一.PHP 语法
##1.基本的 PHP 语法
PHP 的脚本块以 <?php 开始，以 ?> 结束。可以把 PHP 的脚本块放置在文档中的任何位置。在支持简写的服务器上，也可以使用 <? 和 ?> 来开始和结束脚本块。PHP 文件通常会包含 HTML 标签，就像一个 HTML 文件，以及一些 PHP 脚本代码。
下面这个一段简单的 PHP 脚本，它可以向浏览器输出文本 "Hello World"：
<html>
<body>

<?php
echo "Hello World";
?>

</body>
</html>
PHP 中的每个代码行都必须以分号结束。有两种通过 PHP 来输出文本的基础指令：echo 和 print。
##2.PHP 中的注释
在 PHP 中，我们使用 // 来编写单行注释，或者使用 /* 和 */ 来编写大的注释块，与c语言不同的是PHP也可以用#进行单行注释。

#二.PHP 变量
##1.PHP 中的变量
PHP 中的所有变量都是以 $ 符号开始的。
在 PHP 中设置变量的正确方法是：
$var_name = value;
如果忘记在变量的前面的 $ 符号的话，变量将是无效的。
##2.PHP 是一门松散类型的语言
在 PHP 中，不需要在设置变量之前声明该变量。根据变量被设置的方式，PHP 会自动地把变量转换为正确的数据类型。而在c语言中，则必须在使用前声明变量的类型和名称。在 PHP 中，变量会在使用时被自动声明。
##3.变量的命名规则
变量名必须以字母或下划线 "_" 开头。
变量名只能包含字母数字字符以及下划线。
变量名不能包含空格。如果变量名由多个单词组成，那么应该使用下划线进行分隔（比如 $my_string），或者以大写字母开头（比如 $myString）。

#三.PHP 字符串
（主要写了几个用于操作字符串的最常用的函数和运算符）
在创建字符串之后，我们就可以对它进行操作了。可以直接在函数中使用字符串，或者把它存储在变量中。
在下面，PHP 脚本把字符串 "Hello World" 赋值给名为 $txt 的字符串变量：
<?php
$txt="Hello World";
echo $txt;
?>
以上代码的输出：
Hello World
##1.并置运算符
在 PHP 中，只有一个字符串运算符。
并置运算符 (.) 用于把两个字符串值连接起来。
eg ：
<?php
$txt1="Hello World";
$txt2="1234";
echo $txt1 . " " . $txt2;
?>
以上代码的输出：
Hello World 1234
上面的例子中使用了两次并置运算符。这是由于需要插入第三个字符串。为了分隔这两个变量，要在 $txt1 与 $txt2 之间插入了一个空格。
##2.strlen() 函数
eg：
<?php
echo strlen("Hello world!");
?>
以上代码的输出：
12
##3.strpos() 函数
strpos() 函数用于在字符串内检索一段字符串或一个字符。
如果在字符串中找到匹配，该函数会返回第一个匹配的位置。如果未找到匹配，则返回 FALSE。
eg：
<?php
echo strpos("Hello world!","world");
?> 
以上代码的输出是：
6
在我们的字符串中，字符串 "world" 的位置是 6。返回 6 而不是 7，是由于字符串中的首个位置是 0，而不是 1。

#四.PHP 运算符、循环语句
这一部分基本都与c语言一致，省略一下，就写一下foreach 语句。
foreach 语句用于循环遍历数组。
每进行一次循环，当前数组元素的值就会被赋值给 value 变量（数组指针会逐一地移动） - 以此类推。
语法
foreach (array as value)
{
    code to be executed;
}
例子
下面的例子循可以输出给定数组的值：
<html>
<body>

<?php
$arr=array("one", "two", "three");

foreach ($arr as $value)
{
  echo "Value: " . $value . "<br />";
}
?>

</body>
</html>

#五.PHP 数组
##1.数值数组
数值数组存储的每个元素都带有一个数字 ID 键。
可以使用不同的方法来创建数值数组：
例子 1
在这个例子中，会自动分配 ID 键：
$names = array("Peter","Quagmire","Joe");
例子 2
在这个例子中，人工分配了的 ID 键：
$names[0] = "Peter";
$names[1] = "Quagmire";
$names[2] = "Joe";
可以在脚本中使用这些 ID 键：
<?php

$names[0] = "Peter";
$names[1] = "Quagmire";
$names[2] = "Joe";

echo $names[1] . " and " . $names[2] . " are ". $names[0] . "'s neighbors";
?>
以上代码的输出：
Quagmire and Joe are Peter's neighbors
##2.关联数组
关联数组，它的每个 ID 键都关联一个值。
在存储有关具体命名的值的数据时，使用数值数组不是最好的做法。
通过关联数组，我们可以把值作为键，并向它们赋值。
例子 1
在本例中，我们使用一个数组把年龄分配给不同的人：
$ages = array("Peter"=>32, "Quagmire"=>30, "Joe"=>34);
例子 2
本例与例子 1 相同，不过展示了另一种创建数组的方法：
$ages['Peter'] = "32";
$ages['Quagmire'] = "30";
$ages['Joe'] = "34";
可以在脚本中使用 ID 键：
<?php

$ages['Peter'] = "32";
$ages['Quagmire'] = "30";
$ages['Joe'] = "34";

echo "Peter is " . $ages['Peter'] . " years old.";
?>
以上脚本的输出：
Peter is 32 years old.
##3.多维数组
在多维数组中，主数组中的每个元素也是一个数组。在子数组中的每个元素也可以是数组，以此类推。
例子 1
在本例中，创建了一个带有自动分配的 ID 键的多维数组：
$families = array
(
  "Griffin"=>array
  (
  "Peter",
  "Lois",
  "Megan"
  ),
  "Quagmire"=>array
  (
  "Glenn"
  ),
  "Brown"=>array
  (
  "Cleveland",
  "Loretta",
  "Junior"
  )
);
如果输出这个数组的话，应该类似这样：
Array
(
[Griffin] => Array
  (
  [0] => Peter
  [1] => Lois
  [2] => Megan
  )
[Quagmire] => Array
  (
  [0] => Glenn
  )
[Brown] => Array
  (
  [0] => Cleveland
  [1] => Loretta
  [2] => Junior
  )
)
例子 2
如果试着显示上面的数组中的一个单一的值：
echo "Is " . $families['Griffin'][2] . 
" a part of the Griffin family?"; 
以上代码的输出：
Is Megan a part of the Griffin family?

#六.PHP 函数
##1.创建 PHP 函数：
（1）所有的函数都使用关键词 "function()" 来开始
（2）命名函数:函数的名称应该提示出它的功能。函数名称以字母或下划线开头。
例子：
<html>
<body>

<?php
function writeMyName()
  {
  echo "htt";
  }

writeMyName();
?>

</body>
</html>
##2.PHP 函数 - 添加参数
例子 1
下面的例子讲输出不同的名字，但姓是相同的：
<html>
<body>

<?php
function writeMyName($fname)
  {
  echo $fname . " Yang.<br />";
  }

echo "My name is ";
writeMyName("David");

echo "My name is ";
writeMyName("Mike");

echo "My name is ";
writeMyName("John");
?>

</body>
</html>
上面的代码的输出：
My name is David Yang.
My name is Mike Yang.
My name is John Yang.
例子 2
下面的函数有两个参数：
<html>
<body>

<?php
function writeMyName($fname,$punctuation)
  {
  echo $fname . " Yang" . $punctuation . "<br />";
  }

echo "My name is ";
writeMyName("David",".");

echo "My name is ";
writeMyName("Mike","!");

echo "My name is ";
writeMyName("John","...");
?>

</body>
</html>
上面的代码的输出：
My name is David Yang.
My name is Mike Yang!
My name is John Yang...
3.PHP 函数 - 返回值
函数也能用于返回值。
例子
<html>
<body>

<?php
function add($x,$y)
  {
  $total = $x + $y;
  return $total;
  }

echo "1 + 16 = " . add(1,16);
?>

</body>
</html>
以上代码的输出：
1 + 16 = 17

#七.PHP$_POST和$_GET 
表单实例：
<html>
<body>

<form action="welcome.php" method="post">
Name: <input type="text" name="name" />
Age: <input type="text" name="age" />
<input type="submit" />
</form>

</body>
</html>
上面的 HTML 页面实例包含了两个输入框和一个提交按钮。当用户填写该表单并单击提交按钮时，表单的数据会被送往 "welcome.php" 这个文件。
"welcome.php" 文件类似这样：
<html>
<body>

Welcome <?php echo $_POST["name"]; ?>.<br />
You are <?php echo $_POST["age"]; ?> years old.

</body>
</html>
上面这个脚本的输出样本类似这样：
Welcome John.
You are 28 years old.
##1.PHP $_POST
用于收集提交 method="post" 的 HTML 表单后的表单数据。$_POST 也常用于传递变量。
##2.PHP $_GET
$_ GET可用于收集提交HTML表单(method=”get”)之后的表单数据。也可以收集 URL 中的发送的数据。


