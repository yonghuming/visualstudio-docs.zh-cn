---
title: "向导 (。Vsz) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 9
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1dc3ff7964ea5290ffe926ef75773a7210b6449
ms.lasthandoff: 02/22/2017

---
# <a name="wizard-vsz-file"></a>向导 (。Vsz) 文件
集成的开发环境 (IDE) 使用.vsz 文件来启动向导。 这些.vsz 文件包含 IDE 使用来确定要调用哪个向导的信息以及要传递给向导的信息。  
  
 .Vsz 文件是不包含节.ini 格式的文本文件的版本。 对 IDE 知道的信息存储在文件开头。 这提供 IDE 调用向导.vsz 文件将传递给 IDE 中的参数之间的链接。 文件的其余部分提供的参数特定于该向导，可通过 IDE 收集并传递给特定的向导。  
  
 下面的示例演示.vsz 文件的内容。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 以下是.vsz 文件中的部分。  
  
|部件|说明|  
|----------|-----------------|  
|VSWizard|在文件中的第一个参数是模板文件格式的版本号。 此版本号必须为 6.0、 7.0、 7.1 中或 8.0。 其他数字不能启动，并且会导致无效的格式错误。|  
|向导|此字段包含 OLE 的 ProgID 向导，或者的 GUID 字符串表示形式的 ide 共同创建向导的 CLSID。|  
|参数|这些部件是可选的。 您可以添加多达需要。|  
  
 可以将附加自定义的参数传递到向导的.vsz 文件参数。 每个值作为变量数组中的字符串元素传递给该向导。 有关详细信息，请参阅[自定义参数](../../extensibility/internals/custom-parameters.md)。 有关如何使用.vsz 文件中开发的自定义向导的信息，请参阅[。Vsz 文件 （项目控制）](/visual-cpp/ide/dot-vsz-file-project-control)  
  
 若要将默认区域设置 ID 添加到您的.vsz 文件中，指定`FALLBACK_LCID`= 的 xxxx，其中 xxxx 是区域设置 ID，例如，1033 为英语。 当`FALLBACK_LCID`定义参数，则向导将使用提供的回退区域设置 ID，如果找不到当前的 ID。  
  
## <a name="see-also"></a>另请参阅  
 [自定义参数](../../extensibility/internals/custom-parameters.md)   
 [向导](../../extensibility/internals/wizards.md)   
 [模板目录说明 (。Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
