---
title: "如何： 与 ClickOnce 应用程序一起安装系统必备组件 |Microsoft 文档"
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
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 44acef520a15b86e15906eb4197f538b23b92d8a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>如何：与 ClickOnce 应用程序一起安装系统必备组件
所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序需要，在能够运行之前在计算机上安装.NET Framework 的正确版本; 许多应用程序具有其他系统必备组件。 发布时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，你可以选择一组的必备组件与你的应用程序一起打包。 在安装时，将执行检查以确定它是否已存在; 每个系统必备组件如果在安装之前将不安装[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。  
  
 而不是打包和发布系统必备组件，你还可以指定组件的下载位置。 例如，而不是包含与每个发布的应用程序的先决条件，你可以使用集中的文件共享或包含所有系统必备组件的安装程序的 Web 位置-在安装时，组件将下载和安装从该位置。  
  
> [!IMPORTANT]
>  应将必备组件安装程序的包添加到你的开发计算机中，发布你的第一个之前[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 有关详细信息，请参阅[如何： 与 ClickOnce 应用程序包括先决条件](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)。  
  
 在中管理先决条件**先决条件**对话框中，可从访问**发布**窗格**项目设计器**。  
  
> [!NOTE]
>  除了预先确定的必备组件列表中，你可以将自己的组件添加到列表。 有关详细信息，请参阅[创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>若要指定要使用 ClickOnce 应用程序安装系统必备组件  
  
1.  在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2.  选择**发布**窗格。  
  
3.  单击**先决条件**按钮以打开**先决条件**对话框。  
  
4.  在 **“系统必备”** 对话框中，确保选中 **“创建用于安装系统必备组件的安装程序”** 复选框。  
  
5.  在**先决条件**列表中，选择的组件，你想要安装，，然后单击**确定**。  
  
     所选的组件将打包并随你的应用程序一起发布。  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>若要指定为系统必备组件提供不同的下载位置  
  
1.  在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2.  选择**发布**窗格。  
  
3.  单击**先决条件**按钮以打开**先决条件**对话框。  
  
4.  在 **“系统必备”** 对话框中，确保选中 **“创建用于安装系统必备组件的安装程序”** 复选框。  
  
5.  在**指定系统必备组件的安装位置**部分中，选择**从以下位置下载系统必备组件**。  
  
6.  从下拉列表中，选择一个位置或输入 URL、 文件路径或 FTP 位置，然后单击**确定。**  
  
    > [!NOTE]
    >  必须确保为指定组件的安装程序存在在指定的位置。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)