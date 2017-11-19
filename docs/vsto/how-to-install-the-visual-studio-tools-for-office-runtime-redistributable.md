---
title: "如何： 安装 Visual Studio Tools for Office Runtime 可再发行组件 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: "94"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8d3439a98a445761a8d357d9b4bef631da034943
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>如何：安装 Visual Studio Tools for Office Runtime 可再发行组件
  必须在运行使用 Microsoft Office 开发人员工具中的创建的解决方案，每台计算机上安装 Visual Studio 2010 Tools for Office Runtime [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 安装 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 Microsoft Office 时会自动安装运行时。 有关详细信息，请参阅 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)。  
  
 在以下情况，你可能需要按照手动安装说明操作：  
  
-   需要在服务器上安装 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 例如，希望使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类来管理服务器上的文档级解决方案。  
  
-   需要在已安装 Office 解决方案的所有其他先决条件的计算机上安装运行时。  
  
    > [!NOTE]  
    >  若要安装 .NET Framework 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，你必须是开发计算机上的管理员。  
  
### <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>安装 Visual Studio Tools for Office runtime  
  
1.  安装 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本。  
  
    -   若要下载[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]，请参阅[Microsoft.NET Framework 4 (Web Installer)](http://go.microsoft.com/fwlink/?LinkId=178957)。  
  
    -   若要下载[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]，请参阅[Microsoft.NET Framework 4 Client Profile (Web Installer)](http://go.microsoft.com/fwlink/?LinkId=178958)。  
  
    -   若要下载[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，请参阅[Microsoft.NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)。  
  
2.  运行 vstor_redist.exe 以安装 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
     你可以下载这些安装程序文件从[Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384)。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的先决条件与 .NET Framework 的先决条件相匹配。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]包括的语言包。 如果 Windows 安装设置为非英语语言，则可以以 Windows 使用的语言显示运行时消息。 同样，如果最终用户安装 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，然后在设置为非英语语言的 Windows 安装上运行你的解决方案，则运行时消息将以与 Windows 相同的语言显示。 在某些情况下，可能需要其他语言包。 例如，你可能需要其他语言包，如果你的 Windows 副本使用多个语言设置，或者你已安装后切换到另一种语言[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 你可以找到语言包[Microsoft Visual Studio 2010 Tools，Microsoft Office System （版本 4.0 运行时） 语言包](http://go.microsoft.com/fwlink/?LinkId=140386)。  
  
## <a name="see-also"></a>另请参阅  
 [入门 &#40; Visual Studio &#41; 中的 Office 开发](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [如何： 配置计算机以开发 Office 解决方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [如何： 安装 Office 主互操作程序集](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  