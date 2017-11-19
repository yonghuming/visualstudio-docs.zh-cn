---
title: "SccGet 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGet
helpviewer_keywords: SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20abad6a195d8493be8849588b86035d03fdc654
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccget-function"></a>SccGet 函数
此函数可检索用于查看和编译但不能用于编辑的一个或多个文件的副本。 在大多数系统中，文件被标记为只读的。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源代码管理插件上下文结构中。  
  
 hWnd  
 [in]它提供了任何对话框，父级可以使用源代码管理插件，则 IDE 窗口的句柄。  
  
 nFiles  
 [in]中指定的文件数`lpFileNames`数组。  
  
 lpFileNames  
 [in]要检索的文件的完全限定名称的数组。  
  
 fOptions  
 [in]命令标志 (`SCC_GET_ALL`， `SCC_GET_RECURSIVE`)。  
  
 pvOptions  
 [in]源代码管理插件特定选项。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|Get 操作成功与否。|  
|SCC_E_FILENOTCONTROLLED|文件不是在源代码管理下。|  
|SCC_E_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC_E_FILEISCHECKEDOUT|无法获取用户当前已签出文件。|  
|SCC_E_ACCESSFAILURE|没有访问源代码管理系统，可能由于网络或争用问题发生时出现问题。 建议重试。|  
|SCC_E_NOSPECIFIEDVERSION|指定了一个无效的版本或日期/时间。|  
|SCC_E_NONSPECIFICERROR|非特定故障;未同步文件。|  
|SCC_I_OPERATIONCANCELED|在完成之前取消操作。|  
|SCC_E_NOTAUTHORIZED|用户无权执行此操作。|  
  
## <a name="remarks"></a>备注  
 计数与要检索的文件的名称的数组调用此函数。 如果 IDE 将标志传递`SCC_GET_ALL`，这意味着，中的项`lpFileNames`不是文件而是目录，并在给定目录中的源代码管理下的所有文件都都要检索。  
  
 `SCC_GET_ALL`标志可以与组合`SCC_GET_RECURSIVE`标志来检索给定目录中的所有文件和以及所有子目录。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`永远不会传递且`SCC_GET_ALL`。 另请注意，是否目录 C:\A 和 C:\A\B 上递归传递 get，C:\A\B 和所有子目录将实际来检索两次。 它是 IDE 的责任-并不是源代码管理插件-若要确保使超出数组保持这样的重复项。  
  
 最后，即使源代码管理插件指定`SCC_CAP_GET_NOUI`上初始化，指示它不具有 Get 命令的用户界面、 通过 IDE 以检索文件仍可能调用此函数的标志。 标志只意味着 IDE 不显示 Get 菜单项，并且，该插件不需要提供任何 UI。  
  
## <a name="renaming-and-sccget"></a>重命名和 SccGet  
 情况： 用户签出文件，例如，a.txt，并对其进行修改。 A.txt 可以签入之前，第二个用户将将 a.txt 重命名为 b.txt 中从源代码管理数据库、 检出 b.txt，然后使某些修改文件，并在此将文件签入。 第一个用户想使第一个用户将其本地版本的 a.txt 文件重命名为 b.txt，并执行 get 对该文件，第二个用户所做的更改。 但是，本地缓存，用于跟踪的版本号仍认为 a.txt 的第一个版本存储在本地，并且因此源代码管理无法解决的差异。  
  
 有两种方法，若要解决这种情况下，本地缓存的源控件版本变得与源代码管理数据库不同步：  
  
1.  不允许重命名当前已签出源代码管理数据库中的文件。  
  
2.  执行"删除旧"跟"添加新项"的等效项。 下面的算法是一种方法来实现此目的。  
  
    1.  调用[SccQueryChanges](../extensibility/sccquerychanges-function.md)若要了解有关重命名为 b.txt 从源代码管理数据库中的 a.txt 的函数。  
  
    2.  将本地 a.txt 重命名为 b.txt。  
  
    3.  调用`SccGet`a.txt 和 b.txt 函数。  
  
    4.  从源代码管理数据库中不存在 a.txt，因为缺少 a.txt 版本信息的清除的本地版本缓存。  
  
    5.  签出该 b.txt 文件与本地 b.txt 文件的内容合并。  
  
    6.  现在可以检查更新的 b.txt 文件。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令使用的位标志](../extensibility/bitflags-used-by-specific-commands.md)