---
title: "如何： 创建顺序工作流控制台应用程序 （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e9732334f422b4042f2cd581afaea06bf99ab16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>如何：创建顺序工作流控制台应用程序（旧版）
按照这些步骤可使用 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供的旧 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 来创建顺序工作流控制台应用程序项目。 在需要面向 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>创建顺序工作流控制台应用程序  
  
1.  启动 Visual Studio。  
  
2.  上**文件**菜单上，指向**新建**，然后选择**项目**。  
  
     **“新建项目”** 对话框随即打开。  
  
3.  选择**.NET Framework 3.0**选项或**.NET Framework 3.5**的下拉列表的顶部列表中的选项**新项目**窗口，以访问旧设计器。  
  
    > [!NOTE]
    >  中的默认选项[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]是**.NET Framework 4**。 此选项用于创建面向 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 应用程序，并且不使用旧设计器。  
  
4.  在**项目类型**窗格中，选择 Visual C# 项目或 Visual Basic 项目 (下**其他语言**)，然后选择**工作流**。  
  
5.  在**模板**窗格中，选择**顺序工作流控制台应用程序**。  
  
6.  在**名称**框中，输入你的项目，以便可以方便地标识的描述性名称。  
  
7.  在**位置**框中，输入你要在其中保存你的项目，或单击的目录**浏览**以导航到。  
  
     Windows 窗体设计器将会打开并显示所创建项目的 Form1。  
  
8.  单击“确定”。  
  
     工作流设计器将会打开并显示所创建的顺序工作流的工作流设计图面。  
  
9. 将活动从**工具箱**到中的设计图面**放置活动**指定区域。  
  
## <a name="see-also"></a>另请参阅  
 [创建旧版工作流项目](../workflow-designer/creating-legacy-workflow-projects.md)   
 [开发工作流](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)