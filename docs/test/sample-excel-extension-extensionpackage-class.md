---
title: "示例 Excel 扩展：ExtensionPackage 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 20e3ac96d5b12002b11a9e93b413c48738f57153
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-extensionpackage-class"></a>示例 Excel 扩展：ExtensionPackage 类
此类用于扩展 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 类，并提供测试 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 工作表的编码的 UI 测试的入口点。  
  
## <a name="assembly-attribute"></a>程序集属性  
 文件以程序集属性开头，此属性将此程序集标识为 UI 测试扩展。  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 此属性声明自定义扩展包类的基类名称、包类的名称和完全限定的类名。  
  
## <a name="simple-properties"></a>简单属性  
 此类包含的属性的值供编码的 UI 测试框架用于标识和描述扩展和程序集。 有关详细信息，请参阅代码注释。  
  
## <a name="getservice-method"></a>GetService 方法  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> 方法是由编码的 UI 测试框架使用的单一接入点（由每个对象的基类标识），用于访问技术管理器、属性提供程序和操作筛选器。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

