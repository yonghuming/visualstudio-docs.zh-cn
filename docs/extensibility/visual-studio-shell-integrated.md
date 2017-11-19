---
redirect_url: shell/visual-studio-shell-integrated
title: "Visual Studio Shell （集成） |Microsoft 文档"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d92a6c7250e22972a2b352b74b974601ff6065c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell （集成）
集成的 Visual Studio shell 包括集成的开发环境 (IDE)、 调试器和源代码管理集成。 包含任何编程语言不。 但是，集成的外壳提供一个框架，允许你将添加编程语言。  
  
 集成的 Visual Studio shell 是实际的 Visual Studio 独立 shell 加上的其他安装，包括集成的外壳特定组件组合。  集成的外壳应用程序应包括这两个独立的 shell 可再发行组件包从[Microsoft Visual Studio Shell （独立） 可再发行组件包](http://go.microsoft.com/fwlink/?LinkId=616022)以及集成的外壳可再发行组件包从[Microsoft Visual Studio Shell （集成） 的可再发行组件包](http://go.microsoft.com/fwlink/?LinkId=616021)。  
  
> [!NOTE]
>  你可以访问的隔离和集成 shell 可再发行组件程序包之前，你将需要填写简要客户调查。  填写调查之后, 你将定向到 Visual Studio 连接页，带有可再发行组件包下载链接。  你可以在后续访问的 Visual Studio 连接站点上找到的下载链接**程序 &#124;VISUAL STUDIO 2015 集成和独立 SHELL**选项卡。  
  
 如果作为完整版本的 Visual Studio 的同一计算机上安装集成的外壳应用程序，将直接在 Visual Studio 集成应用程序的组件。  
  
## <a name="features-in-the-integrated-shell"></a>集成外壳中的功能  
  
|||  
|-|-|  
|功能区域|功能|  
|语言支持|-无|  
|IDE|<ul><li>设置<br /><br /> <ul><li>创建设置</li><li>导入和导出设置</li><li>重置设置</li></ul></li><li>**工具箱**集成</li><li>**任务列表**集成</li><li>帮助集成</li><li>**选项**对话框</li><li>字体和颜色管理</li><li>**输出**窗口</li><li>**命令**窗口</li><li>窗口管理</li><li>命令、 菜单和键绑定</li><li>域特定语言 (DSL) 运行时</li></ul>|  
|项目系统和项目类型|-解决方案和解决方案文件夹<br />解决方案配置管理器<br />项管理<br />-单项目和多项目解决方案<br />应用程序设计器 （简化的项目属性）<br />添加 Web 引用<br />-添加服务引用<br />-单项目<br />-网站项目类型<br />Web 应用程序项目|  
|生成|的在 IDE 中自定义生成步骤<br />知识产权 (IP) 保护的预编译<br />代码签名<br />     MSBuild|  
|编辑器|代码浏览工具 （统一的查找、 源定义，继承）<br />代码导航<br />-IntelliSense<br />的智能标记<br />-重构<br />-整齐排列<br />-IntelliSense 筛选<br />-   **代码定义**窗口|  
|Designer|Windows Presentation Foundation 设计器<br />Windows 窗体设计器<br />-Web 设计器和 HTML 编辑器|  
|数据|-   **服务器资源管理器**(简体： 仅限数据)。 请参阅备注 1。<br />-   **数据源**窗口<br />的组完整的数据控件<br />XML 编辑器<br />数据绑定到本地数据源 (。MDF 或。MDB)<br />数据绑定到对象<br />数据绑定到 Web 服务<br />数据绑定到本地数据库服务器<br />数据绑定到远程数据库服务器<br />-远程数据的 DDL 工具<br />-   **服务器资源管理器**扩展性 ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]示例)|  
|调试器|-本地调试。 请参阅备注 2。<br />-托管调试<br />-本地调试<br />-附加到本地进程<br />附加到远程进程<br />匿名委托<br />应用程序域<br />-ASPX 调试<br />-属性<br />-期间 Func eval 中断<br />-断点<br />-断点约束<br />的调用堆栈<br />-   **命令**窗口<br />-跨线程调试<br />数据提示<br />数据可视化工具<br />托管调试助手 (Mda) 的调试程序支持<br />的对类型转发器调试器支持<br />-DTEEvents 支持 OTB<br />-JMC 分档器<br />-调试器 AppID 测试 (DBGCLR)<br />调试程序配置文件<br />-调试器工具和选项<br />调试迭代器<br />设计时表达式计算<br />-C# 表达式计算器<br />-反汇编<br />-编辑并继续<br />表达式计算器 windows （监视，局部变量，自动)<br />-异常帮助器<br />-异常<br />执行<br />-   泛型<br />-获取正确的源<br />HPC/群集调试<br />的集成多语言调试<br />-互操作调试<br />--实时调试<br />-本地调试<br />-托管调试<br />-手动控件 （进程窗口中）<br />内存<br />-小型转储支持<br />-模块<br />-多进程调试<br />本机调试<br />-新调试引擎支持<br />-优化代码调试<br />的筛选输出窗口<br />-处理承载的托管调试<br />-进程<br />-快速监视<br />-注册<br />的堆栈中寄存器<br />-远程调试<br />的返回值<br />-脚本调试<br />源服务支持<br />安全<br />---并行<br />SQL<br />符号服务器<br />跟踪点<br />线程<br />的可视化效果<br />可扩展样式表语言转换 (XSLT) 调试器|  
|64 位支持|-64 位调试对于托管和本机代码，所有语言<br />-x64 本机支持|  
|源代码管理 (SCC)|-基本 SCC 集成。 请参阅备注 3。<br />-工具和选项验证|  
|扩展性|-使用 Vspackage 和 MEF 组件|  
  
## <a name="notes"></a>说明  
  
#### <a name="1-data-tools"></a>1.数据工具  
 集成的外壳包括数据库开发工具，例如数据扩展性支持和简化**解决方案资源管理器**。 但是，SQL Server Express、 SQL Reporting，和 Crystal Reports 不包含在集成外壳。  
  
#### <a name="2-debugging-support"></a>2.调试支持  
 集成的外壳包括相同的 Visual Studio 的社区版本中包含的调试引擎。 调试引擎包括公共调试器用于托管的代码中，并作为相关的功能，如运行，附加、 设置断点、 编辑并继续，以及其他。 但是，调试引擎不支持 SQL Server 数据库调试。  
  
 尽管支持本机调试包含对的基本调试器包中，不能进行扩展以支持其他语言。  
  
#### <a name="3-source-code-control-integration"></a>3.源代码管理集成  
 集成的外壳提供了 Api，用于实现源代码管理 (SCC) 和提供 MSSCCI 基于常见的源控制集成组件。  
  
 虽然 SCC 集成不是 Visual Studio 专业版的一项常规功能，SCC 集成中提供了集成外壳。  
  
#### <a name="4-build-support"></a>4.生成支持  
 集成的外壳提供生成支持。 你可以找到有关在中生成信息[MSBuild 参考](../msbuild/msbuild-reference.md)。  
  
## <a name="features-not-included-in-the-integrated-shell"></a>在集成外壳中未包括的功能  
 下面是集成外壳中未包括的功能的列表：  
  
-   类设计器  
  
-   [PreEmptive 保护-Dotfuscator](../ide/dotfuscator/index.md)  
  
-   语言功能  
  
-   VSHost  
  
-   没有 Visual Studio 语言或其关联的项目模板或项目项模板，都将纳入集成外壳。 其他功能的任何特定于语言的实现不都包括在内，有关示例 Visual Basic 代码段。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)