---
title: "隔离 Shell 入口点参数 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54b15d849efacb681eb8b4238cd067144bc67342
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>独立的 Shell 入口点参数 （c + +）
当一个 Visual Studio shell 基于应用程序启动时，它将调用 Visual Studio shell 的开始入口点。 可以在命令行界面的开始入口点调用中重写以下设置。 有关每个设置的说明，请参阅[。Pkgdef 文件](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   AppName  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Visual Studio Shell 隔离模板创建一个源文件， *solutionName*.cpp，其中*solutionName*是应用程序的解决方案名称。 此文件定义应用程序，_tWinMain 函数的主要入口点。 此函数将调用外壳程序的开始入口点。  
  
 可以通过应用程序启动时更改这些设置来更改应用程序的行为。  
  
## <a name="parameters"></a>参数  
 Visual Studio shell 的开始入口点定义五个参数。 不要更改前四个参数。 第五个参数采用设置替代列表。 从应用程序的主入口点调用外壳程序的开始入口点。  
  
 命令行界面的开始入口点具有以下签名。  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 如果你不想要重写任何应用程序设置，而保留的设置的值覆盖参数为 null 指针。  
  
 若要重写一个或多个设置，传递包含的设置中被重写的 Unicode 字符串。 字符串为以分号分隔名称-值对的列表。 每个对包含该设置将重写，名称跟等号 （=） 跟要应用于设置的值。  
  
> [!NOTE]
>  不包括空白中 Unicode 字符串。  
  
 对于布尔设置，以下字符串表示值 true;所有其他字符串表示值 false。 这些字符串不区分大小写。  
  
-   \+  
  
-   1  
  
-   -1  
  
-   on  
  
-   true  
  
-   是  
  
## <a name="example"></a>示例  
 若要禁用的外接程序，并更改你的应用程序的默认项目位置，可以设置为"AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp"的最后一个参数。  
  
## <a name="see-also"></a>另请参阅  
 [自定义独立的 Shell](customizing-the-isolated-shell.md)   
 [.Pkgdef 文件](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)