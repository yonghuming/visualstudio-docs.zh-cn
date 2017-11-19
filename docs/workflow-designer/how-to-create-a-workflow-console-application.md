---
title: "如何： 创建工作流控制台应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4b019c2733a8e411b1d3e5be15af3b272708ce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-workflow-console-application"></a>如何：创建工作流控制台应用程序
使用 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 可为执行系统或人工流程创建工作流。 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供用于创建这些工作流的设计图面。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 可用于在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内创建工作流，也可集成到重新承载该设计器的其他应用程序。  
  
 本主题介绍如何使用 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 在控制台应用程序中创建工作流。  
  
### <a name="to-create-a-workflow-console-application"></a>创建工作流控制台应用程序  
  
1.  启动 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]。  
  
2.  上**文件**菜单上，指向**新建**，然后选择**项目...**.  
  
     **“新建项目”** 对话框随即打开。  
  
3.  在**已安装的模板**窗格中，选择**工作流**从**Visual C#**或**Visual Basic**分组，具体取决于你语言首选项。  
  
4.  在中间窗格中，选择**工作流控制台应用程序**。  
  
5.  在**名称**框中，输入你的项目，以便可以方便地标识的描述性名称。  
  
6.  在**位置**框中，输入你要在其中保存你的项目，或单击的目录**浏览**以导航到。  
  
7.  在**解决方案**框中，输入新的解决方案的名称。 单击**确定**创建应用程序。  
  
    > [!NOTE]
    >  如果你想要添加到现有的解决方案的工作流控制台应用程序，打开该解决方案中的[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]，右键单击该解决方案中的**解决方案资源管理器**，然后选择**添加**，然后**新建项目...**以打开**新项目**对话框。 按照此过程中的上述步骤继续操作。  
  
8.  该项目模板将在 XAML 中创建一个工作流定义并在源代码中创建控制台应用程序定义。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 将打开并显示所创建工作流的画布。  
  
9. 若要编写工作流，将活动或其他工作流项从**工具箱**到你的工作流中的设计图面。  
  
## <a name="see-also"></a>另请参阅  
 [创建工作流项目](../workflow-designer/creating-a-workflow-project.md)