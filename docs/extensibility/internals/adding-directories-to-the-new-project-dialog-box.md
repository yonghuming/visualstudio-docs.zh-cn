---
title: "将目录添加到新建项目对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新项目对话框中，扩展"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 将目录添加到新建项目对话框
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在创建新的项目类型时，可以注册在同时显示其 **新项目** 对话框的新内容用作模板。  下面的代码示例说明如何注册新的内容，也称为一个节点。  在此示例中， VSPackage 显示的模板 CLSID\_Package 注册。  因此，提供添加的节点，将名称 Folder\_Label\_ResID 资源取决于 **新项目** 对话框的左侧。  此资源从 VSPackage 附属 DLL 被加载。  
  
 **文件夹** 值表示下 Folder\_Label\_ResID 节点显示文件夹的 GUID。  在此示例中， GUID 表示在 **新项目** 对话框的 **项目类型** 窗格的 **其他项目** 文件夹。  如果 **其他项目** 值存在，标签确定在最高级别。  
  
 TemplatesDir 值指定包含项目模板目录的完整路径。  这些文件可能是 .vsz 文件或将克隆的典型的模板文件。  
  
 如果指定 TemplatesLocalizedSubDir，它必须是命名 TemplatesDir 子目录保存本地化的模板字符串的资源 ID。  由于 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 从附属 DLL 加载字符串资源，如果具有，每个附属 DLL 可以包含一个不同的子目录名称。 SortPriority 值指定排序的优先级。  
  
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
  
## 请参阅  
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [添加目录更改为添加新项对话框](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)