---
title: "如何：替换模板中的参数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "模板参数, 代替"
  - "Visual Studio 模板, 使用参数"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：替换模板中的参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建基于模板的文件时，可能会替换模板参数，比如类名称和命名空间。  有关模板参数的完整列表，请参阅[模板参数](../ide/template-parameters.md)。  
  
## 过程  
 每当创建基于模板的项目时，均可以替换模板的文件中的参数。  此过程说明使用模板创建新项目时，如何创建一个将命名空间名称替换为安全的项目名称的模板。  
  
#### 使用参数将命名空间名称替换为项目名称  
  
1.  将参数插入模板中的一个或多个代码文件中。  例如:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  模板参数是以 $*参数*$ 格式编写的。  
  
2.  在模板的 .vstemplate 文件中，找到包括此文件的 `ProjectItem` 元素。  
  
3.  将 `ProjectItem` 元素的 `ReplaceParameters` 特性设置为 `true`。  例如:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## 请参阅  
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [模板参数](../ide/template-parameters.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem 元素（Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)