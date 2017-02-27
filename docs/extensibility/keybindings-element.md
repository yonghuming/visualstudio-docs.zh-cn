---
title: "键绑定元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "KeyBindings"
helpviewer_keywords: 
  - "VSCT XML 架构元素，键绑定"
  - "键绑定元素 (VSCT XML 架构)"
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 键绑定元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

键绑定元素进行分组的键绑定元素和其他键绑定分组。  
  
## 语法  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[键绑定元素](../extensibility/keybinding-element.md)|指定的命令的键盘快捷方式。|  
|[KeyBindings](../extensibility/keybindings-element.md)|键绑定元素进行分组和其他键绑定分组。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定义表示命令的所有元素。|  
  
## 示例  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## 请参阅  
 [键绑定元素](../extensibility/keybinding-element.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)