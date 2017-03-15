---
title: "替换字符串中使用。Pkgdef 和。Pkgundef 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
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
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>替换字符串中使用。Pkgdef 和。Pkgundef 文件
可以使用下面.pkgdef 中列出的替换字符串和.pkgundef 文件为您的 Visual Studio 定义隔离外壳应用程序。  
  
## <a name="substitution-strings"></a>替换字符串  
  
|字符串|描述|  
|------------|-----------------|  
|$=*RegistryEntry*$|值*RegistryEntry*条目。 如果注册表条目字符串以反斜杠结尾 (\\)，则使用默认值的注册表子项。 例如，替换字符串 $= 的 HKEY_CURRENT_USER\Environment\TEMP$ 会扩展为当前用户的临时文件夹。|  
|$AppName $|传递给 AppEnv.dll 入口点应用程序的限定的名称。 限定的名组成的应用程序名称、 下划线和也记录为项目.pkgdef 文件中的 ThisVersionDTECLSID 设置的值的应用程序自动化对象的类标识符 (CLSID)。|  
|$AppDataLocalFolder|为此应用程序 %LOCALAPPDATA%下的子文件夹。|  
|$BaseInstallDir $|Visual Studio 已安装的位置的完整路径。|  
|$CommonFiles $|%Commonprogramfiles%环境变量的值。|  
|$MyDocuments $|当前用户的我的文档文件夹的完整路径。|  
|$PackageFolder $|包含应用程序的包的程序集文件的目录完整路径。|  
|$ProgramFiles $|%Programfiles%环境变量的值。|  
|$RootFolder $|应用程序的根目录完整路径。|  
|$RootKey $|应用程序的的根注册表项。 默认根位于 HKEY_CURRENT_USER\Software\\*CompanyName*\\*p o j*\\*VersionNumber* （时运行该应用程序，_Config 将追加到此密钥）。 设置中的 RegistryRoot 值*SolutionName*.pkgdef 文件。<br /><br /> $RootKey$ 字符串可用于检索子项下的应用程序的注册表值。 例如，字符串"$= $RootKey$ \AppIcon$"将返回在应用程序根子项下 AppIcon 条目的值。<br /><br /> 分析器顺序，处理.pkgdef 文件，并且可以访问应用程序子项下的注册表项，仅当条目之前已定义|  
|$ShellFolder $|Visual Studio 已安装的位置的完整路径。|  
|$System $|Windows\system32 文件夹中。|  
|$WINDIR $|Windows 文件夹中。|  
  
 如果分析器不能识别的替换字符串，或它无法确定注册表项或环境变量的值，然后它不执行替换的字符串的该部分上。
