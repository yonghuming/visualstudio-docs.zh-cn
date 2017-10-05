---
title: "SccDiff 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
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
ms.openlocfilehash: de66dd1f5bb36ac60c145d481f4d46722dc1ca59
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="sccdiff-function"></a>SccDiff 函数
此函数显示 （或 （可选） 只需检查） 控制系统的源中 （在本地磁盘） 上的当前文件和其最近的签入版本之间的差异。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 lpFileName  
 [in]为其请求差异文件的名称。  
  
 fOptions  
 [in]命令标志。 有关详细信息，请参阅备注。  
  
 pvOptions  
 [in]源代码管理插件特定选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|正在使用复制和服务器版本是相同的。|  
|SCC_I_FILESDIFFERS|工作副本不同在源代码管理下的版本。|  
|SCC_I_RELOADFILE|需要重新加载文件或项目。|  
|SCC_E_FILENOTCONTROLLED|文件不是在源代码管理下。|  
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NONSPECIFICERROR|非特定故障;无法获得文件差异。|  
|SCC_E_FILENOTEXIST|找不到本地文件。|  
  
## <a name="remarks"></a>备注  
 此函数有两个不同的用途。 默认情况下，它为文件显示更改的列表。 源代码管理插件将自己的窗口，打开任何格式选择，则显示磁盘上的用户的文件和源代码管理下的文件的最新版本之间的差异。  
  
 或者，IDE 可能只需确定文件是否已更改。 例如，IDE 可能需要确定它是否可以安全地签出文件，而不通知用户。 在这种情况下，IDE 传入`SCC_DIFF_CONTENTS`标志。 源代码管理插件必须检查磁盘，逐字节，针对受源代码管理文件上的文件，并返回一个值，该值指示两个文件是否不同而不向用户显示任何内容。  
  
 作为一种性能优化，源代码管理插件可能会使用基于校验和或而不是逐字节比较的所要求的时间戳的替代方法`SCC_DIFF_CONTENTS`： 这些形式的比较是显然更快，但可靠性较低。 并非所有的源代码管理系统可能支持这些备用比较方法，并且该插件可能具有为回退到内容比较。 所有源控件插件，至少必须都支持的内容比较。  
  
> [!NOTE]
>  快速差异标志是互斥的。 它是有效不传递任何标志，但不是有效同时传递多个。 `SCC_DIFF_QUICK_DIFF`这将合并所有标志掩码可以用于测试，但永远不应作为参数传递。  
  
|`fOption`|含义|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|（可能使用的快速或视觉对象的差异） 的不区分大小写比较。|  
|SCC_DIFF_IGNORESPACE|将忽略 （可能使用的快速或视觉对象的差异） 的空白区域。|  
|SCC_DIFF_QD_CONTENTS|以无提示方式将该文件，逐字节进行比较。|  
|SCC_DIFF_QD_CHECKSUM|以无提示方式比较通过校验和时支持的文件。 如果不支持，回退到内容的比较。|  
|SCC_DIFF_QD_TIME|以无提示方式将通过其时间戳时支持的文件进行比较。 如果不支持，回退到内容的比较。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)
