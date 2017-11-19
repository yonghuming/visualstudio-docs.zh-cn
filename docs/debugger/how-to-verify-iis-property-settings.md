---
title: "如何： 验证 IIS 属性设置 |Microsoft 文档"
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
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0d58ea851423e9239d8685f89890b5d9e152d53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-verify-iis-property-settings"></a>如何：验证 IIS 属性设置
使用 IIS 管理工具，可以设置 Web 应用程序的属性。 这些属性必须正确设置，应用程序才能运行，所以，验证这些设置通常是疑难解答的必需步骤。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>检查 Web 应用程序的 IIS 设置  
  
1.  打开**管理工具**窗口： 在**启动**菜单上，指向**程序**，然后单击**管理工具**。 如果**管理工具**未出现在**程序**菜单，然后查找它在**控制面板**。  
  
    -   在 Windows 2000 中，选择**Internet 服务管理器**。  
  
    -   在 Windows XP 中，选择**Internet Information Services**。  
  
    -   在 Windows Server 2003，双击**管理您的服务器**。  
  
         **管理您的服务器**窗口随即打开。 下**应用程序服务器**，单击**管理此应用程序服务器**。  
  
         **应用程序服务器**窗口随即打开。 打开**Internet Information Services (IIS) Manager**的左窗格中的节点。  
  
2.  在该对话框中，单击表示你的计算机的树控件节点。 单击**网站**节点，并选择 Web 应用程序的节点。 它将为网站节点中，因而的同级**Default Web Site**节点或现有的网站节点下的虚拟目录节点。  
  
3.  右键单击 Web 应用程序，然后在快捷菜单上，单击**属性**。  
  
4.  验证该 Web 应用程序的安全设置。  
  
    1.  Web 应用程序中**属性**窗口中，单击**目录安全性**卡，然后单击**编辑**。  
  
    2.  在**身份验证方法**对话框中，选择**启用匿名访问**和**集成 Windows 身份验证**如果尚未选择。  
  
    3.  单击**确定**关闭**身份验证方法**对话框。  
  
5.  对于 ATL Server 应用程序，请验证 DEBUG 谓词是否与您的 ISAPI 扩展相关联。 有关详细信息，请参阅[如何： 将相关联调试谓词进行的扩展](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e)。  
  
6.  有关[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]应用程序，确保该应用程序设置的应用程序名称的虚拟文件夹**Internet Information Services (IIS) Manager**， **Internet 服务管理器**或**Internet Information Services**。  
  
    1.  Web 应用程序中**属性**窗口中，选择**目录**选项卡上，如果应用程序在虚拟目录中，或**主目录**选项卡上，如果应用程序中网站。  
  
    2.  验证中的名称**本地路径**与实际部署应用程序的位置的目录的名称匹配。  
  
    3.  下**应用程序设置**，键入包含的应用程序的根目录的名称。  
  
    4.  单击**确定**关闭**属性**对话框。  
  
7.  有关[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]应用程序中，单击**ASP.NET**选项卡上，并验证的正确版本[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]指定。  
  
8.  单击**确定**关闭**属性**对话框。  
  
9. 单击**确定**关闭**Internet Information Services (IIS) Manager**， **Internet 服务管理器**，或**Internet Information Services**对话框。  
  
## <a name="see-also"></a>另请参阅  
 [疑难解答](../debugger/debugging-web-applications-troubleshooting.md)