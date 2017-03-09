---
title: "UpdateManifestForBrowserApplication 任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 8
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
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 2a80b4c0ec826a43e768fc4f017c30536bb7c36a
ms.lasthandoff: 02/22/2017

---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication 任务
当生成 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] 项目时，会运行 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> 任务，以将 **\<hostInBrowser />** 元素添加到应用程序清单中 (*projectname*.exe.manifest)。  
  
## <a name="task-parameters"></a>任务参数  
  
|参数|描述|  
|---------------|-----------------|  
|`ApplicationManifest`|必需的 **ITaskItem[]** 参数。<br /><br /> 指定想要将 `<hostInBrowser />` 元素添加到其中的应用程序清单文件的路径和名称。|  
|`HostInBrowser`|所需的 **Boolean** 参数。<br /><br /> 指定是否要修改应用程序清单，以包括 **\<hostInBrowser />** 元素。 如果为 **true**，则一个新 `<`**hostInBrowser />** 元素将包括在 **\<entryPoint />** 元素中。 请注意，元素包含是累计的：如果 **\<hostInBrowser />** 元素已存在，则不会删除或覆盖它。 相反，将创建额外的 **\<hostInBrowser />** 元素。 如果为 **false**，则不会修改应用程序清单。|  
  
## <a name="remarks"></a>备注  
 通过使用 [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] 部署运行 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)]，因此，必须使用支持的部署和应用程序清单进行发布。 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] 使用 [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) 任务来生成应用程序清单。  
  
 然后，若要将应用程序配置为从浏览器中进行管理，则必须将额外的元素 **\<hostInBrowser />** 添加到应用程序清单中，如以下示例所示：  
  
```xml  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 生成 [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] 项目时，将运行 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> 任务，以便添加 `<hostInBrowser />` 元素。  
  
## <a name="example"></a>示例  
 以下示例演示如何确保 `<hostInBrowser />` 元素包括在应用程序清单文件中。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
 [WPF MSBuild 引用](../msbuild/wpf-msbuild-reference.md)   
 [任务参考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [Building a WPF Application (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c) （生成 WPF 应用程序 (WPF)）  
 [WPF XAML Browser Applications Overview](http://msdn.microsoft.com/Library/3a7a86a8-75d5-4898-96b9-73da151e5e16)（WPF XAML 浏览器应用程序概述）
