---
title: "C# 和 C++ 中的 VSCT 示例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 文件, 示例"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# C# 和 C++ 中的 VSCT 示例
VSCT 成为定义命令新的方式。  因此，更改在 VSCT 此示例演示如何发生在 C\# 和 C\+\+ 编译。  命令现在定义在与外部文件的 C\+\+ 和与一个符号部分的 C\# 在 .vsct 文件。  
  
## 定义命令  
  
### C\+\+ 外部文件  
 在 C\+\+ 示例， VSCT 编译器包含外部文件定义常数使用命令中的定义中。  该方式包括这些文件从而定义常数在命令的定义将在 .vsct 文件中的一 `Extern` 标记，并指定外部文件引用的名称在 `href` 属性中。  这些文件是:  
  
-   Guids.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 下面的代码段从 c. c\+\+ .vsct 文件演示如何将这些文件:  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### C\# 符号  
 在 c\# 示例中， .vsct 文件的 `Symbols` 部分在定义命令的文件。  符号定义在一 .vsct 文件是 c\# 起源于元素 ID 由命令表定义方式。  下面是一个代码段从指定命令和常数与它们的 C\# .vsct 文件:  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## 嵌入位图  
  
### C\#  
 在 C\+\+ 和 C\# CTO 二进制文件的位图存储在磁盘上外部。  位图 ID 定义使用方法，使得该定义必须为位图提供 GUID 属性，该属性包含位图的位图条的 `resID` 属性，然后元素的数值 ID 使用在按钮定义 \(`usedList` 属性\) 内。  此描述的一个重要方面是元素 ID 必须是实际索引 \(从 1 开始\) 在位图条内的位图。  
  
 在下面的示例中位图条包括仅包含一个元素。  此元素的 ID 定义为 guidMenuAndCommandsCmdSet: 必须定义 bmpArrow，因此， bmpArrow 为 1。  它也是位图的说明。  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)