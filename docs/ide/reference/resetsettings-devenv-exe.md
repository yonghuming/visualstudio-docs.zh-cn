---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 08d285b07d775f3e46bb2f5106ff8140d3058f8f
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
还原 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 默认设置并自动启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 可选择将这些设置重置为指定的 .vssettings 文件。  
  
 默认设置由首次启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 时选择的配置文件决定。  
  
## <a name="syntax"></a>语法  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>参数  
 `SettingsFile`  
 .vssettings 文件的完整路径和名称应用于 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 若要还原常规开发设置配置文件，请使用 `General`。  
  
## <a name="remarks"></a>备注  
 如果未指定任何 `SettingsFile`，在下次启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 时，系统将提示选择默认的设置集合。  
  
## <a name="example"></a>示例  
 下面的命令行应用 `MySettings.vssettings` 文件中存储的设置。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>另请参阅  
 [个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
