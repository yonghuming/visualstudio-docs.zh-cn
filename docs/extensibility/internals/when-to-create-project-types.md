---
title: "何时创建的项目类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目类型，用于创建条件"
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 何时创建的项目类型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

创建新的项目类型为自定义用户的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供基础。  但是，创建一个新的项目类型对于所有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自定义是必需的。  下列准则可帮助您确定新项目类型是否为该方案是必需的。  
  
## 创建新的项目类型  
 ，如果要自定义 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 到操作。以下一个或多个方法，您必须创建项类型:  
  
-   参与生成，部署，配置和数据源控件。  
  
-   提供调试支持。  
  
-   显示在 **解决方案资源管理器**的项目项。  
  
-   使用 **打开项目** 或 **新项目** 对话框。  
  
-   项目嵌套。  
  
## 扩展现有项类型  
 您可能希望创建可通过以下方式使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 修改或扩展现有项类型的行为，例如，修改生成过程 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目过程的新项目类型:  
  
-   与多个文件使用作为一个单元。  
  
-   显示单个文件作为子项层次结构。  
  
-   在编辑周围显示命令上下文。  
  
-   显示编辑器中的服务上下文。  
  
## 使用现有项类型  
 创建新项目有时不是必需的。  下表显示任务，您不必创建项目类型。  
  
|任务|说明|  
|--------|--------|  
|处理指令|所有 VSPackage 可以处理命令。|  
|生成编辑|自定义编辑器来注册。  有关更多信息，请参见 [Document Windows and Editors](http://msdn.microsoft.com/zh-cn/603625e1-62b6-413a-bc44-089346e166bc)。|  
|拥有窗口|可以创建工具窗口和文档窗口，而无需添加一个新的项目类型。|  
|显示 " 属性 " 窗口中的属性|所有对象都可以公开属性。|  
  
## 创建项目子类型  
 可以使用项目子类型扩展一个托管项目类型，而不必创建新的项目类型。  项目子类型使用 COM 摘要扩展 Microsoft 编写的托管项目 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]。  COM 摘要，您可以重用多个托管项目系统实现和用于特定方案仍自定义通过摘要和使用支持接口。  有关项目子类型的更多信息，请参见 [项目子类型](../../extensibility/internals/project-subtypes.md)。  
  
## 请参阅  
 [Document Windows and Editors](http://msdn.microsoft.com/zh-cn/603625e1-62b6-413a-bc44-089346e166bc)   
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [在 Visual Studio 中的层次结构](../../extensibility/internals/hierarchies-in-visual-studio.md)