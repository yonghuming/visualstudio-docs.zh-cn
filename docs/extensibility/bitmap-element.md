---
title: "Bitmap 元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 223342709dbe97fe38fb7a495ce482ae70e1c807
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bitmap-element"></a>位图元素
定义位图。 从资源或从文件加载位图。  
  
## <a name="syntax"></a>语法  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。 GUID/ID 命令标识符的 GUID。<br /><br /> 位图的 guid 属性不与任何 VSPackage 或其他命令组相关联。  它应是唯一的位图定义，并且不能用于任何其他用途。|  
|ResID|ID 的 GUID/ID 命令标识符。 ResID 或 href 属性是必需的。<br /><br /> 该 resID 属性为整数资源 ID，它确定是要在合并的命令表期间加载的位图条。  加载命令表后，将从相同模块的资源加载指定的资源 ID 的位图。|  
|usedList|所需 resID 属性是否存在。 位图栏中选择可用的映像。|  
|href|位图的路径。 ResID 或 href 属性是必需的。<br /><br /> Include 路径中搜索所指示的图像文件，生成的二进制文件中嵌入的。  命令表合并时，请在图像复制和任何其他资源查找或负载是必需的。  如果 usedList 属性不存在，条带中的所有映像都将用。 **注意：**可能中包括.bmp、.png 和.gif 的几种格式之一提供映像。  早期版本的编译器不支持 alpha 信息部分透明度的 32 位位图图像。 这些版本的解决方法是使用.png 格式。|  
|条件|可选。 请参阅[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|位图元素进行分组。|  
  
## <a name="example"></a>示例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)