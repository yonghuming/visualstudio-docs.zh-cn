---
title: "VSCT XML 架构参考 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fc82041f8ab2790c63c271f85d573a3105ab8b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 架构参考
提供命令表编译器架构元素，其中包含允许子元素和属性为每个。  
  
 一个基于 XML 的命令表 (.vsct) 配置文件定义到集成的开发环境 (IDE) 的 VSPackage 提供的命令元素。 这些元素包括菜单项、 菜单、 工具栏和组合框。  
  
> [!NOTE]
>  VSCT 编译器可以在.vsct 文件上运行预处理器。 因为这通常是 c + + 预处理器，你可以定义包括且宏，具有相同的语法在 c + + 文件中使用。 此示例在.vsct 文件**新项目**向导创建 VSPackage 项目。  
  
## <a name="optional-elements"></a>可选元素  
 某些 VSCT 元素是可选的。 如果`Parent`将暗示 Group_Undefined:0，未指定参数。 如果`Icon`将暗示 guidOfficeIcon:msotcidNoIcon，未指定参数。 定义的快捷键后，模拟，这将是通常未使用，是可选的。  
  
 通过指定的位置中的位图条，可能会在编译时嵌入位图项`href`自变量。 位图条带会在合并过程中复制而不是从 DLL 的资源中提取。 当`href`提供参数，将`usedList`自变量会变为可选，和位图条带中的所有存储槽都被视为已使用。  
  
 通过使用符号名称，必须定义所有的 GUID 和 ID 值。 标头文件中或 VSCT 可能定义这些名称\<符号 > 部分。 符号名称必须是本地的包括通过\<Include > 元素，或所引用的\<Extern > 元素。 从在指定的标头文件中导入符号名称\<Extern > 元素，如果它遵循简单的模式，#define 符号值。 值可能是另一个符号，只要以前定义该符号。 GUID 定义必须遵循 OLE 或 c + + 格式。 ID 值可能是十进制数字或以 0x 开头的十六进制数字，如以下行中所示：  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634、 0xe53d、 0x4a2c，{0xad、 0xcb，0x55、 0x14，0x5c、 0x93，0x62，0xc8}}  
  
 可能使用 XML 注释，但是往返的图形用户界面 (GUI) 工具可能会放弃它们。 内容\<批注 > 保证元素都将保留，与格式无关。  
  
## <a name="schema-hierarchy"></a>架构层次结构  
 .Vsct 文件具有以下主要元素。  
  
 [CommandTable 元素](../extensibility/commandtable-element.md)  
  
 [Extern 元素](../extensibility/extern-element.md)  
  
 [ Include元素](../extensibility/include-element.md)  
  
 [Define 元素](../extensibility/define-element.md)  
  
 [Commands 元素](../extensibility/commands-element.md)  
  
 [CommandPlacements 元素](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings 元素](../extensibility/keybindings-element.md)  
  
 [UsedCommands 元素](../extensibility/usedcommands-element.md)  
  
 [Parent 元素](../extensibility/parent-element.md)  
  
 [Icon 元素](../extensibility/icon-element.md)  
  
 [Strings 元素](../extensibility/strings-element.md)  
  
 [ Command Flag元素](../extensibility/command-flag-element.md)  
  
 [Symbols 元素](../extensibility/symbols-element.md)  
  
 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSPackage 中的命令传送](../extensibility/internals/command-routing-in-vspackages.md)