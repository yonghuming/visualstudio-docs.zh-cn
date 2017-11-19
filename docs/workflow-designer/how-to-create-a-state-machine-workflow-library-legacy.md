---
title: "如何： 创建状态机工作流库 （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 47092f4f541f4f6e797617db3cf2d9c24741d282
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>如何：创建一个状态机工作流库（旧版）
按照这些步骤可使用 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供的旧 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 来创建状态机工作流库项目。 在需要面向 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>创建一个状态机工作流库项目  
  
1.  启动 Visual Studio。  
  
2.  上**文件**菜单上，指向**新建**，然后选择**项目**。  
  
     **“新建项目”** 对话框随即打开。  
  
3.  选择**.NET Framework 3.0**选项或**.NET Framework 3.5**的下拉列表的顶部列表中的选项**新项目**窗口，以访问旧设计器。  
  
    > [!NOTE]
    >  中的默认选项[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]是**.NET Framework 4**。 此选项用于创建面向 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 应用程序，并且不使用旧设计器。  
  
4.  在**项目类型**窗格中，选择 Visual C# 或 Visual Basic (下**其他语言**)，然后选择**工作流**。  
  
5.  在**模板**窗格中，选择**状态机工作流库**。  
  
6.  在**名称**框中，输入你的项目，以便可以方便地标识的描述性名称。  
  
7.  在**位置**框中，输入你要在其中保存你的项目，或单击的目录**浏览**以导航到。  
  
     如果要为项目创建解决方案目录，请选择**创建解决方案的目录**复选框，输入中的名称**解决方案名称**框。  
  
8.  单击“确定”。  
  
## <a name="see-also"></a>另请参阅  
 [创建旧版工作流项目](../workflow-designer/creating-legacy-workflow-projects.md)   
 [状态机工作流](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)