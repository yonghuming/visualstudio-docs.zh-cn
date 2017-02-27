---
title: "IDebugDocumentText2::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2::GetText"
helpviewer_keywords: 
  - "IDebugDocumentText2::GetText"
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugDocumentText2::GetText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

文档中的指定位置检索文本。  
  
## 语法  
  
```cpp#  
HRESULT GetText(   
   TEXT_POSITION pos,  
   ULONG         cMaxChars,  
   WCHAR*        pText,  
   ULONG*        pcNumChars  
);  
```  
  
```c#  
int GetText(   
   eumn_TEXT_POSITION pos,  
   uint               cMaxChars,  
   IntPtr             pText,  
   out uint           pcNumChars  
);  
```  
  
#### 参数  
 `pos`  
 \[in\] 指示要检索的文本位置的 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) 结构。  
  
 `cMaxChars`  
 \[in\] 文本字符的最大数目要检索的。  
  
 `pText`  
 \[in, out\] 对于将使用所需的文本填充的缓冲区的指针。  此缓冲区必须能够包含宽字符的至少 `cMaxChars` 数字。  
  
 `pcNumChars`  
 \[out\] 返回实际检索的字符数。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 示例  
 此示例演示此方法如何从 C\# 调用。  
  
```c#  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace Mynamespace  
{  
    class MyClass  
    {  
         string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)  
        {  
             string documentText = string.Empty;  
             if (pText != null)  
             {  
                  uint numLines = 0;  
                  uint numChars = 0;  
                  int hr;  
                  hr = pText.GetSize(ref numLines, ref numChars);  
                  if (ErrorHandler.Succeeded(hr))  
                  {  
                       IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));  
                       uint actualChars = 0;  
                       hr = pText.GetText(pos, numChars, buffer, out actualChars);  
                       if (ErrorHandler.Succeeded(hr))  
                       {  
                            documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);  
                       }  
                       Marshal.FreeCoTaskMem(buffer);  
                  }  
              }  
              return documentText;  
         }  
    }  
}  
```  
  
## 请参阅  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)