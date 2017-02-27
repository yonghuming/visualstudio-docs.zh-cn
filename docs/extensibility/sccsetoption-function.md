---
title: "SccSetOption 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccSetOption"
helpviewer_keywords: 
  - "SccSetOption 函数"
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccSetOption 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数设置控制的源代码管理插件行为的选项。  
  
## 语法  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源控制插件上下文结构。  
  
 nOption  
 \[\] in正在设置的选项。  
  
 dwVal  
 \[\] in选项的设置。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|说明|  
|-------|--------|  
|SCC\_OK|已成功设置的选项。|  
|SCC\_I\_SHARESUBPROJOK|返回的 if `nOption` 已 `SCC_OPT_SHARESUBPROJ` 和源代码管理插件允许 IDE 以将目标文件夹设置。|  
|SCC\_E\_OPNOTSUPPORTED|该选项未设置，不应依赖。|  
  
## 备注  
 IDE 将调用此函数可控制行为的源代码管理插件。 第一个参数， `nOption`, ，该值指示第二个，，正在设置的值 `dwVal`, ，指示要执行的操作具有此值。 该插件将与此信息存储 `pvContext``,` 因此 IDE 必须在调用后调用此函数 [SccInitialize](../extensibility/sccinitialize-function.md) \(但不是一定在每次调用后 [SccOpenProject](../extensibility/sccopenproject-function.md)\)。  
  
 所选项及其值的摘要:  
  
|`nOption`|`dwValue`|描述|  
|---------------|---------------|--------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|启用\/禁用后台事件队列。|  
|`SCC_OPT_USERDATA`|任意值|指定要传递给一个用户值 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 回调函数。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指示是否 IDE 当前支持取消操作。|  
|`SCC_OPT_NAMECHANGEPFN`|指向 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 回调函数|将指针设置到名称更改回调函数。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|指示 IDE 允许超出其文件手动 \(通过源代码管理用户界面\) 检查或是否它们必须先签出只能通过源代码管理插件。|  
|`SCC_OPT_SHARESUBPROJ`|不可用|如果源代码管理插件允许 IDE 以指定的本地项目文件夹，该插件返回 `SCC_I_SHARESUBPROJOK`。|  
  
## SCC\_OPT\_EVENTQUEUE  
 如果 `nOption` 是 `SCC_OPT_EVENTQUEUE`, ，禁用 \(或重新启用\) IDE 后台处理。 例如，在编译期间 IDE 可能会指示源代码管理插件以停止在空闲处理的任何类型。 在编译之后, 它将重新启用后台处理，以使即插即用接程序的事件队列中保持最新。 对应于 `SCC_OPT_EVENTQUEUE` 值 `nOption`, ，有两个可能值为 `dwVal`, ，即 `SCC_OPT_EQ_ENABLE` 和 `SCC_OPT_EQ_DISABLE`。  
  
## SCC\_OPT\_HASCANCELMODE  
 如果值为 `nOption` 是 `SCC_OPT_HASCANCELMODE`, ，IDE 允许用户取消长时间运行。 设置 `dwVal` 到 `SCC_OPT_HCM_NO` \(默认值\) 指示 IDE 具有无取消模式。 如果想要使用者必须能够取消，源代码管理插件必须提供其自己的取消按钮。`SCC_OPT_HCM_YES` 指示 IDE 提供了取消操作，因此不需要显示其自己的取消按钮插件 SCC 的能力。 如果 IDE 设置 `dwVal` 到 `SCC_OPT_HCM_YES`, ，它已准备好响应 `SCC_MSG_STATUS` 和 `DOCANCEL` 消息发送到 `lpTextOutProc` 回调函数 \(请参阅 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)\)。 如果 IDE 未设置此变量，该插件发送不应这两条消息。  
  
## SCC\_OPT\_NAMECHANGEPFN  
 如果 nOption 设置为 `SCC_OPT_NAMECHANGEPFN`, ，以及这两个源控制插件和 IDE 允许它，该插件可以实际重命名或移动的文件在源代码管理操作过程。`dwVal` 将被设置为指向类型的函数指针 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)。 在源代码管理操作，该插件可以调用此函数，在三个参数中传递。 这些是文件，该文件中，以及指向相关 IDE 的信息的指针 \(包括完全限定路径\) 的新名称 \(包括完全限定路径\) 的旧名称。 在此最后一个指针发送通过调用的 IDE `SccSetOption` 与 `nOption` 设置为 `SCC_OPT_USERDATA`, ，与 `dwVal` 指向数据。 支持此函数是可选的。 VSSCI 即插即用\-可使用此功能必须将初始化为其函数指针和用户数据变量 `NULL`, ，并且它必须不会调用重命名功能，除非它给予了其中一个。 它应还准备保存已获得的值或更改以响应对的新调用 `SccSetOption`。 此操作不会在源代码管理命令操作，但命令之间，它可能会发生。  
  
## SCC\_OPT\_SCCCHECKOUTONLY  
 如果 nOption 设置为 `SCC_OPT_SCCCHECKOUTONLY`, ，IDE 表示，当前打开的项目中的文件还是应该永远不会检查手动通过源代码管理系统的用户界面。 相反，应签出文件只能通过源代码管理插件 IDE 控制之下。 如果 `dwValue` 设置为 `SCC_OPT_SCO_NO`, ，这意味着这些文件应由插件通常处理，可以通过源代码管理 UI 签出。 如果 `dwValue` 设置为 `SCC_OPT_SCO_YES`, ，然后仅插件允许签出文件，并且不应调用的源代码管理系统 UI。 这是针对其中 IDE 可能会有"伪"，只能通过 IDE 签出有意义的情况。  
  
## SCC\_OPT\_SHARESUBPROJ  
 如果`nOption` 设置为 `SCC_OPT_SHARESUBPROJ`, ，IDE 测试是否从源代码管理中添加文件时，源代码管理插件可以使用指定的本地文件夹。 值 `dwVal` 参数在这种情况下并不重要。 如果该插件允许 IDE 以指定的本地目标文件夹，这些文件会添加源中的位置控制何时 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) 调用时，则该插件必须返回 `SCC_I_SHARESUBPROJOK` 时 `SccSetOption` 调用函数。 然后使用 IDE `lplpFileNames` 参数 `SccAddFromScc` 函数传递的目标文件夹中。 该插件使用该目标文件夹将添加从源代码管理中的文件。 如果该插件不返回 `SCC_I_SHARESUBPROJOK` 时 `SCC_OPT_SHARESUBPROJ` 设置选项，则 IDE 假定插件是能够将文件添加只在当前的本地文件夹中。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)