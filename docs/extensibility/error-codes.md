---
title: "错误代码 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "错误代码，源代码管理插件"
  - "源代码管理插件，错误代码"
  - "错误 [Visual Studio SDK]"
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 错误代码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当源控制插件 API 函数返回一个错误时，它需要是以下的错误代码之一。 所有错误都是负数，警告或信息性错误代码都为正数，并且成功是 0。  
  
|错误代码|值|描述|  
|----------|-------|--------|  
|`SCC_I_SHARESUBPROJOK`|7|插件支持从两个步骤中的源代码管理中添加文件。 有关详细信息，请参阅[SccSetOption](../extensibility/sccsetoption-function.md)。|  
|`SCC_I_FILEDIFFERS`|6|本地文件是不同于在源代码管理数据库中的文件 \(例如， [SccDiff](../extensibility/sccdiff-function.md) 可能会返回此值\)。|  
|`SCC_I_RELOADFILE`|5|在源代码管理操作; 过程中更改本地文件IDE 应尽可能重新加载该文件。|  
|`SCC_I_FILENOTAFFECTED`|4|该文件不受影响。|  
|`SCC_I_PROJECTCREATED`|3|在源代码管理操作过程中创建项目 \(例如，在调用期间 [SccOpenProject](../extensibility/sccopenproject-function.md) 时 `SCC_OP_CREATEIFNEW` 指定标志\)。|  
|`SCC_I_OPERATIONCANCELED`|2|操作已取消。|  
|`SCC_I_ADV_SUPPORT`|1|用于指定的命令的高级选项的插件支持。 有关详细信息，请参阅[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)。|  
|`SCC_OK`|0|成功。|  
|`SCC_E_INITIALIZEFAILED`|\-1|错误: 初始化失败。|  
|`SCC_E_UNKNOWNPROJECT`|\-2|错误: 项目是未知的。|  
|`SCC_E_COULDNOTCREATEPROJECT`|\-3|错误: 无法创建项目。|  
|`SCC_E_NOTCHECKEDOUT`|\-4|错误: 该文件未签出。|  
|`SCC_E_ALREADYCHECKEDOUT`|\-5|错误: 该文件已签出。|  
|`SCC_E_FILEISLOCKED`|\-6|错误: 该文件被锁定。|  
|`SCC_E_FILEOUTEXCLUSIVE`|\-7|错误: 该文件以独占方式签出。|  
|`SCC_E_ACCESSFAILURE`|\-8|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|`SCC_E_CHECKINCONFLICT`|\-9|错误: 时发生冲突签入的过程。|  
|`SCC_E_FILEALREADYEXISTS`|\-10|错误: 该文件已存在。|  
|`SCC_E_FILENOTCONTROLLED`|\-11|错误: 该文件不是源代码管理下。|  
|`SCC_E_FILEISCHECKEDOUT`|\-12|错误: 该文件已签出。|  
|`SCC_E_NOSPECIFIEDVERSION`|\-13|错误: 没有指定的版本。|  
|`SCC_E_OPNOTSUPPORTED`|\-14|错误: 不支持该操作。|  
|`SCC_E_NONSPECIFICERROR`|\-15|非特定的错误。|  
|`SCC_E_OPNOTPERFORMED`|\-16|不执行错误，该操作。|  
|`SCC_E_TYPENOTSUPPORTED`|\-17|错误: 源代码管理系统不支持二进制文件，该文件，例如的类型。|  
|`SCC_E_VERIFYMERGE`|\-18|文件已被自动合并，但尚未检查，因为它是挂起的用户验证。|  
|`SCC_E_FIXMERGE`|\-19|文件已被自动合并，但未检入由于必须手动解决合并冲突。|  
|`SCC_E_SHELLFAILURE`|\-20|由于外壳程序失败，出现错误。|  
|`SCC_E_INVALIDUSER`|\-21|错误: 用户无效。|  
|`SCC_E_PROJECTALREADYOPEN`|\-22|错误: 该项目已打开。|  
|`SCC_E_PROJSYNTAXERR`|\-23|项目存在语法错误。|  
|`SCC_E_INVALIDFILEPATH`|\-24|错误: 文件路径无效。|  
|`SCC_E_PROJNOTOPEN`|\-25|错误: 该项目未打开。|  
|`SCC_E_NOTAUTHORIZED`|\-26|错误: 用户未授权来执行此操作。|  
|`SCC_E_FILESYNTAXERR`|\-27|文件存在语法错误。|  
|`SCC_E_FILENOTEXIST`|\-28|错误，本地文件不存在。|  
|`SCC_E_CONNECTIONFAILURE`|\-29|Error: there was 时失败的连接。|  
|`SCC_E_UNKNOWNERROR`|\-30|出现未知的错误。|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|\-31|当前正在进行后台 get 操作。|  
  
## 提供用于快速检查宏  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE) IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE) IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## 备注  
 所有源控制插件 API 函数 \(除 [SccAdd](../extensibility/sccadd-function.md), ，[SccCheckin](../extensibility/scccheckin-function.md), ，和 [SccDiff](../extensibility/sccdiff-function.md)\) 都按照预期成功时作为参数传递的本地文件中的工作文件夹不存在。 例如，IDE 可能会发出调用 [SccCheckout](../extensibility/scccheckout-function.md) 或 [SccUncheckout](../extensibility/sccuncheckout-function.md) 中工作文件夹中，不存在，但在源代码管理系统中存在的文件。 此调用将会成功。 只有在没有工作文件夹中或在源代码管理系统中没有文件时该函数应失败。  
  
 某些函数，如 `SccAdd` 和 `SccCheckin`, ，应专门返回 `SCC_E_FILENOTEXIST` 工作文件夹中的文件不存在时。 其他函数需要时工作文件不存在，如果函数在源代码管理系统上有效的文件名操作成功。  
  
 即使插件已将其标记文件只读的某项操作时，源代码管理插件应在工作文件夹中，做任何假设有关文件上的权限。 工作文件夹中的文件可以移动、 删除和更改即插即用接程序的控制范围之外。  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)