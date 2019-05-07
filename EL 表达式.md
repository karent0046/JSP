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
pageContext.setAttribute("uname", "zhangsan");
	request.setAttribute("uname", "lisi");
	session.setAttribute("uname", "wangwu");
	application.setAttribute("uname", "zhaoliu");
	
	// 通过pageContext对象设置指定域范围的值
	pageContext.setAttribute("a", "aaa", PageContext.REQUEST_SCOPE);
	
	
	// 将user对象存到作用域中
	User user = new User();
	user.setUname("admin");
	user.setUpwd("123456");
	request.setAttribute("user", user);
	
	//定义变量(测试取不到局部变量值;浏览器输出结果:获取request域对象的值:zhangsan---;后面取不到userName的值)
	String userName ="lisi";
	
	// List集合
	List<String> list = new ArrayList<>();
	request.setAttribute("list", list);
	
	List<String> list2 = new ArrayList<>();
	list2.add("aaa");
	list2.add("bbb");
	list2.add("ccc");
	list2.add("ddd");
	request.setAttribute("list2", list2);
	
	
	// Map
	Map<String,Object> map = new HashMap<String,Object>();
	map.put("aaa", "111");
	map.put("bbb", 2222);
	map.put("ccc-a", 333);
	request.setAttribute("map", map);
	
	
	request.setAttribute("num1", 10);
	request.setAttribute("num2", 50);
	
	request.setAttribute("str1", "aaa");
	request.setAttribute("str2", "bbb");
	request.setAttribute("str3", "ccc");
 ```
 输出:
 
获取域对象的值及判断

pageContext范围：zhangsan

获取指定范围的值：lisi

获取JavaBean的值：com.shsxt.po.User@7cb75296

获取JavaBean的指定属性值：admin

获取变量的值：

判断JavaBean对象是否为空：false

判断域对象是否不为空：false

判断List集合是否为空且长度是否小于1：true

判断List集合是否为空且长度是否小于1：false

得到List集合的长度：4

得到字符串的长度：8

获取List集合中指定下标的值：ccc

获取Map中指定key的值：2222

获取Map中指定key的值：333

EL运算

加法：2 -- 20 --- 60

除法：5.0 --- 5.0

判断：true -- true -- false -- false -- true

等值比较：false -- false -- false

字符串截取：a

