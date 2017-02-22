---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

从端口提供程序获取用户名。  
  
## 语法  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### 参数  
 `pbstrUserName`  
 \[out\] 包含用户名的字符串。  
  
## 返回值  
 如果方法成功，则返回 `S_OK`。  否则返回错误代码。  
  
## 备注  
 `GetUserName` 返回在 **附加的进程** 对话框的 **用户名** 列中显示的用户名。  若要查看 **附加的进程** 对话框中，单击 **附加的进程** 在 **工具** 菜单中 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 集成开发环境中 \(IDE\)。  
  
## 请参阅  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)