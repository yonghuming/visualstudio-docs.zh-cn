---
title: "SccSetOption 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccSetOption
helpviewer_keywords: SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0bc7ab99c6bc3643ee61b403e4aa0c40c41a63a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccsetoption-function"></a>SccSetOption 函数
此函数设置控制的插件的源控件的行为的选项。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 nOption  
 [in]设置选项。  
  
 dwVal  
 [in]设置选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功设置选项。|  
|SCC_I_SHARESUBPROJOK|时返回`nOption`已`SCC_OPT_SHARESUBPROJ`和源代码管理插件允许 IDE 以设置目标文件夹。|  
|SCC_E_OPNOTSUPPORTED|选项未设置，不应依赖。|  
  
## <a name="remarks"></a>备注  
 IDE 调用此函数可控制的插件的源控件的行为。 第一个参数， `nOption`，该值指示第二个时，正在设置的值`dwVal`，指示要执行的操作具有此值。 该插件将与此信息存储`pvContext``,`因此 IDE 必须在调用后调用此函数[SccInitialize](../extensibility/sccinitialize-function.md) (但不是一定在每次调用之后[SccOpenProject](../extensibility/sccopenproject-function.md))。  
  
 选项及其值的摘要：  
  
|`nOption`|`dwValue`|描述|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|启用/禁用后台事件队列。|  
|`SCC_OPT_USERDATA`|任意值|指定要传递给一个用户值[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回调函数。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指示是否 IDE 当前支持取消操作。|  
|`SCC_OPT_NAMECHANGEPFN`|指向[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回调函数|设置对名称更改的回调函数的指针。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|指示 IDE 允许外其文件手动 （通过源控件的用户界面） 检查或是否它们必须先签出只能通过源代码管理插件。|  
|`SCC_OPT_SHARESUBPROJ`|不可用|如果源代码管理插件允许 IDE 以指定的本地项目文件夹，该插件返回`SCC_I_SHARESUBPROJOK`。|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 如果`nOption`是`SCC_OPT_EVENTQUEUE`，禁用 （或重新启用） IDE 后台处理。 例如，在编译期间 IDE 可能指示源代码管理插件以停止在空闲处理的任何类型。 编译之后, 它会重新启用保持即插即用接程序的事件队列中最新的后台处理。 对应于`SCC_OPT_EVENTQUEUE`值`nOption`，有两个可能值`dwVal`，也就是说，`SCC_OPT_EQ_ENABLE`和`SCC_OPT_EQ_DISABLE`。  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 如果值`nOption`是`SCC_OPT_HASCANCELMODE`，IDE 允许用户取消长时间运行。 设置`dwVal`到`SCC_OPT_HCM_NO`（默认值） 指示 IDE 提供无取消模式。 如果想要能够取消用户，源代码管理插件必须提供其自己的取消按钮。 `SCC_OPT_HCM_YES`指示 IDE 提供取消操作，因此 SCC 插件不需要显示其自己的取消按钮的功能。 如果 IDE 设置`dwVal`到`SCC_OPT_HCM_YES`，它已准备好响应`SCC_MSG_STATUS`和`DOCANCEL`消息发送到`lpTextOutProc`回调函数 (请参阅[LPTEXTOUTPROC](../extensibility/lptextoutproc.md))。 如果 IDE 未设置此变量，该插件发送不应这两条消息。  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 如果 nOption 设置为`SCC_OPT_NAMECHANGEPFN`，和这两个源控件插件和 IDE 允许它，该插件可以实际重命名或移动的文件在源代码管理操作过程。 `dwVal`将设置为类型的函数指针[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)。 在源代码管理操作，该插件可以调用此函数，并在三个参数传递。 这些是文件的旧名称 （带有完全限定路径），该文件中，以及指向相关 IDE 的信息的指针 （带有完全限定路径） 的新名称。 IDE 将发送此最后一个指针在通过调用`SccSetOption`与`nOption`设置为`SCC_OPT_USERDATA`，与`dwVal`指向数据。 支持此函数是可选的。 VSSCI 即插即用-可使用此功能必须将初始化为其函数指针和用户数据变量`NULL`，并且它必须不会调用重命名功能，除非它已被授予一个。 它应还准备保留为其指定的值或更改以响应对的新调用`SccSetOption`。 此操作不会在源代码管理命令操作，但它可能会发生命令之间。  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 如果 nOption 设置为`SCC_OPT_SCCCHECKOUTONLY`，IDE 指示当前打开的项目中的文件应永远不会将已签出，手动通过源代码管理系统的用户界面。 相反，应将签出文件只能通过源代码管理插件 IDE 控制之下。 如果`dwValue`设置为`SCC_OPT_SCO_NO`，这意味着应由该插件通常被视为文件，并可以通过源代码管理 UI 签出。 如果`dwValue`设置为`SCC_OPT_SCO_YES`，然后仅插件则允许以签出文件，并且不应该调用的源控制系统 UI。 这是为： IDE 可能具有"伪文件"，可满足要签出只能通过 IDE 的情况。  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 如果`nOption`设置为`SCC_OPT_SHARESUBPROJ`，IDE 是否正在测试是否从源代码管理中添加文件时，源代码管理插件可以使用指定的本地文件夹。 值`dwVal`参数在此情况下并不重要。 如果该插件允许 IDE 以指定文件会添加从源的位置的本地目标文件夹控制[SccAddFromScc](../extensibility/sccaddfromscc-function.md)调用，则该插件必须返回`SCC_I_SHARESUBPROJOK`时`SccSetOption`技术支持部门调用。 然后使用 IDE`lplpFileNames`参数`SccAddFromScc`函数传递目标文件夹中。 该插件使用该目标文件夹将添加从源代码管理中的文件。 如果该插件不返回`SCC_I_SHARESUBPROJOK`时`SCC_OPT_SHARESUBPROJ`设置选项，则 IDE 假定该插件是否能够将文件添加仅在当前的本地文件夹中。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)