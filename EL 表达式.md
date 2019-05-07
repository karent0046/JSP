# EL表达式

语法:${域对象的key值}---仅限域变量名

注意点:

1.el表达式操作的是域对象中的值,无法操作局部变量

2.JSP中域对象4个范围:page(本页面),request(一次请求),session(一次会话),application(整个应用程序)

3.如果U盾讴歌域范围内存在同域名对象,el表达式的取值范围是从小范围到大范围,取到即止,取不到则返回空字符串

4.可以获取指定域对象的值:pageScope,requestScope,sessionScope,applicationScope(一般不会特意取重名,了解即可)

5.获取javaBean的属性值:${存在域对象中的对象名.属性名}javaBean中的属性必须提供getter方法

6.判断对象是否为空:${empty 域对象名称} 不为空${!empty 域对象名称}

list取值:${list[下标]}

map取值:${map.key}或${map["key"]

等值比较: ==(主要) 或 eq(了解) ${对象1 == 对象2}或${对象1 eq 对象2}

其他运算符<> +-*/同上(除法有2种写法/和div);$(a+b>c)

```
//存request对象
		request.setAttribute("uname", "zhangsan");
	 //测试其余3种(自小到大顺序) 
	 	pageContext.setAttribute("uname", "zhangsan2");
	 	//request.setAttribute("uname", "zhangsan");
	 	session.setAttribute("uname", "zhangsan3");
	 	application.setAttribute("uname", "zhangsan4");
	 //定义变量(测试取不到局部变量值;浏览器输出结果:获取request域对象的值:zhangsan---;后面取不到userName的值)
		 String userName ="lisi";
	 
	 //将javaBean存到域对象中
		User user = new User();
	 	user.setUname("哈哈");
	 	//myUser为user的对象所以是myUser.uname
	 	request.setAttribute("myUser", user);
	//List 集合	
	 	List<String> list = new ArrayList<String>();
	 	list.add("aaa");
	 	list.add("bbb");
	 	list.add("ccc");
	 	request.setAttribute("list", list);
	 	
	 	List<String> list2 = new ArrayList<String>();
	 	request.setAttribute("list2", list2);
	 	
	 	List<String> list3 = null;
	 	request.setAttribute("list3", list3);
	 // Map对象
	 Map map = new HashMap();
	 map.put("aaa","111");
	 map.put("bbb",222);
	 map.put("ccc-a",333);
	 request.setAttribute("map", map);
	 
	 //设置域对象
	 request.setAttribute("str", "aa");
	 request.setAttribute("str2", "bb");
	 request.setAttribute("str3", "aa");

	 request.setAttribute("num", 10);
	 request.setAttribute("num2", 1);
	 request.setAttribute("num3", 2);
	 request.setAttribute("num4", 10);
   
 <h3>获取域对象的值及判断</h3>
 <h6>pageContext范围：${uname }</h6>
 <h6>获取指定范围的值：${requestScope.uname }</h6>
 <h6>获取JavaBean的值：${user }</h6>
 <h6>获取JavaBean的指定属性值：${user.uname }</h6>
 <h6>获取变量的值：${str }</h6>
 <h6>判断JavaBean对象是否为空：${empty user }</h6>
 <h6>判断域对象是否不为空：${!empty str }</h6>
 <h6>判断List集合是否为空且长度是否小于1：${empty list }</h6>
 <h6>判断List集合是否为空且长度是否小于1：${empty list2 }</h6>
 <h6>得到List集合的长度：${list2.size() }</h6>
 <h6>得到字符串的长度：${uname.length() }</h6>
 <h6>获取List集合中指定下标的值：${list2[2] }</h6>
 <h6>获取Map中指定key的值：${map.bbb }</h6>
 <h6>获取Map中指定key的值：${map["ccc-a"] }</h6>
 <h3>EL运算</h3>
 <h6>加法：${1+1 } -- ${num1 + 10 } --- ${num1+num2 }</h6>
 <h6>除法：${num2 / num1} --- ${num2 div num1 }</h6>
 <h6>判断：${num1 > 0 } -- ${num2 > num1 }  -- ${num1 + 10 > num2 } -- ${num1 + 10 >= num2 } -- ${num1 + 10 <= num2 + 1 }</h6>
 <h6>等值比较：${num1 == num2 } -- ${str1 == str2 } -- ${str1 eq str3 }</h6>
 <h6>字符串截取：${str1.substring(0,1) }</h6>
 ```
 
