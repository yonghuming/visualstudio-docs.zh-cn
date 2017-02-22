---
title: "SccInitialize 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccInitialize"
helpviewer_keywords: 
  - "SccInitialize 函数"
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccInitialize 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数初始化源代码管理插件，并提供了集成的开发环境 \(IDE\) 的限制和功能。  
  
## 语法  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### 参数  
 `ppvContext`  
 \[\] in源代码管理插件可以在此处放置指向其上下文结构的指针。  
  
 `hWnd`  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 `lpCallerName`  
 \[\] in调用的源代码管理插件的程序的名称。  
  
 `lpSccName`  
 \[in、 out\]源代码管理插件放置其自己的名称的位置的缓冲区 \(不能超过 `SCC_NAME_LEN`\)。  
  
 `lpSccCaps`  
 \[\] out返回的源代码管理插件的功能标志。  
  
 `lpAuxPathLabel`  
 \[in、 out\]源代码管理插件放置一个字符串，描述的位置的缓冲区 `lpAuxProjPath` 返回由参数 [SccOpenProject](../extensibility/sccopenproject-function.md) 和 [SccGetProjPath](../extensibility/sccgetprojpath-function.md) \(不能超过 `SCC_AUXLABEL_LEN`\)。  
  
 `pnCheckoutCommentLen`  
 \[\] out返回签出注释的最大允许长度。  
  
 `pnCommentLen`  
 \[\] out返回其他注释的最大允许长度。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|源控件初始化成功。|  
|SCC\_E\_INITIALIZEFAILED|无法初始化系统。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户以执行指定的操作。|  
|SCC\_E\_NONSPECFICERROR|模糊失败;未初始化源代码管理系统。|  
  
## 备注  
 它首次加载源代码管理插件时，IDE 将调用此函数。 这样，IDE 将某些信息，如到插件的调用方名称。 IDE 还会让某些信息，如注释和即插即用接程序的功能的最大允许长度。  
  
 `ppvContext` 指向 `NULL` 指针。 源代码管理插件可以分配供自己使用的结构并将存储到在该结构的指针 `ppvContext`。 IDE 会将此指针传递给每个其他 VSSCI API 函数，允许插件而无需对全局存储中有可用的上下文信息和支持的插件的多个实例。 这种结构应该释放时 [SccUninitialize](../extensibility/sccuninitialize-function.md) 调用。  
  
 `lpCallerName` 和 `lpSccName` 参数使 IDE 和源代码管理插件能够交换名称。 可能使用这些名称只是为了区分多个实例，或者它们可能会实际出现在菜单或对话框。  
  
 `lpAuxPathLabel` 参数是一个字符串作为注释用于标识存储在解决方案文件，并传递到源代码管理插件对的调用中的辅助项目路径 [SccOpenProject](../extensibility/sccopenproject-function.md)。[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 使用字符串"SourceSafe 项目:";其他源代码管理插件应避免使用此特定字符串。  
  
 `lpSccCaps` 参数给出源代码管理插件一个位置来存储 bitflags，该值指示即插即用接程序的功能。 \(有关功能 bitflags 的完整列表，请参阅 [功能标志](../extensibility/capability-flags.md)\)。 例如，如果将结果写到一个调用方提供回调函数，该插件会将设置功能的插件计划位 SCC\_CAP\_TEXTOUT。 这将向 IDE 来创建版本控制结果的窗口发送信号。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [功能标志](../extensibility/capability-flags.md)