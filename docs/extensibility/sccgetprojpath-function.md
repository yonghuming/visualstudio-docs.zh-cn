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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 551fe26fe20da62d6892a8c7e807cf6c22600fc8
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 函数
此函数会提示用户输入项目路径，即只对源代码管理插件有意义的字符串。 用户操作时调用它︰  
  
-   创建新的项目  
  
-   将现有项目添加到版本控制  
  
-   尝试查找现有的版本控制项目  
  
## <a name="syntax"></a>语法  
  
```cpp#  
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
 [in]源控制插件上下文结构。  
  
 hWnd  
 [in]源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 lpUser  
 [in、 out]用户名 （不超过 SCC_USER_SIZE，包括 NULL 结束符）  
  
 lpProjName  
 [in、 out]IDE 项目、 项目工作区中或生成文件 （不超过 SCC_PRJPATH_SIZE，包括 NULL 结束符） 的名称。  
  
 lpLocalPath  
 [in、 out]项目的有效路径。 如果`bAllowChangePath`是`TRUE`，源代码管理插件可以修改此字符串 （不超过 _MAX_PATH，包括 null 结束符）。  
  
 lpAuxProjPath  
 [in、 out]返回的项目路径 （不超过 SCC_PRJPATH_SIZE，包括 NULL 结束符） 的缓冲区。  
  
 bAllowChangePath  
 [in]如果这是`TRUE`，源代码管理插件可以提示输入，并修改`lpLocalPath`字符串。  
  
 pbNew  
 [in、 out]传入的值指示是否创建一个新项目。 返回值指示创建项目的成功︰  
  
|传入|解释|  
|--------------|--------------------|  
|TRUE|用户可以创建一个新的项目。|  
|FALSE|用户不可能创建一个新的项目。|  
  
|传出|解释|  
|--------------|--------------------|  
|TRUE|已创建一个新的项目。|  
|FALSE|选择一个现有项目。|  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回下列值之一︰  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功创建或检索项目。|  
|SCC_I_OPERATIONCANCELED|已取消该操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。|  
|SCC_E_CONNECTIONFAILURE|时尝试连接到源代码管理系统出现问题。|  
|SCC_E_NONSPECIFICERROR|发生了未指定的错误。|  
  
## <a name="remarks"></a>备注  
 此函数的目的是为了 IDE 以获取参数`lpProjName`和`lpAuxProjPath`。 源代码管理插件会提示用户提供此信息后，它会将这两个字符串传递回 IDE 中。 IDE 将仍然存在其解决方案文件中的这些字符串并将它们传递到[SccOpenProject](../extensibility/sccopenproject-function.md)每当用户打开此项目。 这些字符串启用该插件来跟踪与项目关联的信息。  
  
 当首次调用该函数时，`lpAuxProjPath`设置为空字符串。 `lProjName`此外可以为空，或者它可能包含 IDE 项目名称，可能会被使用或者忽略源代码管理插件。 该函数成功返回时，该插件返回两个对应的字符串。 IDE 不作出任何假设这些字符串，不会使用它们，并将不允许用户对其进行修改。 如果用户想要更改的设置，将调用 IDE`SccGetProjPath`同样，在相同的值并向其传递以前接收了上一次。 这样，对这两个字符串插件的完全控制。  
  
 有关`lpUser`、 IDE 可能会传递用户名称中，或它可能只是一个指针传递到一个空字符串。 如果没有用户名，源代码管理插件应使用它作为默认值。 但是，如果未将名称传递，或者具有给定名称的登录失败，该插件应提示用户输入登录名和传递回名称`lpUser`当接收有效的登录名。 因为该插件可能会更改此字符串，IDE 会始终分配大小的缓冲区 (`SCC_USER_LEN`+&1;)。  
  
> [!NOTE]
>  IDE 将执行的第一个操作可能会在调用`SccOpenProject`函数或`SccGetProjPath`函数。 因此，它们都具有相同`lpUser`参数，它使源代码管理插件在任一时间记录中的用户。 即使从函数返回表示失败，该插件必须填充此字符串与有效的登录名。  
  
 `lpLocalPath`为用户保留项目的位置的目录。 可能为空字符串。 如果没有当前定义的 （在尝试从源代码管理系统下载的项目的用户） 的目录并且`bAllowChangePath`是`TRUE`，源代码管理插件可以提示用户进行输入凭据或使用某些其他方法来将放到它自己的字符串`lpLocalPath`。 如果`bAllowChangePath`是`FALSE`，该插件不应更改字符串，因为用户已使用指定的目录中。  
  
 如果用户创建一个新项目来置于源代码管理之下，源代码管理插件可能不实际创建其在源代码管理系统时`SccGetProjPath`调用。 相反，它返回传递的非零值的字符串沿`pbNew`，指示将在源代码管理系统中创建的项目。  
  
 例如，如果用户在**新项目**Visual Studio 中的向导将他或她的项目添加到源代码管理、 Visual Studio 会调用此函数和插件确定它是否可以在源代码管理系统，以包含 Visual Studio 项目中创建一个新项目。 如果用户单击**取消**之前完成向导，永远不会创建项目。 如果用户单击**确定**，Visual Studio 会调用`SccOpenProject`，并传入`SCC_OPT_CREATEIFNEW`，并在该时间创建受源代码管理项目。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
