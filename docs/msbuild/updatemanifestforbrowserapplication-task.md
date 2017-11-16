---
title: "UpdateManifestForBrowserApplication 任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
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
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 24430b3cfa74724dc8fc6ca3d92e5507c3f13514
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication 任务
生成 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] 项目时，运行 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> 任务，以将 \<hostInBrowser /> 元素添加到应用程序清单中 (projectname.exe.manifest)。  
  
## <a name="task-parameters"></a>任务参数  
  
|参数|说明|  
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
  
 当生成 [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] 项目时，将运行 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> 任务，以添加 `<hostInBrowser />` 元素。  
  
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
 [Building a WPF Application (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) （生成 WPF 应用程序 (WPF)）  
 [WPF XAML Browser Applications Overview](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)（WPF XAML 浏览器应用程序概述）