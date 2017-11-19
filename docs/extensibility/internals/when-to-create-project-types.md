---
title: "何时创建项目类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b532ad4e72fb15cd9409c362259347f6f3833d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="when-to-create-project-types"></a>何时创建项目类型
创建新的项目类型提供了用于自定义的基础[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]为你的用户。 但是，创建新的项目类型不需要所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自定义项。 以下准则可帮助您确定是否为你的方案需要新的项目类型。  
  
## <a name="create-a-new-project-type"></a>创建新的项目类型  
 如果你想要自定义，则必须创建一种项目类型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以充当一个或多个通过以下方式：  
  
-   参与生成、 配置和源代码管理部署。  
  
-   提供调试支持。  
  
-   显示中的项目项**解决方案资源管理器**。  
  
-   使用**打开项目**或**新项目**对话框。  
  
-   支持项目嵌套。  
  
## <a name="extend-an-existing-project-type"></a>扩展现有项目类型  
 你可能想要创建新的项目类型，可以使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通过以下方式修改或扩展现有的项目类型的行为，例如，修改的生成过程[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]项目：  
  
-   作为单个单元使用多个文件。  
  
-   作为子项目的层次结构中显示单个文件。  
  
-   显示围绕编辑器命令上下文。  
  
-   为编辑器中显示的服务上下文。  
  
## <a name="use-an-existing-project-type"></a>使用现有的项目类型  
 创建新的项目不有时需要。 下表显示不需要创建的项目类型的任务。  
  
|任务|描述|  
|----------|-----------------|  
|处理命令|任何 VSPackage 可以处理命令。|  
|生成编辑器|可以注册自定义编辑器。 有关详细信息，请参阅[文档窗口和编辑器](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)。|  
|拥有 windows|你可以创建工具和文档窗口而不添加新项目类型。|  
|在属性窗口中公开属性|所有对象都可以都公开属性。|  
  
## <a name="create-a-project-subtype"></a>创建项目子类型  
 你可以使用项目子类型而无需创建新的项目类型扩展的托管的项目类型。 项目子类型使用 COM 聚合来扩展在 Microsoft 中编写的托管的项目[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]。 使用 COM 聚合，可以重复使用的托管的项目系统实现大部分并仍用于特定方案通过聚合和支持接口使用自定义。 有关项目子类型的详细信息，请参阅[项目子类型](../../extensibility/internals/project-subtypes.md)。  
  
## <a name="see-also"></a>另请参阅  
 [文档窗口和编辑器](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [清单： 创建新项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Visual Studio 中的层次结构](../../extensibility/internals/hierarchies-in-visual-studio.md)