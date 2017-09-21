---
title: "IDebugClassField::GetDefaultIndexer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetDefaultIndexer"
helpviewer_keywords: 
  - "IDebugClassField::GetDefaultIndexer 方法"
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取默认索引器的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```c#  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### 参数  
 `pbstrIndexer`  
 \[out\] 返回包含默认索引器的名称的字符串。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有默认的索引器。  否则，返回错误代码。  
  
## 备注  
 类的默认索引器被标记为数组访问的 `Default` 属性的属性。  这是特定于 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]。  这是在 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 声明的默认索引器的示例，以及如何使用它。  
  
```vb#  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## 请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)