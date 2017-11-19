---
title: "刷新 UWP 或 Windows 8.1 应用程序 |Microsoft 文档"
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
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5f5592893452c3fdf7f535758f09d7877030c03
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="refresh-a-uwp-or-windows-81-app"></a>刷新 UWP 或 Windows 8.1 应用
![适用于 Windows 和 Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 你进行调试，然后刷新通过选择使用 JavaScript UWP 应用时，可以对你的代码进行更改**刷新 Windows 应用程序**按钮上**调试**工具栏。 选择此按钮将重新加载应用程序，但不会停止并重新启动调试器。 通过“刷新”功能，可修改 HTML、CSS 和 JavaScript 代码并迅速看到结果。 对于 UWP 和 Windows 8.1 应用程序支持此功能。  
  
 刷新功能不保持应用程序状态，也不反映对应用程序的以下更改：  
  
-   程序包清单文件更改，其中包括对程序包清单中指定图像的更改。  
  
-   引用更改（如添加或移除 SDK 引用）或 Windows 运行时组件（.winmd 文件）更改。  
  
-   资源更改，如对 .resjson 文件中字符串的更改。  
  
-   导致路径名更改、新建项目文件或删除文件的项目文件更改。  
  
-   项目和项属性更改（如对所选调试设备的更改）或对文件的程序包操作的更改（在“属性”窗口中）。  
  
> [!IMPORTANT]
>  在更改引用或包清单或者进行上面的列表中指定的其他更改时，必须停止并重新启动调试器以更新 HTML、CSS 和 JavaScript 源文件。  
  
### <a name="to-refresh-an-app"></a>刷新应用程序  
  
1.  在 Visual Studio 中，使用“导航应用”项目模板创建一个新项目。  
  
     这可以是 UWP 应用或 Windows 8.1 应用程序。  
  
2.  在 Visual Studio 中打开模板后，选择一个调试目标。  
  
     如果 Windows Phone 项目是你的当前启动项目，请将 Windows Phone 仿真程序选为调试目标。 否则，请选择**模拟器**或**本地计算机**。  
  
     ![选择调试目标列表](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  按 F5 以在调试模式下运行应用程序。  
  
4.  切换到 Visual Studio。 （按 F12。）  
  
5.  在**解决方案资源管理器**中**页** > **主**文件夹中，打开 home.html。  
  
6.  将页标题文本从  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     改为类似如下所示的内容：  
  
    ```html  
    Hello!  
    ```  
  
7.  单击**刷新 Windows 应用程序**按钮，如下所示像这样：![刷新 Windows 应用程序按钮](../debugger/media/js_refresh.png "JS_Refresh")。 （或按 F4。）  
  
8.  切换到该应用程序。 将重新加载该应用程序，但不重新启动调试器，并显示新的页面标题。  
  
## <a name="see-also"></a>另请参阅  
 [快速入门：调试 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)