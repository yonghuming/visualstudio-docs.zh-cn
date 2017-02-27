---
title: "SccUncheckout 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUncheckout"
helpviewer_keywords: 
  - "SccUncheckout 函数"
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUncheckout 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数会撤消以前的签出操作，从而将所选的文件或文件的内容还原到前签出状态。 签出后对文件所做的所有更改都都将丢失。  
  
## 语法  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 nFiles  
 \[\] in中指定的文件数 `lpFileNames` 数组。  
  
 lpFileNames  
 \[\] in要撤消签出文件的完全限定的本地路径名称的数组。  
  
 选项  
 \[\] in\(未使用\) 的命令标志。  
  
 pvOptions  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|撤消签出成功。|  
|SCC\_E\_FILENOTCONTROLLED|所选的文件不是源代码管理下。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NONSPECIFICERROR|非特定故障。 撤消签出未成功。|  
|SCC\_E\_NOTCHECKEDOUT|用户没有签出该文件。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_PROJNOTOPEN|尚未从源代码管理打开项目。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前取消了操作。|  
  
## 备注  
 执行此操作后 `SCC_STATUS_CHECKEDOUT` 和 `SCC_STATUS_MODIFIED` 标志会同时为清除对其执行撤消签出的文件。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)