---
title: "IDebugPortPicker::DisplayPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayPortPicker"
  - "IDebugPortPicker::DisplayPortPicker"
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

显示允许用户选择端口的指定对话框。  
  
## 语法  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```c#  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### 参数  
 `hwndParentDialog`  
 \[in\] 父对话框的句柄。  
  
 `pbstrPortId`  
 \[out\] 端口标识符字符串。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  `S_FALSE` 的返回值 \(或 `S_OK` 的返回值和 `BSTR` 设置为 `NULL`\) 指示用户单击 **取消**。  
  
## 请参阅  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)