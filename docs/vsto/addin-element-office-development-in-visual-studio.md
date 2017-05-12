---
title: "&lt;addin&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<addIn> 元素"
  - "addin 元素"
  - "<addin> 元素"
ms.assetid: 4abec4c3-8c7c-4b2b-9128-79fa4e863281
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;addin&gt; 元素（Visual Studio 中的 Office 开发）
  `vstav3`  命名空间的 `addin` 元素包含特定于使用 Visual Studio 开发的 Microsoft Office VSTO 外接程序和文档级自定义项的信息。  
  
## 语法  
  
```  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  
  
## 元素和属性  
 `vstav3`  命名空间的 `addin` 元素包含有关 Office 解决方案和 Microsoft Office 应用程序的信息。 此元素必须在以下命名空间中：`vstav3=urn:schemas-microsoft-com:vsta.v3`。 子元素也必须在此命名空间中。  
  
 `addin` 元素没有属性。  
  
 `addin` 元素具有以下子元素。  
  
### entryPoints  
 必需。[&#60;entryPoints&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/entrypoints-element-office-development-in-visual-studio.md) 中对 `entryPoints` 元素进行了描述。  
  
### 更新  
 必需。[&#60;update&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/update-element-office-development-in-visual-studio.md) 中对 `update` 元素进行了描述。  
  
### postActions  
 可选。[&#60;postActions&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/postactions-element-office-development-in-visual-studio.md) 中对 `postActions` 元素进行了描述。  
  
### 应用程序  
 必需。[&#60;application&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/application-element-office-development-in-visual-studio.md) 中对 `application` 元素进行了描述。  
  
## 文档级自定义项示例  
  
### 描述  
 下面的代码示例演示使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的文档级 Office 解决方案中的 `addin` 元素。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## VSTO 外接程序示例  
  
### 描述  
 下面的代码示例演示使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的应用程序级 Office 解决方案中的 `addin` 元素。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  