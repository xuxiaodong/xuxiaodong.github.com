---
layout: page
title: VimL Crash Course
---

{{ page.title }}
================

VimL 即 Vim script language，它内建于 Vim 中，是一种用来编写 Vim
脚本的程序语言。

数据类型
--------

VimL 主要包括数值、字符串、列表、以及字典等四种数据类型。

### 数值 ###

1. 十进制
2. 十六进制，以“0x”或“0X”打头，如：0x7f 为十进制的 127
3. 八进制，以“0”打头，如：036 为十进制的 30

### 字符串 ###

1. 单引号引起
2. 双引号引起
3. 使用“.”连接

### 列表 ###

    let alist = ['a', 1, 'c']

1. add - 添加元素到列表
2. + - 合并列表
3. extend - 扩展列表

### 字典 ###

    let uk2nl = {'one': 'een', 'two': 'twee', 'three': 'drie'}

变量、赋值及表达式
------------------

### 变量 ###

VimL 的变量名由字母、数字及下划线组成，且开头不能是数字。

变量默认是全局的（但在函数中是局部的），可在变量名前增加前缀改变其作用域。

1. s:name - 局部变量（针对脚本文件）
2. b:name - 局部变量（针对缓冲）
3. w:name - 局部变量（针对窗口）
4. g:name - 全局变量（函数中可见）
5. v:name - Vim 预定义的变量
6. a:name - 函数参数

### 赋值 ###

例：

    let i = 1

### 表达式 ###

1. $NAME - 环境变量
2. &name - 选项
3. @r - 寄存器
4. 算术 `+ - * / %`
5. 逻辑 `== != > >= < <=`
6. 匹配 `=~ !~`
7. 执行 execute normal eval

条件与循环
----------

### 条件 ###

    if 条件
      语句
    [elseif 条件
      语句]
    [else
      语句]
    endif

### 循环 ###

    while 条件
      语句
    endwhile

continue 与 break

    for 变量 in 列表
      语句
    endfor

函数
----

### 定义 ###

    function 名称(参数, ...)
      语句
      [return]
    endfunction

可使用 ! 覆盖已定义的函数。

### 调用 ###

使用 call 或作为表达式调用。

异常
----

    try
      语句
    catch [/错误/]
      语句
    endtry

参考
----

[usr_41](http://vimdoc.sourceforge.net/htmldoc/usr_41.html)
