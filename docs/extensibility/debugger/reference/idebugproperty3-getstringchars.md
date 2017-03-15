---
title: "IDebugProperty3::GetStringChars |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
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
ms.sourcegitcommit: b743df25d0d17465de411211f5b0b6893bf67f9b
ms.openlocfilehash: a9433d9914f647c43d8190fb15fb35a99bf77a7b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
检索此属性与关联的字符串，并将其存储在用户提供的缓冲区。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```c#  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>参数  
 `buflen`  
 [in]用户提供缓冲区可以容纳最大字符数。  
  
 `rgString`  
 [out]返回的字符串。  
  
 [C + + 只]，`rgString`是指向该缓冲区用于接收字符串的 Unicode 字符的指针。 此缓冲区必须至少为`buflen`值中的字符 （非字节）。  
  
 `pceltFetched`  
 [out]返回的实际存储在缓冲区中的字符数的位置。 (可以是`NULL`c + + 中。)  
  
## <a name="return-value"></a>返回值  
 如果成功，返回`S_OK`; 否则返回错误代码。  
  
## <a name="remarks"></a>备注  
 在 c + +，必须格外小心以确保缓冲区已至少`buflen`Unicode 字符。 请注意，Unicode 字符 2 个字节长。  
  
> [!NOTE]
>  在 c + +，则返回的字符串不包括终止 null 字符。 如果给出，`pceltFetched`将在字符串中指定的字符数。  
  
## <a name="example"></a>示例  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>另请参阅  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
