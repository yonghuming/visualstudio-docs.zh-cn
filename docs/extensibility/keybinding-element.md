---
title: "键绑定元素 | Microsoft Docs"
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
  - "VSCT XML 架构元素，键绑定"
  - "键绑定元素 (VSCT XML 架构)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 键绑定元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

键绑定元素指定的命令的键盘快捷方式。  
  
 命令可拥有与之关联的单个和双键绑定。 单个键绑定的一个示例是 CTRL \+ S 表示 **保存** 命令。 双键绑定需要两个连续的键组合来触发命令。 双键绑定的一个示例是 CTRL \+ K、CTRL \+ K 以设置书签。  
  
## 语法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|guid|必需。|  
|id|必需。|  
|编辑器|必需。 编辑器 GUID 指示此键盘快捷方式将对其活动的编辑上下文。 全局绑定作用域值为"guidVSStd97"。|  
|key1|必需。 有效值包括所有键入是字母数字和也两位数字加 0x 和 VK\_constants 的十六进制值。|  
|mod1|可选。 CTRL、 ALT 和 SHIFT 用空格分隔的任意组合。|  
|key2|可选。 有效值包括所有键入是字母数字和也两位数字加 0x 和 VK\_constants 的十六进制值。|  
|mod2|可选。 CTRL、 ALT 和 SHIFT 用空格分隔的任意组合。|  
|仿真程序|可选。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|父级||  
|批注||  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[键绑定元素](../extensibility/keybindings-element.md)|键绑定元素进行分组和其他键绑定分组。|  
  
## 示例  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## 请参阅  
 [键绑定元素](../extensibility/keybindings-element.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)