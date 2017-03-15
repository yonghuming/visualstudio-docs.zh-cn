---
title: "XslTransformation 任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 4
author: kempb
ms.author: kempb
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
ms.openlocfilehash: d240cca44bf389f97eaa7f4709690c0dc89cacc1
ms.lasthandoff: 02/22/2017

---
# <a name="xsltransformation-task"></a>XslTransformation 任务
通过使用 XSLT 或编译的 XSLT 转换 XML 输入并输出到输出设备或文件。  
  
## <a name="parameters"></a>参数  
 下表描述了 `XslTransformation` 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|`OutputPaths`|所需的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定 XML 转换的输出文件。|  
|`Parameters`|可选 `String` 参数。<br /><br /> 指定 XSLT 输入文档的参数。|  
|`XmlContent`|可选 `String` 参数。<br /><br /> 指定 XML 输入为字符串。|  
|`XmlInputPaths`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定 XML 输入文件。|  
|`XslCompiledDllPath`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定已编译的 XSLT。|  
|`XslContent`|可选 `String` 参数。<br /><br /> 指定 XSLT 输入为字符串。|  
|`XslInputPath`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定 XSLT 输入文件。|  
  
## <a name="remarks"></a>备注  
 除了具有表中列出的参数，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数及其说明的列表，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)
