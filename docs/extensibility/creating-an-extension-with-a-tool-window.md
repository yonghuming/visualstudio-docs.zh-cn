---
title: "使用一个工具窗口创建扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用一个工具窗口创建扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在此过程中，您将学习如何使用 VSIX 项目模板和 **自定义工具窗口** 项模板，从而创建一个与工具窗口的扩展。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### 创建工具窗口  
  
1.  创建一个名为的 VSIX 项目 **FirstWindow**。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\# \/ 可扩展性**。  
  
2.  当项目打开后时，添加一个名为的工具窗口项模板 **FirstWindow**。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **自定义工具窗口**。 在 **名称** 在窗口的底部字段中，工具窗口文件名称更改为 **FirstWindow.cs**。  
  
3.  生成项目并启动调试。  
  
     将显示 Visual Studio 的实验实例。 有关的实验实例的详细信息，请参阅 [实验实例](../extensibility/the-experimental-instance.md)。  
  
4.  在实验实例中，转到 **视图 \/ 其他窗口**。  
  
     您应该看到的菜单项 **FirstWindow**。 单击该按钮。  
  
     您应该看到一个工具窗口具有标题 **FirstWindow** 和按钮的一种说法 **Click Me\!。**