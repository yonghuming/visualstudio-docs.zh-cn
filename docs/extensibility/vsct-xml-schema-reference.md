---
title: "VSCT XML 架构参考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 命令表配置文件 (VSCT)、 XML 架构"
  - "VSCT XML 架构元素"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCT XML 架构参考
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

提供命令表编译器架构元素，其中包含允许子元素和属性为每个。  
  
 基于 XML 的命令表配置 \(.vsct\) 文件定义了集成的开发环境 \(IDE\) 的 VSPackage 提供的命令元素。 这些元素包括菜单项、 菜单、 工具栏和组合框。  
  
> [!NOTE]
>  VSCT 编译器可以在.vsct 文件上运行预处理器。 因为这通常是 c \+ \+ 预处理器，您可以定义包含和宏，不会产生与在 c \+ \+ 文件中使用的语法相同。 此操作的示例提供在.vsct 文件 **新项目** 向导为 VSPackage 项目创建。  
  
## 可选元素  
 某些 VSCT 元素是可选的。 如果 `Parent` 将暗示 Group\_Undefined:0，未指定参数。 如果 `Icon` 将暗示 guidOfficeIcon:msotcidNoIcon，未指定参数。 定义的快捷键后，模拟，这是通常未使用，是可选的。  
  
 通过指定的位置中的位图条，可能会在编译时嵌入位图项 `href` 参数。 位图条在合并过程中复制而不是从该 DLL 的资源中提取。 当 `href` 未提供参数， `usedList` 参数将成为可选的并且所有插槽的位图条都被都视为已使用。  
  
 通过使用符号名称，必须定义所有 GUID 和 ID 值。 标头文件中或在 VSCT \< 符号 \> 部分中，可以定义这些名称。 符号名称必须是本地的 \< 包括 \> 元素，通过包括或由 \< Extern \> 元素引用。 符号名称从它遵循简单模式，如果 \< Extern \> 元素中指定的标头文件导入 \#define 符号值。 值可能是另一个符号，只要以前定义该符号。 GUID 定义必须遵循 OLE 或 c \+ \+ 格式。 ID 值可能是十进制数字或十六进制数以 0x 开头，如以下各行中所示:  
  
-   {} 6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8  
  
-   {0x6d484634、 0xe53d、 0x4a2c，{0xad、 0xcb，0x55、 0x14，0x5c、 0x93，0x62，0xc8}}  
  
 可以使用 XML 注释，但往返的图形用户界面 \(GUI\) 工具可能会放弃它们。 保证 \< 批注 \> 元素的内容都将保留，与格式无关。  
  
## 架构层次结构  
 .Vsct 文件具有以下主要元素。  
  
 [CommandTable 元素](../extensibility/commandtable-element.md)  
  
 [Extern 元素](../extensibility/extern-element.md)  
  
 [Include 元素](../extensibility/include-element.md)  
  
 [定义元素](../extensibility/define-element.md)  
  
 [Commands 元素](../extensibility/commands-element.md)  
  
 [CommandPlacements 元素](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)  
  
 [键绑定元素](../extensibility/keybindings-element.md)  
  
 [UsedCommands 元素](../extensibility/usedcommands-element.md)  
  
 [父元素](../extensibility/parent-element.md)  
  
 [Icon 元素](../extensibility/icon-element.md)  
  
 [字符串元素](../extensibility/strings-element.md)  
  
 [命令标志元素](../extensibility/command-flag-element.md)  
  
 [符号元素](../extensibility/symbols-element.md)  
  
 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的命令传送](../extensibility/internals/command-routing-in-vspackages.md)