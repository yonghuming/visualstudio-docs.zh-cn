---
title: "“选项”对话框 ->“环境”->“自动恢复”| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
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
ms.openlocfilehash: 320b31b01237656be157be9ad9ce5787521215db
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="autorecover-environment-options-dialog-box"></a>“选项”对话框 ->“环境”->“自动恢复”
使用选项对话框中的此页可指定是否自动备份文件。 使用此页，还可指定当集成开发环境 (IDE) 意外关闭时是否还原已修改的文件。 要访问此对话框，请依次选择“工具”菜单->“选项”->“环境”文件夹->“自动恢复”页。 如果此页未出现在列表中，请在“选项”对话框中选择“显示所有设置”。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在“工具”菜单上选择“导入和导出设置”。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  
  
 **保存自动恢复信息的时间间隔: \<n> 分钟**  
 使用此选项可以自定义在编辑器中自动保存文件的频率。 对于以前保存的文件，文件的副本保存在 \\...\My Documents\Visual Studio \<版本>\Backup Files\\<项目名称>。 如果是新文件且尚未手动保存，则将使用一个随机生成的文件名自动保存该文件。  
  
 **保留自动恢复信息的天数: \<n> 天**  
 使用此选项可指定 Visual Studio 将为自动恢复创建的文件保留多长时间。  
  
## <a name="see-also"></a>另请参阅  
 [“选项”对话框](../../ide/reference/options-dialog-box-visual-studio.md)
