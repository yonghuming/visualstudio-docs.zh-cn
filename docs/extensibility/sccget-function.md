---
title: "SccGet 函数 | Microsoft Docs"
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
  - "SccGet"
helpviewer_keywords: 
  - "SccGet 函数"
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGet 函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函数可检索一个或多个文件用于查看和编译但不能用于编辑的副本。 在大多数系统中，则文件被标记为只读。  
  
## 语法  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 参数  
 pvContext  
 \[\] in源代码管理插件上下文结构中。  
  
 hWnd  
 \[\] in源代码管理插件可以用作所有对话框，它提供了一个父 IDE 窗口的句柄。  
  
 nFiles  
 \[\] in中指定的文件数 `lpFileNames` 数组。  
  
 lpFileNames  
 \[\] in要检索的文件的完全限定名称的数组。  
  
 选项  
 \[\] in命令标志 \(`SCC_GET_ALL`, ，`SCC_GET_RECURSIVE`\)。  
  
 pvOptions  
 \[\] in源代码管理插件特定选项。  
  
## 返回值  
 此函数的源代码控制插件实现应返回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|获取操作的成功。|  
|SCC\_E\_FILENOTCONTROLLED|文件不是源代码管理下。|  
|SCC\_E\_OPNOTSUPPORTED|源代码管理系统不支持此操作。|  
|SCC\_E\_FILEISCHECKEDOUT|无法获取当前用户已签出文件。|  
|SCC\_E\_ACCESSFAILURE|没有访问源代码管理系统，很可能是由于网络或争用问题时出现问题。 建议重试。|  
|SCC\_E\_NOSPECIFIEDVERSION|指定了一个无效的版本或日期\/时间。|  
|SCC\_E\_NONSPECIFICERROR|模糊失败;不同步文件。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前取消操作。|  
|SCC\_E\_NOTAUTHORIZED|用户无权执行此操作。|  
  
## 备注  
 此函数调用计数、 要检索的文件的名称的数组。 如果 IDE 传递了标志 `SCC_GET_ALL`, ，这意味着，中的项 `lpFileNames` 不是文件而是目录，并在给定目录中的源代码管理下的所有文件都都要从中检索。  
  
 `SCC_GET_ALL` 可以与组合标志 `SCC_GET_RECURSIVE` 标志来检索给定目录中的所有文件和以及所有子目录。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` 永远不会传递而比不 `SCC_GET_ALL`。 另请注意，是否目录 C:\\A 和 C:\\A\\B，同时传递递归获得 C:\\A\\B 及其所有的子目录将实际检索两次。 IDE 的责任 — 并不是源控制即插即用中的\-\-若要确保使从数组保持这样的重复项。  
  
 最后，即使源代码管理插件指定 `SCC_CAP_GET_NOUI` 上初始化，表示它没有 Get 命令的用户界面，仍可以通过 IDE 以检索文件调用此函数的标志。 该标志只是意味着 IDE 不显示 Get 菜单项，并且，该插件不需要提供任何用户界面。  
  
## 重命名和 SccGet  
 情况: 用户签出文件，例如，a.txt，并对其进行修改。 A.txt 才能签入之前，第二个用户将将 a.txt 重命名为 b.txt 在源代码管理数据库中、 检出 b.txt，然后使某些修改文件，并在此签入该文件。 第一个用户想要使第一个用户将其本地版本的 a.txt 文件重命名为 b.txt 并获取对该文件，第二个用户所做的更改。 但是，本地缓存，用于跟踪的版本号仍认为 a.txt 的第一个版本存储在本地并因此源代码管理不能解决的差异。  
  
 有两种方法可以解决这种情况下，源控件版本的本地缓存变得与源代码管理数据库不同步:  
  
1.  不允许重命名当前已签出源代码管理数据库中的文件。  
  
2.  执行操作"删除旧"后跟"添加新项"的等效项。 下面的算法是一种方法实现此目的。  
  
    1.  调用 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 函数可了解如何重命名为 b.txt 在源代码管理数据库中的 a.txt。  
  
    2.  将本地 a.txt 重命名为 b.txt。  
  
    3.  调用 `SccGet` a.txt 和 b.txt 函数。  
  
    4.  因为 a.txt 源代码管理数据库中不存在，本地版本缓存缺失 a.txt 版本信息的清除。  
  
    5.  签出该 b.txt 文件合并在一起本地 b.txt 文件的内容。  
  
    6.  更新的 b.txt 文件现在可以签入。  
  
## 请参阅  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md)