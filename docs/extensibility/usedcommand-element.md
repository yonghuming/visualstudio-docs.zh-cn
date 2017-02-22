---
title: "UsedCommand 元素 | Microsoft Docs"
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
  - "UsedCommands 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素 UsedCommands"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# UsedCommand 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

允许访问另一个.vsct 文件中定义的命令的 VSPackage。 例如，如果你的 VSPackage 使用标准 **副本** 命令，由定义 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外壳程序中，您可以将命令添加到菜单或工具栏上而无需重新实现。  
  
## 语法  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|guid|必需。 标识的命令的 GUID ID 对 GUID。|  
|id|必需。 标识的命令的 GUID ID 对 ID。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|无||  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|UsedCommand 元素进行分组和其他 UsedCommands 分组。|  
  
## 备注  
 通过将命令添加到 `<UsedCommands>` 元素，VSPackage 通知 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage 要求命令的环境。 应添加 `<UsedCommand>` 包所需的任何命令的元素可能不包括在所有版本和 Visual Studio 的配置。 例如，如果您的包调用特定于 Visual c \+ \+ 的命令，该命令将不可用的 Visual Web Developer 用户除非您包含 `<UsedCommand>` 命令的元素。  
  
## 示例  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## 请参阅  
 [UsedCommands 元素](../extensibility/usedcommands-element.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)