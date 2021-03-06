书籍仓储管理
=====

简介
----
一个基于MySQL的书籍仓储管理的雏形，采用Qt实现了简单的可视化用户界面，平台Windows。

功能简述
----

### 仓库构建
1、仓库初始化。
2、货架初始化。

### 入库功能
1、填表入库。
2、批量入库。


### 出库功能

1、填表出库。
2、批量出库。
3、设计捡货路线。

### 查询功能

1、按描述查询。
2、按货架查询。

### 使用说明
保证你的sql已经引入了store_0.sql中建立好的数据。

初始化过程：
1、首先，初始化仓库数据。
2、选中仓库修改模式，拖动生产一个矩形框作为仓库轮廓，在弹出的对话框内，指明仓库规格和集散点坐标（作为捡货路径的起点和终点）等信息。
3、然后，可以选中货架修改模式，拖动产生一个矩形框作为一个货架的轮廓，在弹出的对话框内填写相关信息。（软件会自动解决货架冲突的判断问题）

入库过程：
1、点击选中货物入库按钮，点击批量入库，然后选择一个标准输入文件（各项以制表符分割）。即可完成批量入库。
2、填表入库，点击初始化表项，填写表项，点击表项货物入库，即可将表内信息完整的货物入库。

出库过程：
1、点击选中货物出库按钮，点击批量出库，然后选择一个标准输出文件（各项以制表符分割）。即可完成批量出库。
2、填表出库，点击初始化表项，填写表项（指明类型、名称、数量），点击显示路径，生产捡货路径，完成之后点击表项货物出库即可完成出库。

货物检索：
1、按货架检索，选中查询模式，点击货架，即可获得货架之内货物的列表信息。
2、按描述检索，在货物检索中填写检索关键词，选择搜索域（名称、类别、描述），点击检索货物，即可得到（名称、类别、描述）中包含关键词的货物信息。


代码文件概述
----

dbms.h 提供数据库功能接口的封装。


* storehouse.h 表述仓库的实体类。
* conhouse.h 表述仓库的控制类，用于执行仓库的插入和删除。

* storeshelf.h 表述货架实体类。
* conshelf.h 表述货架的控制类，用于执行货架的插入和删除、和货架图形化的位置计算。

* storebill.h 表述货单的实体类，提供货单相关信息。
* conbill.h 表述货单的控制类，提供执行货单、捡货路径计算、批量出库等接口。

* storeitem.h 表述货物（即书籍）的实体类。
* conitem.h 表述货物的控制类，执行货物的删除、插入、按描述查询、按货架查询、更改存量的工作。

* housedialog.h 表述了仓库建立的软件界面。
* shelfdialog.h 表述了货架建立的软件界面。
* storescene.h 表述了可视化仓库表示的软件界面，用于支持包括集散点的重定位、货架建立删除的操作等等。

* mainwindow.h 用于联系界面的各类操作和各个控制类。

实体属性
----
仓库：编号	名称	坐标	宽	高	描述
货架：编号	名称	所属仓库	坐标	宽	高	方向	分栏	层数	描述
货物：编号	名称	类别	数量	所属货架	方向	分栏	分层	描述

依赖
----
编译前请确认pro文件中的文件路径设置符合环境。
需要较高版本的MySQL，，可以引入data文件夹下面的store_0.sql引入已经建立好的数据库。
需要QtGui4.dll QtCore4.dll libmysql.dll mingwm10.dll 等动态库文件的支持。

注意！文件夹路径不要使用任何非ASCII字符(特别不能使用中文路径)。

data下面提供了几组测试数据 in 文件表示批量输入的ASCIII编码的文件，out 文件表述货物批量输出的ASCIII编码的文件。


