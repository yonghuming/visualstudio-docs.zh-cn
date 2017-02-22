---
title: "预提取 Windows 应用商店应用的内容 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 预提取 Windows 应用商店应用的内容
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要使 Windows 应用商店应用能够更快地响应，你可以请求 Windows 将一些 Web 内容（如网页或 Web 图像）预加载到应用的 [WinINet](http://msdn.microsoft.com/zh-cn/0a06f2af-957a-4dff-a8cc-187370181b5c) [WinINet](http://msdn.microsoft.com/library/aa383630.aspx)缓存中。此功能称为“预提取”。它对于启动时使用的内容特别有效，但你也可以预提取其他常用内容。利用 [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) 类的方法，可以指定要预加载的内容的 URI。有关如何将 ContentPrefetcher 功能添加到应用的示例，请参阅 Windows SDK [内容预提取示例](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)。  
  
 Windows 使用试探法来确定何时及是否应进行预提取，以及将下载哪些资源。试探法将考虑系统网络和电源情况、用户应用使用情况历史记录和之前预提取尝试的结果。在 Visual Studio 中，可以使用**“触发 Windows 应用商店应用预提取”**命令来强制 Windows 忽略 ContentPrefetcher 试探法并预加载所有指定的 Web 内容。若要在已知状态（已加载或未加载）下使用要预提取的内容测试应用的行为或性能，这会很有用。  
  
## 强制预加载 ContentPrefetcher 指定的资源  
 此过程假定你已在应用项目中设置 ContentPrefetcher 功能并指定预加载的内容 URI。若要在指定资源为新的或已修改的资源时强制预加载内容，你必须在选择**“触发 Windows 应用商店应用预提取”**命令之前启动和停止此应用程序。先运行应用程序以注册 URI。然后，**“触发 Windows 应用商店应用预提取”**命令将强制 ContentPrefetcher 下载此内容并将其添加到缓存。在应用的后续运行中，你可以假定已预加载此内容。  
  
1.  启动应用以将预提取内容 URI 注册到应用。在**“调试”**菜单上，选择**“启动调试”**（键盘快捷键：F5）。  
  
2.  在**“调试”**菜单上，选择**“停止调试”**（键盘快捷键：Shift \+ F5）。  
  
3.  在**“调试”**菜单上，选择**“其他调试目标”**，然后选择**“触发 Windows 应用商店应用预提取”**。  
  
 现在可以利用预提取的 Web 资源来调试、测试或分析应用。  
  
> [!NOTE]
>  当你添加或修改指定的 Web 内容时，请重复上述步骤。  
  
## 请参阅  
 [博客文章：在 Visual Studio 2013 Update 2 中触发 Windows 应用商店应用的预提取](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)