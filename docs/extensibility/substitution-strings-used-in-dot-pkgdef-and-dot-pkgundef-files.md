---
redirect_url: shell/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files
title: "在中使用的替换字符串。Pkgdef 和。Pkgundef 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 220e6d9bb9d360a51f9a83b5d0b4420cf64aef91
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>在中使用的替换字符串。Pkgdef 和。Pkgundef 文件
你可以使用在.pkgdef 下面列出的替换字符串和.pkgundef 文件定义 for Visual Studio 独立 shell 应用程序。  
  
## <a name="substitution-strings"></a>替换字符串  
  
|字符串|描述|  
|------------|-----------------|  
|$=*RegistryEntry*$|值*RegistryEntry*条目。 如果注册表条目字符串以反斜杠结尾 (\\)，则使用默认值的注册表子项。 例如，替换字符串 $= 的 HKEY_CURRENT_USER\Environment\TEMP$ 为扩展到当前用户的临时文件夹。|  
|$AppName $|传递给 AppEnv.dll 入口点应用程序的限定的名称。 限定的名称由应用程序名称、 下划线和也记录为项目.pkgdef 文件中的 ThisVersionDTECLSID 设置的值的应用程序自动化对象的类标识符 (CLSID) 组成。|  
|$AppDataLocalFolder|为此应用程序 %LOCALAPPDATA%下的子文件夹。|  
|$BaseInstallDir $|安装 Visual Studio 的位置的位置的完整路径。|  
|$CommonFiles $|%Commonprogramfiles%环境变量的值。|  
|$MyDocuments $|当前用户的我的文档文件夹的完整路径。|  
|$PackageFolder $|包含应用程序的包的程序集文件的目录完整路径。|  
|$ProgramFiles $|%Programfiles%环境变量的值。|  
|$RootFolder $|应用程序的根目录完整路径。|  
|$RootKey $|应用程序根注册表项。 默认情况下的根处于 HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* （时运行该应用程序，则 _Config 追加到此密钥）。 设置中的 RegistryRoot 值*SolutionName*.pkgdef 文件。<br /><br /> $RootKey$ 字符串可以用于检索应用程序子项下的注册表值。 例如，字符串"$= $RootKey$ \AppIcon$"将返回在应用程序根子项的下方 AppIcon 条目的值。<br /><br /> 分析器按顺序处理.pkgdef 文件，并仅当以前定义过条目时，才可以访问的应用程序子项下的注册表项|  
|$ShellFolder $|安装 Visual Studio 的位置的位置的完整路径。|  
|$System $|Windows\system32 文件夹中。|  
|$WINDIR $|Windows 文件夹中。|  
  
 如果分析器无法识别的替换字符串，或它不能确定注册表项或环境变量的值，然后它不执行替换的字符串的该部分。