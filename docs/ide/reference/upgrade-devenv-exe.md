---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
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
ms.openlocfilehash: 1e8f81e61121fd6779cc0f0ebdbd166bf0c27c6f
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
将解决方案文件及其所有项目文件或指定的项目文件更新为这些文件的当前 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 格式。  
  
## <a name="syntax"></a>语法  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>参数  
 `SolutionFile`  
 如果要升级整个解决方案及其项目，则是必需的。 解决方案文件的路径和名称。 可以只输入解决方案文件的名称，也可以输入解决方案文件的完整路径和名称。 如果命名的文件夹或文件尚不存在，将创建该文件夹或文件。  
  
 `ProjectFile`  
 如果要升级单个项目，则是必需的。 解决方案中项目文件的路径和名称。 可以只输入项目文件的名称，也可以输入项目文件的完整路径和名称。 如果命名的文件夹或文件尚不存在，将创建该文件夹或文件。  
  
## <a name="remarks"></a>备注  
 备份文件自动创建并复制到一个名为 Backup 的目录中，该目录是在当前目录中创建的。  
  
 要升级源代码控制的解决方案或项目，必须先将其签出。  
  
 使用 `/upgrade` 开关不会启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 可在解决方案或项目的开发语言的“升级报告”中看到升级结果。 不会返回任何错误或使用情况信息。 有关在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中升级项目的详细信息，请参阅[移植、迁移和升级 Visual Studio 项目](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)。  
  
## <a name="example"></a>示例  
 此示例升级 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 解决方案的默认文件夹中名为“MyProject.sln”的解决方案文件。  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>另请参阅  
 [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
