---
title: "将目录添加到新建项目对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f24fd3c3a0ffb537c63346ef867a2a43481acfa9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>将目录添加到新建项目对话框
在创建新项目类型时，你还可以注册中的新目录**新项目**对话框以显示它们用于作为模板。 下面的代码示例说明如何注册一个新目录，也称为一个节点。 在示例中，注册 VSPackage CLSID_Package 所公开的模板。 因此，左侧**新项目**对话框添加的节点中，提供与由 Folder_Label_ResID 资源的名称。 从 VSPackage 附属 DLL 加载此资源。  
  
 **文件夹**值代表该 Folder_Label_ResID 节点是否显示在其下的文件夹的 GUID。 在示例中，GUID 表示**其他项目**文件夹中的**项目类型**窗格**新项目**对话框。 如果**其他项目**值不存在，则标签将定位在顶级。  
  
 TemplatesDir 值指定包含的项目模板的目录的完整路径。 这些文件可以是.vsz 文件或要克隆的典型的模板文件。  
  
 如果指定 TemplatesLocalizedSubDir，它必须命名 TemplatesDir 包含本地化的模板的子目录的字符串的资源 ID。 因为[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]加载字符串资源从附属 DLL 如果你有一个，每个附属 DLL 可以包含不同的子目录的名称。 SortPriority 值指定排序的优先级。  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [将目录添加到“添加新项”对话框](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)