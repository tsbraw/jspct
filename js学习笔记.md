Js学习笔记：

### 变量
	var 变量名;	(定义)
	eg. let name = prompt('What is your name?')
	变量名 = '字符' / 数值 /..	(初始化)
	0-9,a-z,A-Z和下划线命名		(命名规则)
	不被允许:
		规则之外、下划线开头、数字开头、保留字(如var\function\let\for..)

	数据类型(typeof)		基本(Number、String、Boolean、Null、Undefined、Symbol) 引用(Object)
	对象	eg. let dog = {name : 'Spot' , breed : 'Dalmatian'};
	
	#JavaScript是一种动态类型语言，不需要指定变量将包含什么数据类型。
	
	算术运算： （+ - * / % **(幂))
	旧的Math.pow(7,3) 相当于 7**3	(7是基数,3是指数)
	优先级同数学运算；
	num++ 先返回num,在返回num+1；++num 先运算；
	==/!= 和 ===/!== 前者测试值是否相同,但是数据类型可能不同,而后者的严格版本测试值和数据类型是否相同。

### 字符串
	eg. let string = 'Wubba lubba dub dub';		//不区分'' ""
	转义字符 \	eg. 'I\'ve' => I've 
	连接字符串 +		eg.let mulString = string + '!!!';  //concat()连接两个或多个字符串or数组

	字符串+数值 会将数字转换为字符串;	eg. 'Cris' + 24; ans:'Cris24'.
	typeof('12' + '36'); ans:string.
	toString()方法 and Number()方法.	
	
	字符串做对象：
		获取长度:length 			eg.string.length;
		检索特定字符				   string[0];
		查找字符串 indexOf()		   string.indexOf('lub'); ans:6
		提取字符串 slice()		   string.slice(1,3); 	 'ub' 
								   string.slice(2);		 'ubba lubba dub dub'
		转换大小写 toLowerCase()	   string.toLowerCase(); 'wubba lubba dub dub'
				  toUpperCase()	   string.toUpperCase(); 'WUBBA LUBBA DUB DUB'
		替换某部分 replace()		   string.replace('bba','aab'); 'Wuaab lubba dub dub'


### 数组
	let array = ['e1','e2','e3',...]
	多维数组:
		array=[][] 	eg.random[2][2];
	访问和修改数组:
		array[0] 	ans:'e1';
		array[0] = 'e0';
			//array will now return ['e0','e2','e3',...]
	获取长度 array.length;
	字符串分割为数组 split():
		string.split(separator,howmany);
		  separator必须,从指定地方分割string.
		  howmany可选,指定返回数组的最大长度.
	数组转字符串 join()/toString();
		array.join(separator); 	separator可选,指定要使用的分隔符,默认为','.
	添加和删除:
		push()和pop(); 		在结尾处.
		unshift()和shift(); 	在开头处.

	splice()参数1 添加／删除 的起始位置;参数2 要删除的项目数量。如果设置为 0，则不会删除项目;
	参数3 向数组添加的新项目(可以添加多个).
	reverse() 颠倒数组中元素的顺序,并返回颠倒顺序后的数组.

### 条件
	if..else语法:
		if(condition) {
			code to run if condition is true
		} else {
			run other code
		}
	&& 逻辑与 	|| 逻辑或 	! 逻辑非

	switch语句:
		switch (expression) {
			case chioce1:
				run this code
				break;
			case chiose2:
				run this code instead
				break;
			...
			default:
				acyually,just run this code
		}
	
	三元运算符:
		(condition) ? true run this : false run here;

### 循环
	for:							**优先**
		for (initializer; exit-condition; final-expression) {
		  // code to run
		}
	break退出循环,并使浏览器移动到跟随它的任何代码

	while 和 do...while:
		while:
			initializer
			while (exit-condition) {
			  // code to run
			  final-expression
			}
	
		do...while:
			initializer
			do {
			  // code to run
			  final-expression
			} while (exit-condition)

### 函数与方法
	function myFunction() {			**推荐**
		my codes here;
	}
	匿名函数:
	function() {
		codes here;
	}
	通常使用匿名函数以及事件处理程序:
		eg.myButton.onclick = function() {
				codes here;
			}
	将匿名函数分配为变量的值:
	

```
	var myVary = function(){
			my codes;
		}
		myVary();		//可以用来调用此函数
```



	作用域与冲突:
		多个同名函数在html中被调用,仅以最后一个的内容实现.
		将代码锁定在函数中的部分避免了这样的问题,并被认为是最佳实践.
	
	返回值:
		replace()函数:


