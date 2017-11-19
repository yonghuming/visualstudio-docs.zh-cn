---
title: "调试准备： Windows 窗体应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2d8f123359e4dfff02f05709d8028c2b9fcd3e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-preparation-windows-forms-applications"></a>调试准备：Windows 窗体应用程序
Windows 窗体项目模板创建 Windows 窗体应用程序。 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中调试此类应用程序非常简单。 有关详细信息，请参阅[创建 Windows 应用程序项目](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
 用项目模板创建 Windows 窗体项目时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将自动为调试和发布配置创建所需的设置。 必要时，可更改这些设置。 可以在更改这些设置**\<项目名称 > 属性页**对话框 (**我的项目**在 Visual Basic 中)。  
  
 有关详细信息，请参阅[建议的属性设置](../debugger/managed-debugging-recommended-property-settings.md)。  
  
 下表显示一个附加的建议属性设置。  
  
### <a name="configuration-properties-in-debug-tab"></a>“调试”选项卡中的“配置属性”  
  
|**属性名称**|**设置**|  
|-----------------------|-----------------|  
|**启动操作**|-将设置为**起始项目**大部分时间。 设置为**启动外部程序**如果你想要启动其他可执行文件启动时调试 （通常调试 Dll）。|  
  
 可以从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内部或者通过附加到已经运行的应用程序来调试 Windows 窗体应用程序。 有关附加的详细信息，请参阅[附加到运行进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>调试 C#、F# 或 Visual Basic Windows 窗体应用程序  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中打开项目。  
  
2.  根据需要创建断点。  
  
     由于 Windows 窗体应用程序是事件驱动的，您的断点将进入事件处理程序代码，或进入由事件处理程序代码调用的方法。 要在其中设置断点的典型事件包括：  
  
    1.  与控件关联的事件，如 Click、Enter 等  
  
    2.  与应用程序启动和关闭关联的事件，如 Load、Activated 等  
  
    3.  焦点和验证事件。  
  
     有关详细信息，请参阅[在 Windows 窗体中创建事件处理程序](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms)。  
  
3.  上**调试**菜单上，单击**启动**。  
  
4.  调试使用中讨论的技术[调试器基础知识](../debugger/debugger-basics.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) （调试托管代码）  
 [C#、F#、和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [如何： 设置调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)   
 [对于 C# 的项目设置调试配置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [调试配置适用于 Visual Basic 项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [将附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows 窗体](/dotnet/framework/winforms/index)