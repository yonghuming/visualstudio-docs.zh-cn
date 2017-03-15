---
title: "独立 Shell 入口点参数 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 10
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 13f05a147f0d9ab36d49b93cc91bcbaa7b002c70
ms.lasthandoff: 02/22/2017

---
# <a name="isolated-shell-entry-point-parameters-c"></a>独立的 Shell 入口点参数 （c + +）
Visual Studio 基于 shell 的应用程序启动时，它将调用 Visual Studio shell 的开始入口点。 可以在对外壳中的开始入口点的调用中重写以下设置。 每个设置的说明，请参阅[。Pkgdef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   应用程序名  
  
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
  
 Visual Studio Shell 独立模板创建一个源文件， *solutionName*.cpp，其中*solutionName*是应用程序的解决方案名称。 此文件定义应用程序，_tWinMain 函数的主入口点。 此函数将调用外壳中的开始入口点。  
  
 通过更改这些设置应用程序启动时，可以更改该应用程序的行为。  
  
## <a name="parameters"></a>参数  
 Visual Studio shell 的开始入口点定义五个参数。 不要更改前四个参数。 第五个参数将设置重写列表。 外壳中的开始入口点，从应用程序的主入口点调用。  
  
 外壳中的开始入口点具有以下签名。  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 如果不希望重写任何应用程序设置，而保留的设置的值覆盖参数为 null 指针。  
  
 若要覆盖一个或多个设置，请传递一个 Unicode 字符串，包含要被重写的设置。 字符串为名称 / 值对之间用分号分隔的列表。 每个对包含跟有等号 （=）、 要应用于的设置的值后跟要重写，请设置的名称。  
  
> [!NOTE]
>  Unicode 字符串中不包含空格。  
  
 对于布尔设置，下面的字符串表示值 true;所有其他字符串表示值 false。 这些字符串不区分大小写。  
  
-   \+  
  
-   1  
  
-   -1  
  
-   on  
  
-   true  
  
-   是  
  
## <a name="example"></a>示例  
 若要禁用加载项和更改您的应用程序的默认项目位置，可以设置为"AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp"的最后一个参数。  
  
## <a name="see-also"></a>另请参阅  
 [自定义独立的 Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgdef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
