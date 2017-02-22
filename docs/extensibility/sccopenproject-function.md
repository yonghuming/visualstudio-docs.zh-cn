---
title: "SccOpenProject 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccOpenProject"
helpviewer_keywords: 
  - "SccOpenProject 函数"
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# SccOpenProject 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数将打开现有的源代码管理项目或创建新的证书。  
  
## 语法  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpUser  
 \[in、 out\]用户 \(不超过 SCC\_USER\_SIZE，包括 NULL 结束符\) 的名称。  
  
 lpProjName  
 \[\] in标识项目的名称的字符串。  
  
 lpLocalProjPath  
 \[\] in该项目的工作文件夹路径。  
  
 lpAuxProjPath  
 \[in、 out\]辅助一个可选字符串，标识项目 \(不超过 SCC\_AUXPATH\_SIZE，包括 NULL 结束符\)。  
  
 lpComment  
 \[\] in正在创建一个新项目的注释。  
  
 lpTextOutProc  
 \[\] in要显示文本输出从源代码管理插件的可选的回调函数。  
  
 dwFlags  
 \[\] in信号是否需要如果项目是未知的源创建一个新项目控制插件。 值可以是组合的 `SCC_OP_CREATEIFNEW` 和 `SCC_OP_SILENTOPEN.`  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|打开项目的成功。|  
|SCC\_E\_INITIALIZEFAILED|无法初始化项目。|  
|SCC\_E\_INVALIDUSER|用户不可以登录到源代码管理系统。|  
|SCC\_E\_COULDNOTCREATEPROJECT|项目不存在之前调用; `SCC_OPT_CREATEIFNEW` 标志已设置，但无法创建该项目。|  
|SCC\_E\_PROJSYNTAXERR|无效的项目的语法。|  
|SCC\_E\_UNKNOWNPROJECT|该项目是未知的源代码管理插件，和 `SCC_OPT_CREATEIFNEW` 未设置标志。|  
|SCC\_E\_INVALIDFILEPATH|无效或不可用的文件路径。|  
|SCC\_E\_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NONSPECFICERROR|非特定的失败;未初始化的源控制系统。|  
  
## 备注  
 用户名称，请传入 IDE \(`lpUser`\)，或它可能只是一个指针传递到一个空字符串。 如果没有用户名，源代码管理插件应使用它作为默认值。 但是，如果未将名称传递，或者如果具有给定名称的登录失败，该插件应提示用户以用户身份登录并将返回中的有效名称 `lpUser` 当接收有效的登录名`.` 因为插件可能会更改用户名称字符串，IDE 会始终分配大小的缓冲区 \(`SCC_USER_LEN`\+ 1 或 SCC\_USER\_SIZE，包括 null 终止符的空间\)。  
  
> [!NOTE]
>  IDE 可能还需要执行的第一个操作可能是对的调用 `SccOpenProject` 函数或 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)。 出于此原因，它们都具有相同 `lpUser` 参数。  
  
 `lpAuxProjPath` 和`lpProjName` 读取该解决方案文件，或它们返回到调用 `SccGetProjPath` 函数。 这些参数包含源代码管理插件将与项目相关联的字符串，并且只对该插件有意义。 如果没有此类字符串位于解决方案文件，并且用户不提示浏览 \(它将返回一个字符串通过 `SccGetProjPath` 函数\)，IDE 将空字符串传递两个 `lpAuxProjPath` 和 `lpProjName`, ，而且我们预期要更新该插件，该函数返回时这些值。  
  
 `lpTextOutProc` 是指向由源代码管理插件用于显示命令结果输出到 IDE 提供一个回调函数的指针。 中详细描述此回调函数 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
> [!NOTE]
>  如果打算利用此源代码管理插件，它必须为其设置 `SCC_CAP_TEXTOUT` 中标记出来 [SccInitialize](../extensibility/sccinitialize-function.md)。 如果未设置该标志，或者如果 IDE 不支持此功能， `lpTextOutProc` 将 `NULL`。  
  
 `dwFlags` 参数控制结果的事件中打开该项目当前不存在。 它包含两个 bitflags `SCC_OP_CREATEIFNEW` 和 `SCC_OP_SILENTOPEN`。 如果存在已打开的项目，该函数只需将打开项目并返回 `SCC_OK`。 如果项目不存在并且 `SCC_OP_CREATEIFNEW` 标志为 on，源代码管理插件可以在源代码管理系统中创建项目，打开它，并返回 `SCC_OK`。 如果项目不存在，并且 `SCC_OP_CREATEIFNEW` 标志处于关闭状态，该插件应该再检查 `SCC_OP_SILENTOPEN` 标志。 如果不在该标志，该插件可能会提示用户输入项目名称。 如果该标志上，则该插件只应返回 `SCC_E_UNKNOWNPROJECT`。  
  
## 调用顺序  
 在正常的事件，过程 [SccInitialize](../extensibility/sccinitialize-function.md) 将第一次调用，以打开源控制会话。 会话可能包含对的调用 `SccOpenProject`, 、 其他源控制插件 API 函数调用后, 跟，将通过调用终止 [SccCloseProject](../extensibility/scccloseproject-function.md)。 此类会话可能会重复几次之前 [SccUninitialize](../extensibility/sccuninitialize-function.md) 调用。  
  
 如果源代码管理插件集 `SCC_CAP_REENTRANT` 中位 `SccInitialize`, ，则上面的会话顺序可能会在并行中重复多次。 不同 `pvContext` 结构跟踪不同的会话，其中的每个 `pvContext` 一次是与一个打开的项目相关联。 基于`pvContext` 参数，该插件可以确定在任何特定的调用中引用的项目。 如果的功能位 `SCC_CAP_REENTRANT` 未设置，则 nonreentrant 源代码管理插件以使用多个项目的能力受到的限制。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT` 源控制插件 API 的 1.1 版中引入了位。 未设置，或者在 1.0 版中，将被忽略和所有版本 1.0 源代码管理插件都被都认为是 nonreentrant。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [字符串长度限制](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)