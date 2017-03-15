---
title: "如何：在工作流设计器中给工作流添加备注 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.Annotations.Annotation.UI"
  - "Annotation"
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
caps.handback.revision: 5
ms.author: "sdanie"
manager: "erikre"
---
# 如何：在工作流设计器中给工作流添加备注
为方便创建更大、更复杂的工作流，[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 使开发人员可以将批注添加到以下类型的设计器中的项：  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   从 <xref:System.Activities.Statements.FlowNode> 中派生的类。  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  注释的内容保存到 XAML 文件纯文本关联的工作流，并有可能被其他人读取。敏感信息输入注释时要谨慎。  
  
### 将注释添加到设计器中的一个活动  
  
1.  在工作流设计器中，右键单击项中工作流设计器并选择**批注**、**添加注释**。  
  
2.  在提供的空白处添加注释的文本。  
  
3.  该项将显示注释图标。将鼠标悬停在注释图标将显示注释的文本。  
  
     ![显示注释的序列活动](../debugger/debug-interface-access/annotation.md "Annotation")  
  
### 活动设计器中显示的批注  
  
1.  使用活动设计器具有外活动显示注释，请单击 **Pin** 注释装饰器中的图标。  
  
2.  注释将显示在活动设计器中。在下面的屏幕快照中，活动设计器中显示注释“工作流中的开始活动”。  
  
     ![活动设计器中显示的注释](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  显示外活动设计器的注释，将鼠标悬停在活动设计器中的注释区域，单击 **脱离** 图标  
  
     ![活动设计器外显示的注释](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### 显示或隐藏所有批注  
  
1.  右键单击一个有注释的活动。选择 **批注**、**显示所有批注**。  
  
2.  所有注释将显示在活动设计器中。  
  
3.  要显示活动设计器之外的所有批注，请右键单击活动，然后选择 **批注**、**隐藏所有批注**。  
  
### 编辑或删除注释为活动  
  
1.  右键单击一个有注释的活动。  
  
2.  选择**批注**、**编辑批注** 或 **删除批注**。  
  
3.  将打开进行编辑或删除注释。  
  
4.  要同时删除所有注释，请右键单击工作流设计器并选择 **注释**、**都删除所有批注**。  
  
### 添加、编辑和删除注释的变量或自变量  
  
1.  变量或自变量上右键单击并选择添加注释。  
  
2.  在注释中输入文本。变量或自变量将显示注释图标。  
  
3.  右键单击具有注释的变量或自变量。选择编辑批注。  
  
4.  将打开进行编辑注释。  
  
5.  右键单击具有注释的变量或自变量。选择删除注释。  
  
6.  将删除该注释。