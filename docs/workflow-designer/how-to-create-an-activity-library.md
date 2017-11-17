---
title: "如何： 创建活动库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: "12"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a61c8f4ea5e9d9cc6d4ab13437d2ec4d4eef7ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-an-activity-library"></a>如何：创建活动库
自定义活动用于在工作流中对特定业务流程进行建模。 通过 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 中的活动库模板，可使用 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 直观地创建这种自定义活动。  
  
### <a name="to-create-a-workflow-activity-library"></a>创建工作流活动库  
  
1.  启动 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]。  
  
2.  上**文件**菜单上，指向**新建**，然后选择**项目...**.  
  
     **“新建项目”** 对话框随即打开。  
  
3.  在**项目类型**窗格中，选择**工作流**从**Visual C#**项目或**Visual Basic**分组，具体取决于你语言首选项。  
  
4.  在**模板**窗格中，选择**活动库**。  
  
5.  在**名称**框中，键入你的项目的描述性名称以便可以方便地标识。  
  
6.  在**位置**框中，键入想要保存你的项目，或单击的目录中**浏览**以导航到。  
  
7.  在**解决方案**框中，键入你的解决方案的描述性名称，然后单击**确定**。  
  
    > [!NOTE]
    >  如果你想要添加到现有的解决方案的工作流控制台应用程序，打开该解决方案中的[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]，右键单击该解决方案中的**解决方案资源管理器**，然后选择**添加**，然后**新建项目...**以打开**新项目**对话框。 按照此过程中的上述步骤继续操作。  
  
8.  该项目模板将创建一个 XAML 格式的活动定义。 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]将打开并显示自定义活动的画布。  
  
9. 将活动从**工具箱**到设计图面可将其包括在你自定义活动。  
  
    > [!CAUTION]
    >  自定义活动的主体中只能有一个子活动；但是，该子活动可以是一个复合活动，如 <xref:System.Activities.Statements.Sequence> 活动或 <xref:System.Activities.Statements.Flowchart> 活动。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建活动](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [创建工作流项目](../workflow-designer/creating-a-workflow-project.md)