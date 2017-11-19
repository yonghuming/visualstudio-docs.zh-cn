---
title: "UsedCommand 元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b3974c9103a385badc56fda759ee95ef3a40a93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="usedcommand-element"></a>UsedCommand 元素
允许 VSPackage 访问在另一个.vsct 文件中定义的命令。 例如，如果你的 VSPackage 使用标准**复制**命令，通过定义[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]外壳程序中，你可以将命令添加到菜单或工具栏上无需重新执行它。  
  
## <a name="syntax"></a>语法  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。 标识的命令的 GUID ID 对 GUID。|  
|id|必需。 标识该命令的 GUID ID 对的 ID。|  
|条件|可选。 请参阅[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|无||  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|组 UsedCommand 元素和其他 UsedCommands 分组。|  
  
## <a name="remarks"></a>备注  
 通过添加到命令`<UsedCommands>`元素，VSPackage 通知[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage，需要该命令的环境。 应添加`<UsedCommand>`包所需的任何命令的元素可能不包括在所有版本和 Visual Studio 的配置。 例如，如果你的包调用特定于 Visual c + + 的命令，该命令将不可用的 Visual Web Developer 用户除非你包括`<UsedCommand>`命令的元素。  
  
## <a name="example"></a>示例  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>另请参阅  
 [UsedCommands 元素](../extensibility/usedcommands-element.md)   
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)