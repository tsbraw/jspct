Js学习笔记：

1.变量
let / var 变量名;	(定义)
eg. let name = prompt('What is your name?')

变量名 = '字符' / 数值 /..	(初始化)

0-9,a-z,A-Z和下划线命名		(命名规则)
不被允许:
	规则之外、下划线开头、数字开头、保留字(如var\function\let\for..)

数据类型(typeof)		(Number、String、Boolean、Array)
对象	eg. let dog = {name : 'Spot' , breed : 'Dalmatian'};

###JavaScript是一种动态类型语言，不需要指定变量将包含什么数据类型。

算术运算： （+ - * / % **(幂))
旧的Math.pow(7,3) 相当于 7**3	(7是基数,3是指数)
优先级同数学运算；
num++ 先返回num,在返回num+1；++num 先运算；
==/!= 和 ===/!== 前者测试值是否相同,但是数据类型可能不同,而后者的严格版本测试值和数据类型是否相同。


