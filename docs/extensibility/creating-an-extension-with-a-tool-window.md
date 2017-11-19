---
title: "使用工具窗口创建扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cda2d9bc4bde1c0bf9d9dd82c48864725f0e25f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-tool-window"></a>使用工具窗口创建扩展
在此过程中，你将学习如何使用 VSIX 项目模板和**自定义工具窗口**项模板，从而创建一个与工具窗口的扩展。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="creating-a-tool-window"></a>创建工具窗口  
  
1.  创建一个名为的 VSIX 项目**FirstWindow**。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  在项目打开，添加名为的工具窗口项模板**MyWindow**。 在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**自定义工具窗口**。 在**名称**在窗口底部字段中，工具窗口文件名称更改为**MyWindow.cs**。  
  
3.  生成项目并启动调试。  
  
     将显示 Visual Studio 的实验实例。 实验实例有关的详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
4.  在实验实例中，转到**视图 / 其他窗口**。  
  
     你应看到的菜单项**MyWindow**。 单击此链接。  
  
     你应看到工具窗口标题**MyWindow**和按钮说**Click Me ！。**