---
title: "IDebugErrorBreakpointResolution2::GetResolutionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorBreakpointResolution2::GetResolutionInfo"
helpviewer_keywords: 
  - "IDebugErrorBreakpointResolution2::GetResolutionInfo"
ms.assetid: d94c4f60-8796-4848-86ee-186bbaa613f5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugErrorBreakpointResolution2::GetResolutionInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取断点错误解析信息。  
  
## 语法  
  
```cpp#  
HRESULT GetResolutionInfo(   
   BPERESI_FIELDS            dwFields,  
   BP_ERROR_RESOLUTION_INFO* pErrorResolutionInfo  
);  
```  
  
```c#  
int GetResolutionInfo(   
   enum_BPERESI_FIELDS        dwFields,  
   BP_ERROR_RESOLUTION_INFO[] pErrorResolutionInfo  
);  
```  
  
#### 参数  
 `dwFields`  
 \[in\] 确定标志的组合。 [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) 枚举的 `pErrorResolutionInfo` 的哪些字段将完成。  
  
 `pErrorResolutionInfo`  
 \[in, out\] 使用断点解析的声明填充的 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 示例  
 下面的示例执行显示 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) 接口的简单 `CDebugErrorBreakpointResolution` 对象的方法。  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetResolutionInfo(  
   BPERESI_FIELDS dwFields,  
   BP_ERROR_RESOLUTION_INFO* pBPErrorResolutionInfo)    
{    
   HRESULT hr;    
  
   if (pBPErrorResolutionInfo)    
   {    
      // Copy the specified fields of the request information from the class member  
      // variable to the local BP_ERROR_RESOLUTION_INFO variable.    
      hr = CopyBP_ERROR_RESOLUTION_INFO(m_bpErrorResolutionInfo,  
                                        *pBPErrorResolutionInfo,  
                                        dwFields);    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}  
  
HRESULT CDebugErrorBreakpointResolution::CopyBP_ERROR_RESOLUTION_INFO(  
   BP_ERROR_RESOLUTION_INFO& bpResSrc,  
   BP_ERROR_RESOLUTION_INFO& bpResDest,  
   DWORD dwFields)  
{    
   HRESULT hr = S_OK;    
  
   // Start with a raw copy.    
   memcpy(&bpResDest, &bpResSrc, sizeof(BP_ERROR_RESOLUTION_INFO));    
  
   // The fields in the destination is the result of the AND of bpInfoSrc.dwFields  
   // and dwFields.    
   bpResDest.dwFields = dwFields & bpResSrc.dwFields;    
  
   // Fill in the bp location information if the BPERESI_BPRESLOCATION flag  
   // is set in BPERESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_BPRESLOCATION))    
   {    
      // Switch on the BP_TYPE.      
      switch (bpResSrc.bpResLocation.bpType)    
      {    
         case BPT_CODE:    
         {    
            // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.    
            bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();    
            break;    
         }    
         case BPT_DATA:    
         {    
            // Copy the bstrDataExpr, bstrFunc, and bstrImage of the  
            // BP_RESOLUTION_DATA structure.    
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);  
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);  
            bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);  
            break;  
         }  
         default:  
         {  
            assert(FALSE);  
            // Clear the BPERESI_BPRESLOCATION flag of the BPERESI_FIELDS  
            // in the destination BP_ERROR_RESOLUTION_INFO.  
            ClearFlag(bpResDest.dwFields, BPERESI_BPRESLOCATION);  
            break;  
         }    
      }    
   }    
   // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_PROGRAM))    
   {    
      bpResDest.pProgram->AddRef();    
   }    
   // AddRef the IDebuThread2 if the BPRESI_THREAD flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_THREAD))    
   {    
      bpResDest.pThread->AddRef();    
   }    
   // Check if the BPERESI_MESSAGE flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_MESSAGE))    
   {    
      // Copy the source bstrMessage into the destination bstrMessage.    
      bpResDest.bstrMessage = SysAllocString(bpResSrc.bstrMessage);    
      // Clear the destination flag if there is no message.    
      if (!bpResDest.bstrMessage)    
      {    
         ClearFlag(bpResDest.dwFields, BPERESI_MESSAGE);    
      }    
   }    
  
   return hr;    
}    
```  
  
## 请参阅  
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)