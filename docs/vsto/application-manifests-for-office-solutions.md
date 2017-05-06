---
title: "Office 解决方案的应用程序清单"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "应用程序清单 [Visual Studio 中的 Office 开发]"
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Office 解决方案的应用程序清单
  应用程序清单是一个 XML 文件，描述加载到 Microsoft Office 解决方案中的程序集。 Visual Studio 中的 Microsoft Office 开发工具使用 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md) 引用中定义的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 应用程序清单架构。  
  
 Office 解决方案的应用程序清单使用以下 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 元素和特性。  
  
|元素|说明|特性|  
|--------|--------|--------|  
|[&#60;assembly&#62; 元素（ClickOnce 应用程序）](~/deployment/assembly-element-clickonce-application.md)|必需。 顶级元素。|`manifestVersion`|  
|[&#60;assemblyIdentity&#62; 元素（ClickOnce 应用程序）](~/deployment/assemblyidentity-element-clickonce-application.md)|必需。 标识 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 应用程序的主程序集。|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60;trustInfo&#62; 元素（ClickOnce 应用程序）](~/deployment/trustinfo-element-clickonce-application.md)|标识应用程序安全性要求。|无|  
|[&#60;entryPoint&#62; 元素（ClickOnce 应用程序）](~/deployment/entrypoint-element-clickonce-application.md)|必需。 标识用于执行的应用程序代码入口点。|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60;dependency&#62; 元素（ClickOnce 应用程序）](~/deployment/dependency-element-clickonce-application.md)|必需。 标识应用程序运行所需的每个依赖项。 （可选）标识需要进行预安装的程序集。|无|  
|[&#60;file&#62; 元素（ClickOnce 应用程序）](http://msdn.microsoft.com/library/56e3490c-eed5-4841-b1bf-eefe778b6ac9)|必需。 标识应用程序使用的每个非程序集文件。 可以包括与文件关联的组件对象模型 \(COM\) 隔离数据。|`name`<br /><br /> `size`|  
  
 Office 解决方案的应用程序清单具有 `co.v1` 命名空间中的以下元素。  
  
```  
<entryPoint> <co.v1:customHostSpecified /> </entryPoint>   
```  
  
 这些应用程序清单还具有 `vstav3` 命名空间中的以下元素和特性。  
  
```  
<addIn> <entryPointsCollection> <entryPoints> <entryPoint> </entryPoint> </entryPoints> </entryPointsCollection> <update></update> <postActions> <postAction> <postActionData> </postActionData> <postAction> </postActions> <application> <customizations> <customization> </customization> </customizations> </application </addIn>  
```  
  
|元素|说明|特性|  
|--------|--------|--------|  
|[&#60;customHostSpecified&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|必需。 将清单专门标记为 Office 解决方案。|无|  
|[&#60;addin&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/addin-element-office-development-in-visual-studio.md)|必需。 将入口点存储到单个命名空间。|无|  
|[&#60;entryPointsCollection&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|必需。 针对一个或多个 Office 解决方案对所有程序集进行分组。|`id`|  
|[&#60;entryPoints&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/entrypoints-element-office-development-in-visual-studio.md)|必需。 对要运行 Office 解决方案的所有程序集进行分组。|无|  
|[&#60;entryPoint&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/entrypoint-element-office-development-in-visual-studio.md)|必需。 标识要在 Office 解决方案中运行的程序集。|`class`<br /><br /> `contract`|  
|[&#60;update&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/update-element-office-development-in-visual-studio.md)|必需。 配置解决方案的更新。|`enabled`<br /><br /> `expiration`|  
|[&#60;postActions&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/postactions-element-office-development-in-visual-studio.md)|可选。 对在 Office 解决方案安装后运行的部署后操作进行分组。|无|  
|[&#60;postAction&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/postaction-element-office-development-in-visual-studio.md)|可选。 标识部署后操作。|无|  
|[&#60;postActionData&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/postactiondata-element-office-development-in-visual-studio.md)|可选。 配置部署后操作的数据。|无|  
|[&#60;application&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/application-element-office-development-in-visual-studio.md)|必需。 将特定于应用程序的信息包装到单个节点内。|无|  
|[&#60;customizations&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/customizations-element-office-development-in-visual-studio.md)|必需。 将所有的应用程序特定于宿主的信息存储在单独的命名空间内。|无|  
|[&#60;customization&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/customization-element-office-development-in-visual-studio.md)|必需。 将应用程序特定于宿主的信息存储在单独的命名空间内。|`xmlns`|  
|[&#60;document&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/document-element-office-development-in-visual-studio.md)|仅针对文档级解决方案为必需。 存储特定于自定义的信息。|`solutionId`|  
|[&#60;appAddin&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/appaddin-element-office-development-in-visual-studio.md)|仅针对应用程序级解决方案为必需。 存储特定于自定义的信息。|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60;friendlyName&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/friendlyname-element-office-development-in-visual-studio.md)|可选。 存储显示在已安装的 VSTO 外接程序的列表中的 VSTO 外接程序的名称。|无|  
|[&#60;description&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/description-element-office-development-in-visual-studio.md)|仅针对 VSTO 外接程序为必需。 存储在已安装的程序的列表中出现的描述。|无|  
|[&#60;formRegions&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/formregions-element-office-development-in-visual-studio.md)|仅为包含窗体区域的 Outlook VSTO 外接程序所需。|无|  
|[&#60;formRegion&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/formregion-element-office-development-in-visual-studio.md)|仅为包含窗体区域的 Outlook VSTO 外接程序所需。|`Name`|  
|[&#60;vstoRuntime&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|必需。 介绍 Office 解决方案支持的特定版本的 Visual Studio Tools for Office Runtime。|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## 备注  
 可以在 Office 解决方案中手动编辑应用程序和部署清单。 此后，必须通过使用清单生成和编辑工具 \(mage.exe 和 mageui.exe\) 对应用程序和部署清单重新签名。 有关详细信息，请参阅[如何：为应用程序和部署清单重新签名](~/deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## 文件位置  
 应用程序清单特定于单一版本的解决方案。 为此，应用程序清单应与部署清单分开存储。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将特定于版本的文件放置在一个子目录中，该子目录以发布文件夹中**应用程序文件**子目录中的关联版本命名。  
  
## 文件名语法  
 应用程序清单文件的名称应为应用程序的完整名称和扩展名，如 `assemblyIdentity` 元素中所标识的那样，后跟 extension.manifest。 例如，引用 OutlookAddIn1.dll 自定义的应用程序清单将使用以下文件名语法。  
  
 `OutlookAddIn1.dll.manifest`  
  
## 请参阅  
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  