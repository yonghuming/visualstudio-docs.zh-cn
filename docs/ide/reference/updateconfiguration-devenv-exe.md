---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 6e74ef38969cb62790629b34041ceef535ff6f9e
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
通知 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 合并系统上的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包，并检查 MEF 缓存中是否有任何更改。  
  
## <a name="syntax"></a>语法  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>备注  
 安装 VSIX 包时，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 会自动运行此命令。 应在修补文件后运行 `devenv.exe /updateconfiguration`，以便 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 更新 MEF 缓存。 这样便于评估是否进行了适当的修补。  
  
## <a name="example"></a>示例  
 以下命令行会使 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 合并系统上的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包，并检查 MEF 缓存中是否有任何更改。  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>另请参阅  
 [个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
