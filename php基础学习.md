####   php基础学习



```
1.php变量
<?php
$a = rand(0, 9);
$b = $a // 不会开辟空间
$a = rand(0,9);//值改变后会开辟空间
$b = &$a;
memory_get_usage($b);
xdebug_debug_zval($b)
unset($b); //unset只会取消引用

对象本身就是引用传递

题目;
/**<?php 
	$data = ['a', 'b', 'c'];
	foreach($data as $key => $val)
	{
		$val = &$data[$key];
	}
	程序运行时，每一次循环结束后变量$data的值是什么 请解释？
	程序执行完成后，变量$data的值是什么？请解释？
	*/
	第一次$data是['a', 'b', 'c']
	第二次$data['b', 'b', 'c']
	第三次$data['b', 'c', 'c']

2.php字符串可以用哪三种定义方法及各自区别是什么
定义方式
单引号  //单引号不能解析变量，不能解析转义字符，只能解析单引号和反斜线本身，变量和变量，变量和字符串、字符串和字符串之前可以用.连接
双引号  //双引号可以解析变量，变量可以使用特殊字符和{}包含，双引号可以解析所有转义字符，也可以使用.连接
区别 单引号的效率更高
heredoc和newdoc

heredoc写法类似双引号
$str = <<< EoT
.
.
.
EoT

newdoc 
$str = <<< 'EoT'
.
.
.
'EoT'


数据类型
三大数据类型(标量（整形、浮点、字符串、布尔）、复合（数组和对象）、特殊（NULLfa和resource资源）)
浮点类型 float 不能用于比较运算，如==的比较
布尔型  //0， 0.0，' ','0',false,array(),NULL这七种都是false
超全局数组 $GLOBALS、$_GET、$_POST、$_REQUEST、$_SESSION、$_COOKIE、$_SERVER、$_FILES、$_ENV
常量const define const是语言结构，速度快，定义后不可修改，不可删除，可以定义类的变量 define是一个方法 
预定义常量__FILE__、__LINE__、__DIR__、__FUNCTION__、__CLASS__、__TRAIT__、__METHOD__、__NAMESPCE__

3.运算符的考点
php所有运算符
1.运算符的优先级  递增/递减>!>算术运算符>大小比较>(不)相等比较>引用>位运算符(^)>位运算符(|)>逻辑与>逻辑或>三目>赋值>and>xor>or
2.比较运算符 ==和====区别
3.递增/递减运算符  递增/递减运算符不影响布尔值 递减NULL值没有效果 递增NULL值为1 递增和递减在前就先运算符后返回，反之就先返回，后运算
4.逻辑运算符  短路作用  ||和&&与or和and的优先级不同
5.错误控制符 @放在php表达式之前，该表达式可能产生的任何错误信息都会被忽略掉

真题
foo()和@foo()之间的区别
下列程序中请写出打印输出的结果
<?php
$a = 0;
$b = 0;
if($a = 3>0|| $b=3>0)
{
	$a++;
	$b++;
	echo $a. "\n";
	echo $b. "\n";
}

1 1

4.流程控制
列出遍历数组的三种方式及各自区别
1.for  只能遍历索引数组 
2.foreach   foreach遍历会对数组进行reset操作
3.while（）、list（）、each（）组合循环

php分支结构
1.if(exp)
elseif(exp2)
elseif(exp2)
else{}

switch(exp)
case ...;
continue;
||
break;
case ...;
breack;
default: ...;
break;

区别效率switch case的效率会高一些，sitch ...case的条件只能是整形、浮点型或字符串

真题 php中如何优化多个if... else 语句的情况
1.把出现次数多的情况放在判断条件的前面
2.对于复杂的条件判断，如果条件是整型、浮点型、字符串，可以把判断改用switch ...case

```





方法  memory_get_usage()获取内存大小

xdebug方法