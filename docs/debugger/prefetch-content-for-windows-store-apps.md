---
title: "调试在 UWP 应用中使用预提取的内容 |Microsoft 文档"
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d85c76ce48ca2e04e7ce40b9e40075c8ba539e6
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>调试使用 Visual Studio 中的预提取的内容的 UWP 应用
![仅适用于 Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 若要使 UWP 应用能够更快地响应，你可以请求 Windows 将一些 web 内容，例如网页或 web 图像，预加载到应用的[WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)缓存。 此功能称为“预提取”。 它对于启动时使用的内容特别有效，但也预提取其他常用的内容。 方法[Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx)类，你可以指定要预加载内容的 Uri。 请参阅 Windows SDK[内容预提取示例](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)有关如何将 ContentPrefetcher 功能添加到你的应用程序的示例。  
  
 Windows 使用试探法来确定何时及是否应进行预提取，以及将下载哪些资源。 试探法将考虑系统网络和电源情况、用户应用使用情况历史记录和之前预提取尝试的结果。 在 Visual Studio 中，你可以使用**触发 Windows 应用商店应用预提取**命令来强制 Windows 忽略 ContentPrefetcher 试探法并预加载所有指定的 web 内容。 若要在已知状态（已加载或未加载）下使用要预提取的内容测试应用程序的行为或性能，这会很有用。  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>强制预加载 ContentPrefetcher 指定的资源  
 此过程假定你已在应用程序项目中设置 ContentPrefetcher 功能并指定预加载的内容 URI。 若要强制预加载内容时指定的资源为新的或已修改，你必须启动和停止应用程序，在选择之前**触发 Windows 应用商店应用预提取**命令。 先运行应用程序以注册 URI。 **触发 Windows 应用商店应用预提取**命令将强制 ContentPrefetcher 下载此内容并将它添加到缓存。 在应用程序的后续运行中，你可以假定已预加载此内容。  
  
1.  启动应用程序以将预提取内容 URI 注册到应用程序。 上**调试**菜单上，选择**启动调试**(键盘快捷键： F5)。  
  
2.  上**调试**菜单上，选择**停止调试**(键盘快捷键： Shift + F5)。  
  
3.  上**调试**菜单上，选择**其他调试目标**，然后选择**触发 Windows 应用商店应用预提取**。  
  
 现在可以利用预提取的 Web 资源来调试、测试或分析应用程序。  
  
> [!NOTE]
>  当你添加或修改指定的 Web 内容时，请重复上述步骤。  
  
## <a name="see-also"></a>另请参阅  
 [博客文章： 触发预提取为 Windows 应用商店应用在 Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)