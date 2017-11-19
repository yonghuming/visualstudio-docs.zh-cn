---
title: "SccOpenProject 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccOpenProject
helpviewer_keywords: SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d61b4fade0775c5e017a85fa5364779bc567b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccopenproject-function"></a>SccOpenProject 函数
此函数打开现有的源代码管理项目，或创建一个新。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpUser  
 [在中，out]用户 （不超过 SCC_USER_SIZE，包括 NULL 终止符） 的名称。  
  
 lpProjName  
 [in]标识项目的名称的字符串。  
  
 lpLocalProjPath  
 [in]到项目的工作文件夹路径。  
  
 lpAuxProjPath  
 [在中，out]一个可选的辅助字符串，用于标识项目 （不超过 SCC_AUXPATH_SIZE，包括 NULL 结束符）。  
  
 lpComment  
 [in]正在创建一个新项目的注释。  
  
 lpTextOutProc  
 [in]可选的回调函数显示从源代码管理插件输出的文本。  
  
 dwFlags  
 [in]信号是否需要如果项目是未知的源创建新项目控制插件。 值可以是的组合`SCC_OP_CREATEIFNEW`和`SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|打开项目的成功。|  
|SCC_E_INITIALIZEFAILED|无法初始化项目。|  
|SCC_E_INVALIDUSER|用户不无法登录到源代码管理系统所造成。|  
|SCC_E_COULDNOTCREATEPROJECT|项目不存在之前调用; `SCC_OPT_CREATEIFNEW`标志已设置，但无法创建项目。|  
|SCC_E_PROJSYNTAXERR|无效的项目语法。|  
|SCC_E_UNKNOWNPROJECT|项目是未知的源代码管理插件，和`SCC_OPT_CREATEIFNEW`，未设置标志。|  
|SCC_E_INVALIDFILEPATH|无效或不可用的文件路径。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NONSPECFICERROR|非特定的失败;未初始化的源控制系统。|  
  
## <a name="remarks"></a>备注  
 用户名称，请传入 IDE (`lpUser`)，或它可能只需在一个指针传递到一个空字符串。 如果没有用户名，源代码管理插件应使用它作为默认值。 但是，如果未将名称传递，或者如果具有给定名称的登录失败，该插件应提示用户登录并将返回中的有效名称`lpUser`当它收到的有效登录`.`因为插件可能会更改的用户名称字符串IDE 将始终分配缓冲区的大小 (`SCC_USER_LEN`+ 1 或 SCC_USER_SIZE，其中包括 null 终止符的占用空间)。  
  
> [!NOTE]
>  IDE 可能还需要执行的第一个操作可能是对的调用`SccOpenProject`函数或[SccGetProjPath](../extensibility/sccgetprojpath-function.md)。 因此，这两个具有相同`lpUser`参数。  
  
 `lpAuxProjPath`和`lpProjName`读取解决方案文件，或它们返回到调用`SccGetProjPath`函数。 这些参数包含源代码管理插件将与项目相关联的字符串，并且仅对插件有意义。 如果没有此类字符串中的解决方案文件并且用户不提示浏览 (这将返回一个字符串通过`SccGetProjPath`函数)，IDE 将空字符串传递两个`lpAuxProjPath`和`lpProjName`，而且我们预期要更新这些值通过插件在此函数返回。  
  
 `lpTextOutProc`是由源代码管理插件用于显示命令结果输出到 IDE 提供的回调函数指针。 中详细描述此回调函数[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
> [!NOTE]
>  如果打算充分利用此源代码管理插件，它必须为其设置`SCC_CAP_TEXTOUT`中标记出来[SccInitialize](../extensibility/sccinitialize-function.md)。 如果未设置该标志，或者如果 IDE 不支持此功能，`lpTextOutProc`将`NULL`。  
  
 `dwFlags`参数控制结果中，打开项目当前不存在。 它包含两个 bitflags`SCC_OP_CREATEIFNEW`和`SCC_OP_SILENTOPEN`。 如果已打开项目存在，则函数将只需将打开项目并返回`SCC_OK`。 如果项目不存在，并且`SCC_OP_CREATEIFNEW`标志位于，源代码管理插件可以在源代码管理系统中创建项目，打开它，并返回`SCC_OK`。 如果项目不存在，并且`SCC_OP_CREATEIFNEW`标志处于关闭状态，该插件应然后检查`SCC_OP_SILENTOPEN`标志。 如果不在该标志，该插件可能会提示用户输入项目名称。 如果该标志是在上，该插件应只需返回`SCC_E_UNKNOWNPROJECT`。  
  
## <a name="calling-order"></a>调用顺序  
 在正常运行的事件， [SccInitialize](../extensibility/sccinitialize-function.md)将首先调用，以打开源控制会话。 会话可能包含对的调用`SccOpenProject`、 其他源控制插件 API 函数调用后, 跟和将终止通过调用[SccCloseProject](../extensibility/scccloseproject-function.md)。 此类会话可能会重复几次之前[SccUninitialize](../extensibility/sccuninitialize-function.md)调用。  
  
 如果源代码管理插件集`SCC_CAP_REENTRANT`中位`SccInitialize`，则上面的会话顺序可能在并行中重复多次。 不同`pvContext`结构跟踪的不同的会话，其中的每个`pvContext`一次处于与一个打开的项目相关联。 基于`pvContext`参数，该插件可以确定哪些项目引用中的任何特定调用。 如果的功能位`SCC_CAP_REENTRANT`未设置，nonreentrant 源控件插件的局限于其能够处理多个项目。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT`源控件插件 API 版本 1.1 中引入了位。 其未设置或版本 1.0，在将被忽略，并且所有版本 1.0 源控件插件都被都认为是 nonreentrant。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [字符串长度限制](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)