===============================
Python 编程语言：简明指南
===============================

Python 是一种高层次的、解释型的编程语言，以其简单易读的语法和强大的功能而闻名。本文将介绍 Python 的一些基本概念和功能。

.. contents::
   :local:
   :depth: 2

Python 简介
============

Python 由 Guido van Rossum 在 1980 年代后期创建，并在 1991 年首次发布。它的设计哲学强调代码的可读性，并使用显式的语法来表达程序的逻辑。

历史背景
---------

Python 的名字来源于喜剧团体 Monty Python。与其名字相反，Python 并不是一门玩笑语言，而是一门广泛应用于各个领域的严肃编程语言。

特点
-----

Python 有以下主要特点：

- 简洁明了的语法
- 丰富的标准库和第三方模块
- 强大的社区支持
- 跨平台兼容性

安装和设置
============

安装 Python 非常简单，你可以从官方 `Python 网站 <https://www.python.org>`_ 下载适用于不同操作系统的安装包。

代码示例
--------

以下是一个简单的 Python 代码示例：

.. code-block:: python

    def hello_world():
        print("Hello, World!")

    if __name__ == "__main__":
        hello_world()

常用数据类型
=============

Python 支持多种数据类型，包括：

整数
----

整数（`int`）是一种基本数据类型，用于表示没有小数部分的数值。

浮点数
------

浮点数（`float`）用于表示带有小数部分的数值。

字符串
------

字符串（`str`）用于表示文本数据。你可以使用单引号或双引号定义字符串。

.. code-block:: python

    message = "Hello, Python!"

列表
----

列表（`list`）是一种有序的可变集合，使用方括号表示。

.. code-block:: python

    fruits = ["apple", "banana", "cherry"]

字典
----

字典（`dict`）是一种无序的键值对集合，使用大括号表示。

.. code-block:: python

    person = {"name": "John", "age": 30}

条件语句和循环
================

条件语句
---------

使用 `if`、`elif` 和 `else` 可以实现条件判断。

.. code-block:: python

    x = 10
    if x < 0:
        print("负数")
    elif x == 0:
        print("零")
    else:
        print("正数")

循环
-----

Python 支持 `for` 循环和 `while` 循环。

.. code-block:: python

    # for 循环
    for i in range(5):
        print(i)

    # while 循环
    count = 0
    while count < 5:
        print(count)
        count += 1

模块和包
========

模块
-----

模块是包含 Python 代码的文件，可以使用 `import` 语句导入模块。

.. code-block:: python

    import math
    print(math.sqrt(16))

包
---

包是包含多个模块的文件夹，通常包含一个 `__init__.py` 文件。

.. _external-link:

更多资源
========

- 官方文档：`Python 文档 <https://docs.python.org>`_
- 社区论坛：`Python 论坛 <https://python-forum.io>`_

结论
====

Python 是一门功能强大且易于学习的编程语言，适合从初学者到专家的各类编程任务。

.. note::

   学习编程是一段旅程，享受编程的乐趣，持续学习和实践，你会成为一名优秀的程序员。

.. tip::

   多练习写代码，多阅读官方文档和优秀的开源项目，有助于提高编程技能。

.. warning::

   编程过程中注意备份代码，以防数据丢失。

**加粗文本示例** 和 *斜体文本示例*。

- 项目一
- 项目二

1. 第一点
2. 第二点

这是一个引用::

    "这是一段引用文本。"

这是一个注脚示例 [#]_。

.. [#] 注脚内容。

再见！

.. image:: https://www.python.org/static/community_logos/python-logo-master-v3-TM.png
   :alt: Python 标志
   :width: 200px
