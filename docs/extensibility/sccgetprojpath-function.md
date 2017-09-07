---
title: "SccGetProjPath 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b45e9a9f33bd5f1b30ee0f300385ef984ce1bc0b
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 函数
此函数会提示用户输入是一个字符串，仅对源代码管理插件有意义的项目路径。 当用户是，将调用：  
  
-   创建新项目  
  
-   将现有项目添加到版本控制  
  
-   尝试查找现有的版本控制项目  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpUser  
 [在中，out]用户名 （不超过 SCC_USER_SIZE，包括 NULL 终止符）  
  
 lpProjName  
 [在中，out]IDE 项目、 项目工作区中或生成文件 （不超过 SCC_PRJPATH_SIZE，包括 NULL 终止符） 的名称。  
  
 lpLocalPath  
 [在中，out]项目的工作路径。 如果`bAllowChangePath`是`TRUE`，源代码管理插件可以修改此字符串 （不超过 _MAX_PATH，包括 null 结束符）。  
  
 lpAuxProjPath  
 [在中，out]返回的项目路径 （不超过 SCC_PRJPATH_SIZE，包括 NULL 终止符） 的缓冲区。  
  
 bAllowChangePath  
 [in]如果这是`TRUE`，源代码管理插件可以查询和修改`lpLocalPath`字符串。  
  
 pbNew  
 [在中，out]传入的值指示是否创建新项目。 返回值指示成功创建项目：  
  
|传入|解释|  
|--------------|--------------------|  
|true|用户可能创建一个新的项目。|  
|false|用户不可能创建一个新的项目。|  
  
|传出|解释|  
|--------------|--------------------|  
|true|创建新项目。|  
|false|选择了现有项目。|  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功创建或检索项目。|  
|SCC_I_OPERATIONCANCELED|已取消该操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。|  
|SCC_E_CONNECTIONFAILURE|尝试连接到源代码管理系统时出错。|  
|SCC_E_NONSPECIFICERROR|发生了未指定的错误。|  
  
## <a name="remarks"></a>备注  
 此函数的目的是供 IDE 以获取参数`lpProjName`和`lpAuxProjPath`。 源代码管理插件提示用户输入此信息后，它会将这两个字符串传递回 IDE 中。 IDE 仍然存在其解决方案文件中的这些字符串并将它们传递到[SccOpenProject](../extensibility/sccopenproject-function.md)每当用户打开此项目。 这些字符串启用要跟踪与项目关联的信息的插件。  
  
 当第一次调用函数时，`lpAuxProjPath`设置为空字符串。 `lProjName`也可能为空，或它可能包含 IDE 项目名称，可能会使用源代码管理插件或者将其忽略。 在该函数成功返回时，该插件返回两个相应的字符串。 IDE，不作出任何假设这些字符串，不会使用它们，并且不允许用户对其进行修改。 如果用户想要更改设置，将调用 IDE`SccGetProjPath`同样，在相同的值将其传递之前接收在前一次。 这样，对这两个字符串插件的完全控制。  
  
 有关`lpUser`，IDE 可能传入用户名，或者它可能只需在一个指针传递到一个空字符串。 如果没有用户名，源代码管理插件应使用它作为默认值。 但是，如果未将名称传递，或者具有给定名称的登录失败，该插件应提示用户输入登录名和密码名称后`lpUser`当它收到的有效登录。 因为插件可能会更改此字符串，IDE 将始终分配缓冲区的大小 (`SCC_USER_LEN`+ 1)。  
  
> [!NOTE]
>  IDE 执行的第一个操作可能是调用`SccOpenProject`函数或`SccGetProjPath`函数。 因此，这两个具有相同`lpUser`参数，它使源代码管理插件在任一时记录中的用户。 即使从函数返回表示失败，该插件必须填充此字符串与有效的登录名。  
  
 `lpLocalPath`是用户其中保留项目的目录。 它可能是空字符串。 如果没有当前定义 （如果用户尝试从源代码管理系统中下载的项目） 的目录并且`bAllowChangePath`是`TRUE`，源代码管理插件可以提示用户输入或使用其他某种方法来将其拥有字符串插入`lpLocalPath`。 如果`bAllowChangePath`是`FALSE`，该插件不应更改为字符串，因为用户已在指定的目录中工作。  
  
 如果用户创建新项目将在源代码管理下，源代码管理插件可能会不实际创建它在源代码管理系统时`SccGetProjPath`调用。 相反，它返回传递的非零值的字符串沿`pbNew`，指示将在源代码管理系统中创建的项目。  
  
 例如，如果中的用户**新项目**Visual Studio 中的向导将他或她的项目添加到源代码管理、 Visual Studio 会调用此函数和插件确定它是否可以在到的源控制系统中创建新项目包含 Visual Studio 项目。 如果用户单击**取消**之前完成向导，永远不会创建项目。 如果用户单击**确定**，Visual Studio 会调用`SccOpenProject`，并传入`SCC_OPT_CREATEIFNEW`，并在该时间创建受源代码管理项目。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
