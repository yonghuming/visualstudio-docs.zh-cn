---
title: "如何：调试 ActiveX 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件容器调试 [Visual Studio]"
  - "ActiveX 控件, 调试"
  - "容器, 为调试会话指定"
  - "数据绑定控件, ActiveX"
  - "调试 ActiveX 控件"
  - "测试容器"
  - "测试 [Visual Studio], ActiveX 控件"
  - "测试 [Visual Studio], 测试容器"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：调试 ActiveX 控件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中描述的不同，具体取决于您的现有设置或版本。  若要更改设置，请在“工具”菜单上选择“导入和导出设置”。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 若要调试 ActiveX 控件，必须指定一个容器（可执行文件）用于运行控件。  
  
### 为调试会话指定容器  
  
1.  在“解决方案资源管理器”中选择项目。  
  
2.  从**“视图”**菜单中，选定**“属性页”**。  
  
3.  在**“项目属性页”**对话框中，打开**“配置属性”**文件夹并选定**“调试”**。  
  
4.  在**“调试”**类别下，找到**“命令”**属性。  
  
5.  指定容器的路径名。  例如，C:\\Program Files\\Internet Explorer\\IEXPLORE.EXE。  
  
6.  如果指定 Internet Explorer 作为容器，并且正在使用 Active Desktop，在**“命令参数”**框中键入`/new` 。  
  
7.  单击**“确定”**。  
  
     如果在**“项目属性页”**对话框中没有指定容器，则在开始调试时可以指定容器。  当您选择执行命令开始调试时，将出现[“调试会话的可执行文件”对话框](../debugger/executable-for-debugging-session-dialog-box.md)。  在对话框中指定容器的路径名。  
  
## 请参阅  
 [ActiveX 控件](/visual-cpp/mfc/activex-controls)   
 [使用测试容器测试属性和事件](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [调试 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)   
 [使用 Visual Studio 进行调试](../debugger/debugging-in-visual-studio.md)