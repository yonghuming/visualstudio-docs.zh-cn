---
title: "SccAddFromScc 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFromScc
helpviewer_keywords: SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5027e765e12ff483a9a27795990f0ddfbb479a5c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 函数
此函数允许用户浏览源代码管理系统中已有的文件，并随后使这些文件属于当前项目。 例如，此函数可以获取的常见头文件在当前项目而不复制该文件。 返回数组的文件， `lplpFileNames`，包含的用户想要将添加到 IDE 项目的文件列表。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpnFiles  
 [在中，out]正在添加中的文件数缓冲区。 (这是`NULL`如果指向的内存`lplpFileNames`是要释放。 请参阅备注详细信息）。  
  
 lplpFileNames  
 [在中，out]指向不目录路径的情况下的所有文件名称的指针的数组。 此数组进行分配和释放由源代码管理插件。 如果`lpnFiles`= 1 和`lplpFileNames`不`NULL`，指向数组中第一个名称`lplpFileNames`包含目标文件夹。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功，文件已位于，并添加到项目。|  
|SCC_I_OPERATIONCANCELED|操作已取消造成任何影响。|  
|SCC_I_RELOADFILE|需要重新加载文件或项目。|  
  
## <a name="remarks"></a>备注  
 IDE 调用此函数。 如果源代码管理插件支持指定的本地目标文件夹，IDE 将传递`lpnFiles`= 1 并将传递到的本地文件夹名称`lplpFileNames`。  
  
 当调用`SccAddFromScc`函数返回时，该插件已将值分配到`lpnFiles`和`lplpFileNames`，根据需要的文件名称数组分配内存 (请注意，此分配替代中的指针`lplpFileNames`)。 源代码管理插件负责将所有文件都放到用户的目录或指定的指定文件夹中。 然后，IDE 将文件添加到 IDE 项目。  
  
 最后，IDE 调用此函数的第二次，并传入`NULL`为`lpnFiles`。 通过源代码管理插件用于释放为的文件名称数组中分配的内存被解释为特殊的信号`lplpFileNames``.`  
  
 `lplpFileNames`是`char ***`指针。 源代码管理插件放置一个指针到指向文件的名称，因此此 api 以标准方式传递列表的指针的数组。  
  
> [!NOTE]
>  VSSCI API 的初始版本未提供一种方法，以指示添加的文件的目标项目。 以适应这的语义`lplpFIleNames`参数已增强，从而将它设一个输入/输出参数，而不是输出参数。 如果只指定了单个文件，即指向的值由`lpnFiles`= 1，则第一个元素的`lplpFileNames`包含目标文件夹。 若要使用这些新的语义，IDE 调用`SccSetOption`起作用`nOption`参数设置为`SCC_OPT_SHARESUBPROJ`。 如果源代码管理插件不支持语义，它将返回`SCC_E_OPTNOTSUPPORTED`。 执行使用的是禁用**从源代码管理中的添加**功能。 如果插件支持**从源代码管理中的添加**功能 (`SCC_CAP_ADDFROMSCC`)，则它必须支持新的语义，并返回`SCC_I_SHARESUBPROJOK`。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)