---
title: "IDebugObject2::IsUserData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "IDebugObject2::IsUserData 方法"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

确定对象是否表示用户数据。  
  
## 语法  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### 参数  
 `pfUser`  
 \[out\] 返回非零 \(`TRUE`\)，如果对象表示用户数据;零 \(0\)`FALSE`\); 如果未。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 用户数据是作为 JustMyCode 中指定的模块中的所有对象 \(指示一个模块作为用户代码并显示在堆栈跟踪\) 的用户可配置选项。  
  
## 请参阅  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)