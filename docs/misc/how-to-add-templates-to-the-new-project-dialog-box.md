---
title: "如何：将模板添加到“新建项目”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "对话框, 将模板添加到项目"
  - "项目 [Visual Studio SDK], 将模板添加到对话框"
  - "模板 [Visual Studio], 添加到项目对话框"
ms.assetid: fd044681-e666-410d-815c-33db923ed888
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# 如何：将模板添加到“新建项目”对话框
安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 时会安装一系列预定义的项目模板。 关于预定义项目模板的完整列表，请参阅 [NIB 从模板创建项目](http://msdn.microsoft.com/zh-cn/7c36d86a-6b79-4480-8228-0f925f1204b2)。 除了默认的项目模板外，你还可以创建自定义或子类型特定的项目模板。 例如，“智能设备”子类型为 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 项目提供了其自己的模板。 有关如何创建自定义模板的说明，请参阅[如何：创建项目模板](../ide/how-to-create-project-templates.md)。  
  
## 将模板添加到“新建项目”对话框  
  
#### 要将模板添加到“新建项目”对话框  
  
1.  创建一个模板，其中包括 MyTemplate.vstemplate 文件。  
  
2.  选择模板（包括 .vstemplate 文件）中的文件，右键单击所选文件，单击“发送至”，然后单击“压缩的文件夹\(zip 格式\)”。 之前提取的文件被压缩为一个 .zip 文件。  
  
 将 .zip 模板文件放入 **%USERPROFILE%\\Documents\\Visual Studio 2015\\Templates\\ProjectTemplates**。  
  
## 请参阅  
 [Project Subtypes](d235b47b-cf11-4d47-a63f-e33d9d16105d2044a030-0795-4940-bd65-a6e44de98a0f)   
 [NIB：Visual Studio 模板](http://msdn.microsoft.com/zh-cn/141fccaa-d68f-4155-822b-27f35dd94041)   
 [导致添加新项对话框](../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)