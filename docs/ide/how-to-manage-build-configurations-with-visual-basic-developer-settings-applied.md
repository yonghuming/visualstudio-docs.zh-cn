---
title: "如何：在应用 Visual Basic 开发人员设置后管理生成配置 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
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
ms.openlocfilehash: 782d860d94cd9e7d4967076a5ea0d3fe86b29400
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>如何：在应用 Visual Basic 开发人员设置后管理生成配置
默认情况下，应用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 开发人员设置后，所有高级生成配置选项都将隐藏。 本主题说明如何手动启用这些设置。  
  
## <a name="enabling-advanced-build-configurations"></a>启用高级生成配置  
 默认情况下，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 开发人员设置将隐藏用于打开“Configuration Manager”对话框以及[项目设计器中](..//ide/reference/application-page-project-designer-visual-basic.md)的“配置”和“平台”列表的选项。  
  
#### <a name="to-enable-advanced-build-configurations"></a>启用高级生成配置  
  
1.  在 **“工具”** 菜单上，单击 **“选项”**。  
  
2.  展开“项目和解决方案”并单击“常规”。  
  
    > [!NOTE]
    >  即使未选中“显示所有设置”选项，“常规”节点也仍然可见。 如果要查看每个可用选项，请单击“显示所有设置”。  
  
3.  单击“显示高级生成配置”。  
  
4.  单击“确定”。  
  
     现在可在“生成”菜单上使用“Configuration Manager”，并且“项目设计器”上会显示“配置”和“平台”列表。  
  
## <a name="see-also"></a>另请参阅  
 [了解生成配置](../ide/understanding-build-configurations.md)   
 [编译和生成](../ide/compiling-and-building-in-visual-studio.md)
