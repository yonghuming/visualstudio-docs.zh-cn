---
title: "嵌套项目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目的嵌套"
  - "嵌套的项目"
  - "项目 [Visual Studio SDK]，子项目"
  - "项目 [Visual Studio SDK] 嵌套"
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 嵌套项目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

企业应用程序开发人员使用 VS 软件包可以方便地进行分组相似类型的项目组织在一起， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 *项目嵌套*。 例如，企业级模板项目使用嵌套的项目到项目进行分组为类别。 商业外观项目、 Web UI 项目，依次类推组合在一起在一个类别。  
  
 在此方案中，是为开发人员可以嵌套在每个父项目，下面的项目数没有限制过程，尽管开发人员可以以编程方式提供限制。 这种类型的分组还可以进行递归的在这种情况下与子项目具有相同类型的项目可以嵌套在子变得子级，这是父级的子项目的子项目。  
  
 项目嵌套不是内部函数的一部分 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您必须编写代码以启用嵌套和子项目的子项目中的嵌套。 父项目是一个特殊的 VSPackage 或项目类型，创建并注册其自己的 GUID，其中包含实现项目嵌套所需的代码。  
  
 C\# Example.Nested 项目示例中，您可以找到嵌套项目的示例。  
  
## 嵌套的项目的示例  
 ![嵌套项目解决方案](~/docs/extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
嵌套的项目的示例  
  
## 请参阅  
 [如何: 实现嵌套的项目](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [有关卸载和重新加载嵌套项目的注意事项](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [嵌套项目的向导支持](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [实现处理嵌套项目命令](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [对嵌套项目的筛选 AddItem 对话框](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [上下文参数](../../extensibility/internals/context-parameters.md)   
 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)