---
title: "位图元素 | Microsoft Docs"
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
  - "VSCT XML 架构元素位图"
  - "位图元素 (VSCT XML 架构)"
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 位图元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义一个位图。 从资源或从文件加载位图。  
  
## 语法  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|guid|必需。 ID 的 GUID 的命令标识符的 GUID。<br /><br /> 将 guid 属性的位图不与任何 VSPackage 或其他命令组相关联。  它应该是唯一的位图定义并不用于任何其他用途。|  
|resID|ID 的 GUID 的命令标识符的 ID。 ResID 或 href 属性是必需的。<br /><br /> ResID 属性是一个整数资源 ID，用于确定是要在合并的命令表期间加载的位图条。  加载命令表时，将从相同的模块的资源加载指定的资源 ID 的位图。|  
|usedList|所需的 resID 属性是否存在。 位图条中选择可用的映像。|  
|href|位图的路径。 ResID 或 href 属性是必需的。<br /><br /> Include 路径中搜索所指示的图像文件，生成的二进制文件中嵌入的。  命令表合并时，请在图像复制并且没有查找其他资源或负载需要。  如果的 usedList 属性不存在，可以使用条带中的所有映像。 **Note:**  映像可能包括.bmp、.png 和.gif 的几种格式之一提供。  编译器的早期版本不支持具有 alpha 信息部分透明的 32 位位图图像。 这些版本的解决方法是使用.png 格式。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[位图元素](../extensibility/bitmaps-element.md)|位图元素进行分组。|  
  
## 示例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/>  
```  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)