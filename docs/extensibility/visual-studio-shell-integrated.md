---
title: "Visual Studio Shell (集成) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 提示、 集成模式的功能"
  - "Shell [Visual Studio]，集成模式下的功能"
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio Shell (集成)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 集成 shell 包括集成的开发环境 \(IDE\)、 调试器和源代码管理集成。 任何编程语言不是包括在内。 但是，该集成的 shell 提供一个框架，允许您添加的编程语言。  
  
 Visual Studio 集成 shell，实际上是组合的隔离的 Visual Studio shell 再加上其他安装，其中包括集成的外壳特定组件。  集成的外壳应用程序应包括这两个独立的 shell 可再发行组件包从 [Microsoft Visual Studio Shell \(独立\) 可再发行组件包](http://go.microsoft.com/fwlink/?LinkId=616022) 以及从集成的外壳可再发行组件包 [Microsoft Visual Studio Shell \(集成\) 可再发行组件包](http://go.microsoft.com/fwlink/?LinkId=616021)。  
  
> [!NOTE]
>  你可以访问独立和集成外壳可再发行组件程序包之前，您将需要填写简短客户调查。  填写调查之后, 您将被定向到 Visual Studio 连接页面的可再发行组件包的下载链接。  您可以在以后访问的 Visual Studio Connect 站点上找到的下载链接 **程序 &#124;VISUAL STUDIO 2015 集成和独立 SHELL** 选项卡。  
  
 如果在与 Visual Studio 的完整版相同的计算机上安装集成的外壳应用程序，将直接在 Visual Studio 集成应用程序的组件。  
  
## 该集成 Shell 中的功能  
  
|||  
|-|-|  
|功能区域|功能|  
|语言支持|-   无|  
|IDE|<ul><li>设置<br /><br /> <ul><li>创建设置</li><li>导入和导出设置</li><li>重置设置</li></ul></li><li>**工具箱** 集成</li><li>**任务列表** 集成</li><li>帮助集成</li><li>**选项** 对话框</li><li>字体和颜色管理</li><li>**输出** 窗口</li><li>**命令** 窗口</li><li>窗口管理</li><li>命令、 菜单和键绑定</li><li>域特定语言 \(DSL\) 运行时</li></ul>|  
|项目系统和项目类型|-   解决方案和解决方案文件夹<br />-   解决方案配置管理器<br />-   项目管理<br />-   单一项目和多项目解决方案<br />-   应用程序设计器 \(简化的项目属性\)<br />-   添加 Web 引用<br />-   添加服务引用<br />-   单一项目<br />-   Web 站点项目类型<br />-   Web 应用程序项目|  
|生成|-   在 IDE 中的自定义生成步骤<br />-   预编译的知识产权 \(IP\) 的保护<br />-   代码签名<br />     MSBuild|  
|编辑器|-   代码浏览工具 \(统一的查找、 源定义，继承\)<br />-   代码导航<br />-   IntelliSense<br />-   智能标记<br />-   重构<br />-   整齐排列<br />-   IntelliSense 筛选<br />-   **代码定义** 窗口|  
|设计器|-   Windows Presentation Foundation 设计器<br />-   Windows 窗体设计器<br />-   Web 设计器和 HTML 编辑器|  
|数据|-   **服务器资源管理器** \(简化: 仅限数据\)。 请参阅备注 1。<br />-   **数据源** 窗口<br />-   组完整的数据控件<br />-   XML 编辑器<br />-   数据绑定到本地数据源 \(。MDF 或。MDB\)<br />-   数据绑定到对象<br />-   数据绑定到 Web 服务<br />-   将数据绑定到本地数据库服务器<br />-   将数据绑定到远程数据库服务器<br />-   远程数据的 DDL 工具<br />-   **服务器资源管理器** 扩展性 \([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 示例\)|  
|调试器|-   本地调试。 请参阅备注 2。<br />-   托管调试<br />-   本地调试<br />-   附加到本地进程<br />-   附加到远程进程<br />-   匿名委托<br />-   应用程序域<br />-   ASPX 调试<br />-   特性<br />-   Func eval 期间中断<br />-   断点<br />-   断点约束<br />-   调用堆栈<br />-   **命令** 窗口<br />-   跨线程调试<br />-   数据提示<br />-   数据可视化工具<br />-   托管调试助手 \(Mda\) 的调试器支持<br />-   类型转发器的调试器支持<br />-   对 OTB DTEEvents 支持<br />-   JMC 分档器<br />-   调试器 AppID 测试 \(DBGCLR\)<br />-   调试器的配置文件<br />-   调试器工具和选项<br />-   调试迭代器<br />-   设计时表达式计算<br />-   C\# 表达式计算器<br />-   反汇编<br />-   编辑并继续<br />-   表达式计算器 windows \(监视，局部变量，自动\)<br />-   异常帮助器<br />-   异常<br />-   执行<br />-   泛型<br />-   获取正确的源代码<br />-   HPC\/群集调试<br />-   集成多语言调试<br />-   互操作调试<br />-   在实时调试<br />-   本地调试<br />-   托管调试<br />-   手动控制 \(进程窗口\)<br />-   内存<br />-   小型转储支持<br />-   模块<br />-   多进程调试<br />-   本机调试<br />-   新的调试引擎支持<br />-   调试优化的代码<br />-   筛选的输出窗口<br />-   进程托管的托管调试<br />-   进程<br />-   快速监视<br />-   寄存器<br />-   堆栈中的寄存器<br />-   远程调试<br />-   返回值<br />-   脚本调试<br />-   源服务支持<br />-   安全性<br />-   通过并行<br />-   SQL<br />-   符号服务器<br />-   跟踪点<br />-   线程<br />-   可视化效果<br />-   可扩展样式表语言转换 \(XSLT\) 调试器|  
|64 位支持|-   64 位调试对于托管和本机代码，所有语言<br />-   x64 本机支持|  
|源代码管理 \(SCC\)|-   SCC 的基本集成。 请参阅备注 3。<br />-   工具和选项的验证|  
|扩展性|-   使用 Vspackage 和 MEF 组件|  
  
## 备注  
  
#### 1.Data Tools  
 该集成的 shell 包括数据库开发工具，例如数据可扩展性支持和简化 **解决方案资源管理器**。 但是，SQL Server Express、 SQL Reporting，和 Crystal Reports 不包括在集成外壳中。  
  
#### 2.调试支持  
 该集成的 shell 包括同一社区版本的 Visual Studio 中包含的调试引擎。 调试引擎包括常见的调试器，用于托管的代码中，以及相关的功能，如运行，请附加、 设置断点、 编辑并继续，以及其他人。 但是，调试引擎不支持 SQL Server 数据库调试。  
  
 尽管支持本机调试包含对的基本调试器包中，不能进行扩展以支持其他语言。  
  
#### 3.源代码管理集成  
 该集成的 shell 提供的 Api，用于实现源代码管理 \(SCC\) 以及提供 MSSCCI 基于常见的源控制集成组件。  
  
 虽然 SCC 集成不是 Visual Studio Pro edition 》 的固定专栏，该集成 shell 中提供源代码管理集成。  
  
#### 4.生成支持  
 该集成的 shell 提供了生成支持。 您可以找到有关中的生成信息 [MSBuild 参考](../msbuild/msbuild-reference.md)。  
  
## 该集成 Shell 中不包括的功能  
 下面是该集成 shell 中不包括的功能的列表:  
  
-   类设计器  
  
-   强占式 DotFuscator  
  
-   语言功能  
  
-   VSHost  
  
-   无 Visual Studio 语言或其关联的项目模板或项目项模板包含在该集成 shell 中。 其他功能没有特定于语言的实现，但会包括用于示例的 Visual Basic 代码段。  
  
## 请参阅  
 [扩展 Visual Studio 概述](../Topic/Extending%20Visual%20Studio%20Overview.md)