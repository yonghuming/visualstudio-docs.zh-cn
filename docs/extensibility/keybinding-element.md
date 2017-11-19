---
title: "键绑定元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f620d895defbeeb3317f4a977db454a14ce3adc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="keybinding-element"></a>键绑定元素
键绑定元素指定的命令的键盘快捷方式。  
  
 命令可以具有与之关联的单个和双键绑定。 单个键绑定的一个示例是 CTRL + S 表示**保存**命令。 双键绑定需要两个连续的键组合来触发命令。 双键绑定的一个示例是 CTRL + K、 CTRL + K 可以设置书签。  
  
## <a name="syntax"></a>语法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。|  
|id|必需。|  
|编辑器|必需。 编辑器 GUID 指示此键盘快捷方式将对其活动的编辑上下文。 全局绑定作用域值为"guidVSStd97"。|  
|key1|必需。 有效的值包括所有键入是字母数字，以及两位数的十六进制值以 0x 开头和[VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx)。|  
|mod1|可选。 CTRL、 ALT 和 SHIFT 之间用空格分隔的任意组合。|  
|key2|可选。 有效的值包括所有键入是字母数字，以及两位数的十六进制值以 0x 开头和[VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx)。|  
|mod2|可选。 CTRL、 ALT 和 SHIFT 之间用空格分隔的任意组合。|  
|仿真程序|可选。|  
|条件|可选。 请参阅[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|父级||  
|批注||  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[KeyBindings 元素](../extensibility/keybindings-element.md)|组键绑定元素和其他键绑定分组。|  
  
## <a name="example"></a>示例  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>另请参阅  
 [键绑定元素](../extensibility/keybindings-element.md)   
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
