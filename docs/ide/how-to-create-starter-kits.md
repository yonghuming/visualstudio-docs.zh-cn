---
title: "如何：创建初学者工具包 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "初学者工具包, 创建"
ms.assetid: ed7d1844-7c01-424a-a831-5003efe0f7bc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：创建初学者工具包
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

初学者工具包包含完整应用程序的代码以及有关如何修改或扩展该应用程序的文档。  创建初学者工具包基本上与创建普通项目模板相同，唯一的不同之处就是初学者工具包包含设置为在创建基于初学者工具包的项目时要打开的文档文件。  
  
## 设计和开发初学者工具包  
 首先，必须确定要开发的初学者工具包的类型并定义目标用户。  接下来，设计可实现目标的项目和文档。  
  
 如果您正在创建示例应用程序或插件：  
  
-   创建一个项目，保证在生成过程中不出错。  
  
-   添加模板代码，以实现附加任务（可选）。  
  
-   准备文档。  
  
 如果您正在创建学习工具：  
  
-   创建一个项目，保证在生成过程中不出错。  
  
-   组织资源，如代码段和项模板。  
  
-   准备文档。  
  
## 创建模板  
 完成项目和文档后，可以为初学者工具包创建项目模板。  此过程与创建项目模板完全相同。  
  
 下面的主题包含有关创建模板的信息。  
  
 [如何：创建项目模板](../ide/how-to-create-project-templates.md)  
 说明如何使用**“导出模板”**向导创建模板。  
  
 [如何：更新现有模板](../ide/how-to-update-existing-templates.md)  
 描述如何编辑已导出的模板。  使用此过程修改 .vstemplate 文件，进而对初学者工具包进行自定义。  
  
## 请参阅  
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [自定义模板](../ide/customizing-project-and-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)