### 事件
	addEventListener():
		button.addEventListener('click',function);
	||	button.onclick = function;
	removeEventListener():
		button.removeEventListener('click',function);

 	* 给同一个监听器注册多个处理器
		myElement.addEventLister('click',functionA);
		myElement.addEventLister('click',functionB);

 	* 事件对象
		function bgChange(event) {
			var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
			event.target.style.backgroundColor = rndCol;
			console.log(event);
		}
		event 为事件对象; event 的 target 属性始终是事件刚刚发生的元素的引用

 	* 阻止默认行为
		form.onsubmit = function(e) {
			if (fname.value === '' || lname.value === '') {
				e.preventDefault();
				para.textContent = 'You need to fill in both names!';
			}
		}
		onsubmit事件处理程序:在提交的时候,在一个表单上发起submit事件
		在事件对象上调用preventDefault()函数,停止了表单提交

 	* 事件冒泡与获取
		在捕获阶段：
		浏览器检查元素的最外层祖先<html>，是否在捕获阶段中注册了一个onclick事件处理程序，如果是，则运行它。
		然后，它移动到<html>中单击元素的下一个祖先元素，并执行相同的操作，然后是单击元素再下一个祖先元素，依此类推，直到到达实际点击的元素。
	
		在冒泡阶段，恰恰相反:
		浏览器检查实际点击的元素是否在冒泡阶段中注册了一个onclick事件处理程序，如果是，则运行它
		然后它移动到下一个直接的祖先元素，并做同样的事情，然后是下一个，等等，直到它到达<html>元素。

 	* stopPropagation()修复问题
		标准事件对象具有可用的名为 stopPropagation()的函数, 当在事件对象上调用该函数时，它只会让当前
		事件处理程序运行，但事件不会在冒泡链上进一步扩大，因此将不会有更多事件处理器被运行(不会向上冒泡)。

### 对象
	var obj = {};
		控制台输入obj:[object Object]
	访问 obj.object || obj['object']

 	* 设置对象成员
		可以创建新的成员
		 eg. obj['object0'] = 'object0'
 	* this的含义
		关键字"this"指向了当前代码运行时的对象

	函数:
		function Person(name,age,....){coding}
		var person1 = new Person('name',age,...)

	Object()构造函数:
		var person2 = new Object();		//定义了空对象
		person2.neme = 'Here';
		...

	create()方法:
		var person3 = Object.crerate(person1)

 	* 原型
		prototype:
			eg.Person.prototype.greeting = function() {  };

		从无参构造函数继承:
			function Brick() {
				this.width = 10;
				this.height = 20;
			}
			function BlueGlassBrick() {
				Brick.call(this);
				this.opacity = 0.5;
				this.color = 'blue';
			}
			call(this)继承width和height属性,我们仅传入了this到call()中 - 不需要其他参数

		Teacher.prototype = Object.create(Person.prototype);
			Teacher.prototype现在会继承Person.prototype的所有属性和方法;现在
			Teacher()的prototype的constructor属性指向的是Person().
				Teacher.prototype.constructor = Teacher;	将constructor属性指向Teacher()

### JSON
	·JSON 是一种纯数据格式，它只包含属性，没有方法。
	·JSON 要求有两头的 { } 来使其合法。最安全的写法是有两边的括号，而不是一边。
	  甚至一个错位的逗号或分号就可以导致  JSON 文件出错。您应该小心的检查您想使用的数据(虽然计算机生成的 JSON 
	  很少出错，只要生成程序正常工作)。您可以通过像 JSONLint 的应用程序来检验 JSON。
	·JSON 可以将任何标准合法的 JSON 数据格式化保存，不只是数组和对象。比如，一个单一的字符串或者数字可以是合法的JSON 
	  对象。虽然不是特别有用处……
	·不像 JavaScript 标识符可以用作属性，在 JSON 中，只有字符串才能用作属性。

	对象和文本间的转换
		浏览器拥有一个内建的 JSON，包含以下两个方法:
			parse(): 以文本字符串形式接受JSON对象作为参数，并返回相应的对象。
			stringify(): 接收一个对象作为参数，返回一个对应的JSON字符串。

### 线程
	JavaScript一般来说是单线程的.

 	* 实现异步开发
 		+ 函数
 			- setTimeout()	在指定的时间后执行一段代码. 
 				调用clearTimeout()，将setTimeout()调用的标识符作为参数传递给它，从而在超时运行之前取消.
 			- setInterval()	以固定的时间间隔，重复运行一段代码.
 				clearInterval()函数,停止运行setInterval().
 			- requestAnimationFrame()	setInterval()的现代版本;在浏览器下一次重新绘制显示之前执行指定的代码块，
 										从而允许动画在适当的帧率下运行，而不管它在什么环境中运行.
