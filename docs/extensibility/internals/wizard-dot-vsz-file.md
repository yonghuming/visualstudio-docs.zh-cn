---
title: "向导 (。Vsz) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7f4abe6240f799ed6db71fcf04a40774facaf6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-vsz-file"></a>向导 (。Vsz) 文件
集成的开发环境 (IDE) 使用.vsz 文件来启动向导。 这些.vsz 文件包含 IDE 使用来确定哪一种向导要调用的信息以及要传递给向导的信息。  
  
 .Vsz 文件是不包含节.ini 格式的文本文件的版本。 已知到 IDE 的信息存储在文件的开头。 这提供 IDE 调用向导与.vsz 文件传递到 IDE 中的参数之间的链接。 文件的其余部分提供的参数特定于该向导并且，是要收集由 IDE，并传递到特定的向导。  
  
 下面的示例演示.vsz 文件的内容。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 以下是.vsz 文件中的部分。  
  
|部件|描述|  
|----------|-----------------|  
|VSWizard|文件中的第一个参数是模板文件格式的版本号。 此版本号必须 6.0、 7.0、 7.1、 或 8.0。 其他数字无法启动，并会导致无效的格式错误。|  
|向导|此字段包含 OLE 的 ProgID 向导，或或者的 GUID 字符串表示形式由 IDE 共同创建向导的 CLSID。|  
|参数|这些部分为可选。 你可以添加多达所需。|  
  
 参数，以将附加的自定义参数传递到向导.vsz 文件。 每个值中的变体数组的字符串元素作为传递给该向导。 有关详细信息，请参阅[自定义参数](../../extensibility/internals/custom-parameters.md)。 有关如何使用开发中的自定义向导.vsz 文件的信息，请参阅[。Vsz 文件 （项目控制）](/cpp/ide/dot-vsz-file-project-control)  
  
 若要将默认区域设置 ID 添加到你.vsz 文件中，指定`FALLBACK_LCID`= 的 xxxx，其中 xxxx 是区域设置 ID，例如 1033 为英语。 当`FALLBACK_LCID`定义参数，该向导使用提供的回退区域设置 ID，如果找不到当前的 ID。  
  
## <a name="see-also"></a>另请参阅  
 [自定义参数](../../extensibility/internals/custom-parameters.md)   
 [向导](../../extensibility/internals/wizards.md)   
 [模板目录说明 (.Vsdir) 文件](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)