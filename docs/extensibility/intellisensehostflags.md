---
title: "IntelliSenseHostFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IntellisenseHostFlags"
helpviewer_keywords: 
  - "IntelliSense、 IntellisenseHostFlags 枚举"
  - "IntellisenseHostFlags 枚举"
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定 IntelliSense 主机标志。  
  
## 语法  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### 参数  
  
|成员|描述|  
|--------|--------|  
|`IHF_READONLYCONTEXT`|上下文缓冲区是只读的。|  
|`IHF_NOSEPARATESUBJECT`|没有使用者的文本。 上下文缓冲区包含智能感知目标 \(意味着 `!IHF_READONLYCONTEXT`\)。|  
|`IHF_SINGLELINESUBJECT`|不支持多行的主题文本。|  
|`IHF_FORCECOMMITTOCONTEXT`|与 `CanCommitIntoReadOnlyBuffer` 相同。|  
|`IHF_OVERTYPE`|编辑 \(在使用者或上下文\) 时，应该在改写模式来完成。|  
  
## 要求  
 SingleFileeditor.idl  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop>