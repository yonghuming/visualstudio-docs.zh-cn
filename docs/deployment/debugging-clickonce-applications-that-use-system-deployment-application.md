---
title: "调试使用 System.Deployment.Application 的 ClickOnce 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 19fa51106512394175159c7dd656badaf583dd3c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>调试使用 System.Deployment.Application 的 ClickOnce 应用程序
在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可让你配置如何更新应用程序。 但是，如果你需要使用和自定义高级[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署功能，你将需要访问由提供的部署对象模型<xref:System.Deployment.Application>。 你可以使用<xref:System.Deployment.Application>Api，可用于高级任务，如：  
  
-   在你的应用程序中创建一个"立即更新"选项  
  
-   条件，按需下载的各种应用程序组件  
  
-   直接集成到应用程序的更新  
  
-   保证客户端应用程序始终最新  
  
 因为<xref:System.Deployment.Application>Api 工作仅的应用程序部署与[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]技术，对其进行调试的唯一方法是部署应用程序使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，将附加到它，然后对其进行调试。 它可能很难将调试器附加早期足够，因为此代码通常运行时应用程序启动并执行之前可以附加调试器。 一种解决方案是在更新检查代码或按需代码之前将中断 （或停止，对于 Visual Basic 项目）。  
  
 建议的调试方法是，如下所示：  
  
1.  在开始之前，请确保存档的符号 (.pdb) 和源文件。  
  
2.  部署应用程序的版本 1。  
  
3.  创建一个新的空白解决方案。 从**文件**菜单上，单击**新建**，然后**项目**。 在**新项目**对话框中，打开**其他项目类型**节点，然后选择**Visual Studio 解决方案**文件夹。 在**模板**窗格中，选择**空白解决方案**。  
  
4.  将存档的源位置添加到此新的解决方案的属性。 在**解决方案资源管理器**，右键单击解决方案节点，然后单击**属性**。 在**属性页**对话框中，选择**调试源文件**，然后添加已存档的源代码的目录。 否则，调试器将发现过期的源文件，因为源文件的路径会记录在.pdb 文件。 如果调试器使用过期的源文件，你将看到一消息，告知你源不匹配。  
  
5.  请确保调试器可以找到.pdb 文件。 如果你具有使用你的应用程序部署它们，调试器会自动找到它们。 它始终首先旁边程序集问题。 否则，你将需要添加的存档路径**符号文件 (.pdb) 位置**(若要访问此选项，从**工具**菜单上，单击**选项**，然后打开**调试**节点，然后单击**符号**)。  
  
6.  调试之间会发生什么情况`CheckForUpdate`和`Download` / `Update`方法调用。  
  
     例如，更新代码可能如下所示：  
  
    ```  
        Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
            If My.Application.Deployment.IsNetworkDeployed Then  
  
                If (My.Application.Deployment.CheckForUpdate()) Then  
  
                    My.Application.Deployment.Update()  
                    Application.Restart()  
  
                End If  
  
            End If  
        End Sub  
    ```  
  
7.  部署版本 2。  
  
8.  尝试将调试器附加到版本 1 应用程序，下载版本 2 的更新。 或者可以使用`System.Diagnostics.Debugger.Break`方法或只需`Stop`在 Visual Basic 中。 当然，你不应在生产代码中将这些方法调用。  
  
     例如，假定你在开发 Windows 窗体应用程序，并且中必须具有的事件处理程序更新逻辑与此方法。 若要调试它，只需将附加之前按下按钮然后将其设置断点 （请确保你打开相应的存档的文件和设置断点）。  
  
 使用<xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A>属性来调用<xref:System.Deployment.Application>Api 仅在部署应用程序时; Api 不应该调用在调试期间[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Deployment.Application>