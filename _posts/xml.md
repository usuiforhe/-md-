---
title: xml
date: 2017-09-26 20:59:29
tags:
---
## xml概述：

	可扩展标记语言。(Extensible Markup Language)  
	允许开发者自由定义标签，可以将标签和内容有效分离。  
	xml不再侧重于数据如何展示，二十更过的关注数据如何存储和传输。  
 
## xml应用场景：  

	1. xml把数据从HTML分离出来。那温度距离，用html注重于显示而无关数据，用xml改变数据，让html读取。  
	2. 简化数据共享。提供了独立于软件和硬件的存储方式。  
	3. 简化数据的传输。通过xml，可以在不兼容的系统之间传输数据。  
	4. 简化平台的变更。  

## xml的优势：  

	1. 简单易用的标记预语言。xml标签可以自己自由定义。
	2. 严格的格式。比html标签控制更严格。
	3. 数据逻辑和显示逻辑分离。html注重于显示，xml注重于数据存储。

## xml文档规则：  

	1. 有且只有一个根元素
	2. 元素必须合理结束
	3. 元素之间必须合理嵌套
	4. 元素的属性必须有值

## xml存储信息：  

	例如：书名	作者	价格  
  	     java思想	小王	79.00  
   	     Spring指南	小李	89.00  

## xml的写法  

### 字符集：

	1. 简体中文：GBK 或 GB2312
	2. 繁体中文：BIG5
	3. 西欧字符：ISO8859-1
	4. 通用的国际编码：Unicode
	5. 针对Unicode的可变长度字符编码UTF8

### 合法标签名：

	xml元素由开始标签和结束标签组合，结束标签比开始标签多一条斜线
	xml文档区分大小写。所以，开始标签和结束标签必须绝对相同，大小写也要完全一致
	标签名可以字母（包括非西欧字符），数字，下划线，中划线，冒号，点号组成，但是不能以数字，中划线和点号开头
	不能包括 ‘< > , $’
	标签名尽量不要出现英文冒号“:”, 除非是在使用名空间
	标签名不能以字符“xml”等任意大小写组合开始
	标签名不能包含空格

### 空元素：

	例：<元素名 属性名="  " />
	空元素不是内容为空的元素，空元素不接受子元素，也不接受字符内容

	<?xml version="1.0" encoding="GB2312" standalone = "yes" ?>
	<书籍列表>
		<书名> java思想</书名>
		<价格>79.00</价格>
		<作者>小王</作者>
		<书名>Spring指南</书名>
		<价格>89.00</价格>
		<作者>小李</作者>
	</书籍列表>
	那么 <书籍列表> 就是根元素

## 字符数据：  
	开始标签和结束标签之间的文本可以是任何Unicode字符，并且其间的任何字符都重视的传递给xml处理程序
	但是如果中间由 < 或者 & 字符，容易导致辨认错误。例如： <test> 1 + 1 < 3</test>， 这样用浏览器打开就会显示错误。
	解决方法：
		1. 使用实体应用（xml定义了五种实体引用）（记得后面要加分号）：
			&lt;   	--->     "<"   小于符号
			&gt;  	--->     ">"   大于符号
			&amp;  	--->     "&"   and符号 &
			&apos;	--->     "'"     英文单引号
			&quot;	--->     """     英文双引号
		2. 使用CDATA标记
		    在特殊标记CDATA下，所有的特殊字符，甚至是有效元素都将被当成简单字符处理
		    实体引用也会失去作用，变成纯文本
		    语法：
			<![CDATA[文本内容]]>

## 换行处理：  
	目前主流的操作系统，主要由3种换行符：
		1. Windows平台：回车符（CR） 和 换行符 （LF） 的组合存储换行
		2. Unix和Linux平台：以换行符（LF）存储换行
		3. Macintosh平台：以回车符（CR）存储换行
	xml同一换行符（LF） 存储换行

## 命名空间：  
	同一份xml文档中可能出现多个同名的元素和属性。必须添加标记判断
	语法：
		xmlns[:prefix]= "命名空间字符串"
		xmlns -> xml namespace
	例如：
		xmlns:hehe = "http://www.***.com"
		<hehe:name>java思想</hehe:name>
