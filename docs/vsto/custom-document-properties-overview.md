---
title: "自定义文档属性概述 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ee19d6fd6bd84f344a205b0e508abbede63cdebb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="custom-document-properties-overview"></a>Custom Document Properties Overview
  当生成文档级项目时，Visual Studio 会将两个自定义属性添加到项目中的文档： _AssemblyLocation 和 _AssemblyName。 当用户打开的文档时，Microsoft Office 应用程序将检查这些自定义文档属性。 如果它们存在文档中，应用程序加载[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，以启动自定义项。 有关详细信息，请参阅[体系结构的 Office 解决方案中 Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="assemblyname"></a>_AssemblyName  
 此属性包含中的 Office 解决方案加载程序组件的接口的 CLSID [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 CLSID 值为 4E3C66D5-58 D 4-491E-A7D4-64AF99AF6E8B。 你应该永不更改此值。  
  
## <a name="assemblylocation"></a>_AssemblyLocation  
 此属性包含的自定义项中提供有关部署清单的详细信息的字符串。 有关清单的详细信息，请参阅[应用程序和部署清单在 Office 解决方案中](../vsto/application-and-deployment-manifests-in-office-solutions.md)。  
  
 The_AssemblyLocation 属性值可以具有不同的格式，具体取决于解决方案的部署方式：  
  
-   如果已发布解决方案，安装从 Web 站点、 UNC 路径或 CD 或 USB 驱动器，_AssemblyLocation 属性具有格式*部署清单路径*|*解决方案 Id*。 以下字符串是一个示例：  
  
     file://deployserver/MyShare/ExcelWorkbook1.vsto | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9  
  
-   如果你正在运行或调试从 Visual Studio 解决方案，_AssemblyLocation 属性具有格式*DeploymentManifestName*|*解决方案 Id*| vstolocal。 以下字符串是一个示例：  
  
     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal  
  
 *解决方案 Id*是一个 GUID，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]用于标识解决方案。 *解决方案 Id*生成项目时自动生成。 **Vstolocal**术语指示到[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，程序集应加载从文档所在的文件夹。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 中的 Office 解决方案的体系结构](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)   
 [应用程序和 Office 解决方案中的部署清单](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [如何： 使用 ClickOnce 发布 Office 解决方案](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [如何：创建和修改自定义文档属性](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  