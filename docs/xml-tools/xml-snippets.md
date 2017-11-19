---
title: "XML 代码段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4f53c8d55011f52a3ed6ecf6fa4fab77855a9ec3
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2017
---
# <a name="xml-snippets"></a>XML 代码片断
XML 编辑器提供了一个实用工具，调用*XML 代码段*，这样，你更快地生成 XML 文件。 XML 代码段可以通过插入文件反复使用。 您还可以根据 XML 架构定义语言 (XSD) 架构生成 XML 数据。  
  
## <a name="reusable-xml-snippets"></a>可反复使用的 XML 代码段  
 “XML 编辑器”包括许多代码段，用于执行一些常见的任务。 这样，您更容易创建 XML 文件。 例如，如果编写 XML 架构，使用“复杂类型序列元素”和“简单类型元素”代码段将以下 XML 文本插入文件。 然后，根据您的需要更改 `name` 值。  
  
```xml
<xs:element name="name">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="name">  
        <xs:simpleType>  
          <xs:restriction base="xs:string"></xs:restriction>  
        </xs:simpleType>  
      </xs:element>  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 可以通过两种方法插入代码段。 **插入代码段**命令在光标位置插入 XML 代码段。 **侧**命令使用所选文本环绕 XML 代码段。 这两个命令均可以从**IntelliSense**下的子菜单**编辑**菜单上，或通过编辑器快捷菜单。  
  
 有关详细信息，请参阅[如何： 使用 XML 代码段](../xml-tools/how-to-use-xml-snippets.md)。  
  
## <a name="schema-generated-xml-snippets"></a>从架构生成的 XML 代码段  
 “XML 编辑器”还可以从 XML 架构生成 XML 代码段。 通过此功能可以使用从该元素的架构信息生成的 XML 元素来填充元素。  
  
 有关详细信息，请参阅[如何： 生成 XML 代码段从 XML 架构](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)。  
  
## <a name="create-new-xml-snippets"></a>新建 XML 代码段  
 除了默认情况下随 [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio 提供的代码段之外，您还可以创建并使用自己的 XML 代码段。  
  
 有关详细信息，请参阅[如何： 创建 XML 代码段](../xml-tools/how-to-create-xml-snippets.md)。  
  
## <a name="see-also"></a>另请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)