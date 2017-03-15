---
title: "位图元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 架构元素位图"
  - "位图元素 (VSCT XML 架构)"
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 位图元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

对 [位图元素](../extensibility/bitmap-element.md) 元素进行分组。  
  
## 语法  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
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
|[Bitmaps Element](../extensibility/bitmaps-element.md)|位图元素进行分组。|  
|[位图元素](../extensibility/bitmap-element.md)|定义一个位图。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具栏上的命令的集合。|  
  
## 示例  
  
```  
<Bitmaps> <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/> </Bitmaps>  
```  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)