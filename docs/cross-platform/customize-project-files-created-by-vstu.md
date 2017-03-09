---
title: "自定义 VSTU 创建的项目文件 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 2
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9cac5f78264a03764071d2fa3716b30d717c45b6
ms.lasthandoff: 02/22/2017

---
# <a name="customize-project-files-created-by-vstu"></a>自定义 VSTU 创建的项目文件
Visual Studio Tools for Unity 在项目文件生成期间提供 Unity 样式回调。 注册 `VisualStudioIntegration.ProjectFileGeneration` 事件以在生成项目文件时对其进行修改。  
  
## <a name="demonstrates"></a>演示  
 如何自定义由 Visual Studio Tools for Unity 生成的 Visual Studio 项目文件。  
  
## <a name="example"></a>示例  
  
```c#  
using System;  
using System.IO;  
using System.Linq;  
using System.Text;  
using System.Xml.Linq;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class ProjectFileHook  
{  
    // necessary for XLinq to save the xml project file in utf8  
    class Utf8StringWriter : StringWriter  
    {  
        public override Encoding Encoding  
        {  
            get { return Encoding.UTF8; }  
        }  
    }  
  
    static ProjectFileHook()  
    {  
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>  
        {  
            // parse the document and make some changes  
            var document = XDocument.Parse(content);  
            document.Root.Add(new XComment("FIX ME"));  
  
            // save the changes using the Utf8StringWriter  
            var str = new Utf8StringWriter();  
            document.Save(str);  
  
            return str.ToString();  
        };  
    }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [示例：日志回调](../cross-platform/share-the-unity-log-callback-with-vstu.md)
