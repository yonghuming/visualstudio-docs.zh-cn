---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
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
  - "IDebugDocumentChecksum2 接口"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示调试的校验和文档并允许通过检查和组件之间。  
  
## 语法  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## 实现者说明  
 此接口可由显示 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 接口的所有元素实现。  但是，该主体实现调试引擎，以便可以通过返回 IDE 和使用在符号文件嵌入的校验和 \(\*.pdb\)，如果找到源时。  
  
## 方法  
 下表显示 `IDebugDocumentChecksum2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|检索文档检查和和算法标识符为最大字节数使用。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll