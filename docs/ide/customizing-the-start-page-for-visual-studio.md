---
title: "自定义 Visual Studio 的起始页 | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 178c20c9c4c3af8f5252e70ca603cdf8f8335e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>自定义 Visual Studio 的起始页
可以通过多种默认方式来自定义 Visual Studio 的起始页，例如，显示“打开项目”对话框或打开最近加载的解决方案。 你也可以显示自定义起始页，此起始页是在工具窗口中运行的 Windows Presentation Foundation (WPF) XAML 页，并且可以运行 Visual Studio 的内部命令。  

## <a name="customize-the-default-start-page"></a>自定义默认起始页  

1.  在菜单栏上，依次选择“工具” 、“选项” 。  

2.  展开“环境”，然后选择“启动”。  

3.  在“启动时”列表中，选择所需的自定义项。  

## <a name="show-a-custom-start-page"></a>显示自定义起始页  

1.  通过以下方式之一安装自定义起始页：  

    -   从 [Visual Studio 库](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page)、其他网站或本地 Intranet 中的页上安装起始页。  

        打开包含自定义起始页的 .vsix 文件，或复制起始页文件并将其粘贴到计算机上的 **%USERPROFILE% \My Documents\Visual Studio 2017\StartPages** 文件夹。  

    -   如果你已安装 Visual Studio SDK，请创建你自己的起始页。  

         请参阅[创建自定义起始页](../extensibility/creating-a-custom-start-page.md)。  

2.  在菜单栏上，依次选择“工具” 、“选项” 。  

3.  展开“环境”，然后选择“启动”。  

4.  在“自定义起始页”列表中，选择所需的页。  

> [!NOTE]
>  如果自定义起始页中的错误导致 Visual Studio 崩溃，则可以使用安全模式下启动 Visual Studio，然后将其设置为使用默认起始页。 请参阅 [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)。  

## <a name="see-also"></a>请参阅  
 [个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)   
