---
title: "符号元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "符号元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素符号"
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 符号元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义 Guid 和其他 VSCT 元素使用的 Id。 对于非托管代码，此信息通常来自由指定的标头文件 [Extern 元素](../extensibility/extern-element.md)。 托管代码使用的符号元素定义此信息的子元素。  
  
 如果从现有的.cto 文件创建.vsct 文件，将作为符号元素的子级生成符号。 有关详细信息，请参阅[如何：从现有 .Cto 文件创建 .Vsct 文件](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)。  
  
 不应与混淆符号元素 [定义元素](../extensibility/define-element.md), ，用于定义由预处理器使用的名称 \/ 值对。  
  
## 语法  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|无||  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|GuidSymbol|定义在 GUID 符号。 GuidSymbol 有两个必需的属性: 名称和值。 名称是该符号的名称，值为 GUID 字符串形式的值。<br /><br /> 例如: \< GuidSymbol 名称 \="guidVsPackage1Pkg"value \="{c5f54698\-101a\-4846\-84d3\-dc748f9cd848}"\/ \>|  
|IDSymbol|定义的符号。 IDSymbol 有两个必需的属性: 名称和值。 名称是该符号的名称，值为一个字符串形式的符号的值。<br /><br /> 例如: \< IDSymbol 名称 \="MyMenuGroup"value \="0x1020"\/ \>|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|.Vsct 文件的根元素。|  
  
## 示例  
  
```  
<Symbols> <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" /> <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="cmdidMyCommand" value="0x0100" /> <IDSymbol name="cmdidMyTool" value="0x0101" /> </GuidSymbol> </Symbols>  
```  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)