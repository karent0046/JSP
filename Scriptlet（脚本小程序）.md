# Scriptlet

Scriptlet（脚本小程序），所有嵌入在 HTML 代码中的 Java 程序。

在 JSP 中一共有三种 Scriptlet 代码：都必须使用 Scriptlet 标记出来

## 1、java脚本段	

语法：&lt;% // java脚本段  %&gt;

特点：可以定义局部变量，编写java语句；被编译之后会生成在service方法体中

## 2、声明

语法：&lt;%! // 声明全局变量  %&gt;

特点：可以声明全局变量，方法等；被编译之后生成在servlet类体中

## 3、输出

语法：&lt;%= %&gt;

特点：可以输出变量、表达式或字面量；被编译之后生成在service方法体中；相当于out.print()输出



