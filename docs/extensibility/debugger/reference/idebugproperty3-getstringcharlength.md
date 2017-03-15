---
title: "IDebugProperty3::GetStringCharLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetStringCharLength"
helpviewer_keywords: 
  - "IDebugProperty3::GetStringCharLength"
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty3::GetStringCharLength
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回字符数在关联的属性的字符串的。  
  
## 语法  
  
```cpp  
HRESULT GetStringCharLength(  
   ULONG *pLen  
);  
```  
  
```c#  
int GetStringCharLength(  
   out uint pLen  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|`pLen`|\[out\] 返回字符数。属性的字符串的。|  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  
  
## 备注  
 通常，该方法对用于，对于分配缓冲区中的一个前奏 [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) 方法。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口的 **CProperty** 对象的方法。  
  
```cpp#  
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)  
{  
    HRESULT hr = E_INVALIDARG;  
  
    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;  
  
    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;  
  
    if (pLen)  
    {  
        DEBUG_PROPERTY_INFO dpInfo;  
        dpInfo.bstrValue = NULL;  
        ULONG ulen = 0;  
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);  
        if (hr == S_OK && dpInfo.bstrValue)  
        {  
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)  
            {  
                ulen = 0;   //VSWhidbey#64815  
            }  
            else  
            {  
                ulen = ::SysStringLen(dpInfo.bstrValue);  
                if( ulen > 2 &&  
                    dpInfo.bstrValue[0] == L'"' &&  
                    dpInfo.bstrValue[ulen-1] == L'"')  
                {                      
                    ulen = ulen > 2 ? ulen - 2 : ulen;  //remove two double quotes  
                }  
            }  
        }  
        ::SysFreeString(dpInfo.bstrValue);  
        *pLen = ulen;  
    }  
    m_EVALFLAGS = oldEVALFLAGS;  
    return hr;  
}  
```  
  
## 请参阅  
 [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)