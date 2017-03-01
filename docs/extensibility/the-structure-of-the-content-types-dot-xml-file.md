---
title: "[Content_types].xml 文件的结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>[Content_types].xml 文件的结构
包含有关的 VSIX 包中的内容类型的信息。 Visual Studio 将使用 [Content_Types].xml 文件以安装程序包，但不会安装该文件本身。  
  
> [!NOTE]
>  本主题仅适用于在 VSIX 包中使用的 [Content_Type].xml 文件，尽管 [Content_Types].xml 文件类型是组成部分*开放式打包约定 (OPC)*标准。 有关详细信息，请参阅[OPC: 新标准的打包数据](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 网站上。  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述的根元素及其属性和子元素。  
  
### <a name="root-element"></a>根元素  
  
|元素|描述|  
|-------------|-----------------|  
|`Types`|包含枚举的 VSIX 包中的文件类型的子元素。|  
  
### <a name="attributes"></a>特性  
  
|特性|说明|  
|---------------|-----------------|  
|`Xmlns`|（必选。）架构用于此 [Content_Types].xml 文件的位置。|  
  
### <a name="attribute-name-attribute"></a>{属性名称}属性  
  
|值|说明|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|内容类型架构的位置。|  
  
### <a name="child-elements"></a>子元素  
 `Types`元素可以包含任意数量的`Default`元素。  
  
|元素|描述|  
|-------------|-----------------|  
|`Default`|描述 VSIX 包中的内容类型。 包的每个文件类型必须具有其自己`Default`元素。|  
  
### <a name="attributes"></a>特性  
  
|特性|说明|  
|---------------|-----------------|  
|`Extension`|VSIX 包中的文件文件扩展名。|  
|`ContentType`|描述此类是与文件扩展名相关联的内容。|  
  
### <a name="attribute-name-attribute"></a>{属性名称}属性  
 Visual Studio 能够识别以下`ContentType`的关联值`Extension`类型。  
  
|扩展名|ContentType|  
|---------------|-----------------|  
|txt|文本/无格式|  
|pkgdef|文本/无格式|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm 或 html|text/html|  
|rtf|应用程序/rtf 格式|  
|pdf|应用程序/pdf|  
|gif 图像|image/gif|  
|jpg 或 jpeg|映像/jpg|  
|tiff|图像/tiff|  
|vsix|应用程序/zip|  
|zip|应用程序/zip|  
|dll|应用程序/八进制数流|  
|所有其他文件类型|应用程序/八进制数流|  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>说明  
 下面的 [Content_Types].xml 文件介绍了典型的 VSIX 包。  
  
### <a name="code"></a>代码  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>另请参阅  
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC︰ 用于打包你的数据新标准](http://go.microsoft.com/fwlink/?LinkID=148207)
