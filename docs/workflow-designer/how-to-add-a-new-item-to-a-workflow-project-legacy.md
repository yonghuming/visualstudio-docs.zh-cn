---
title: "如何：向工作流项目添加新项（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "活动, 添加到工作流项目"
  - "顺序工作流, 添加到工作流项目"
  - "状态机工作流, 添加到工作流项目"
  - "工作流, 添加新项"
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：向工作流项目添加新项（旧版）
在使用 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 提供的、面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 创建工作流项目之后，可向该项目添加 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 项和其他熟悉的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项。  
  
 下表列出了可添加到工作流项目中的 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 项。  
  
|项|说明|  
|-------|--------|  
|活动|活动定义在设计器代码文件中而用户代码在另一个代码文件中的活动。|  
|Activity \(具有单独的代码\)|位于不同代码文件中的活动定义（以工作流标记形式表示）和用户代码。|  
|顺序工作流 \(代码\)|工作流定义在设计器代码文件中而用户代码在另一个代码文件中的顺序工作流。|  
|顺序工作流 \(具有单独的代码\)|工作流定义（以工作流标记形式表示）与用户代码位于不同代码文件中的顺序工作流。|  
|状态机工作流 \(代码\)|工作流定义在设计器代码文件中而用户代码在另一个代码文件中的状态机工作流。|  
|状态机工作流 \(具有单独的代码\)|工作流定义（以工作流标记形式表示）与用户代码位于不同代码文件中的状态机工作流。|  
  
### 向工作流项目添加新项  
  
1.  在**“项目”**菜单上单击**“添加新项”**。  
  
     此时将打开**“添加新项”**对话框。  
  
2.  选择一个项。  
  
     前面的表列出了可用的 Windows Workflow Foundation 选择。  
  
3.  单击**“添加”**将该项添加到工作流项目中。  
  
## 请参阅  
 [创建旧版工作流项目](../workflow-designer/creating-legacy-workflow-projects.md)