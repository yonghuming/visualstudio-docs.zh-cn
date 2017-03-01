---
title: "注册的单文件生成器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 239f68b8bdbaf910f25b9fbe6e0fdd7061fe0f16
ms.lasthandoff: 02/22/2017

---
# <a name="registering-single-file-generators"></a>注册的单文件生成器
要使自定义工具中可用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，因此必须注册该[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以实例化并将其与特定项目类型。  
  
### <a name="to-register-a-custom-tool"></a>若要注册自定义工具  
  
1.  可以注册的自定义工具 DLL 中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本地注册表中或在系统注册表中，在 HKEY_CLASSES_ROOT 下。  
  
     例如，下面是托管 MSDataSetGenerator 自定义工具，该工具附带的注册信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  创建一个注册表项中的所需[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下生成器配置单元\\*GUID*其中*GUID*由特定语言项目系统或服务定义 GUID。 密钥的名称将成为您的自定义工具的编程名称。 该自定义工具注册表项具有以下值︰  
  
    -   (默认)  
  
         可选。 提供自定义工具的用户友好说明。 此参数是可选的但建议这样做。  
  
    -   CLSID  
  
         必需。 指定的 COM 组件的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>类库的标识符  
  
    -   GeneratesDesignTimeSource  
  
         必需。 指示是否从由该自定义工具生成的文件类型可供可视化设计器。 此参数值必须为 （零） 为 0 到可视化设计器不可用的类型或类型可供可视化设计器 （一个） 1。  
  
    > [!NOTE]
    >  您必须注册所需的自定义工具，可为其每种语言单独的自定义工具。  
  
     例如，MSDataSetGenerator 将自身注册一次为每种语言︰  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [实现单文件生成器](../../extensibility/internals/implementing-single-file-generators.md)   
 [确定项目的默认 Namespace](../../misc/determining-the-default-namespace-of-a-project.md)   
 [公开到可视化设计器的类型](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager 对象介绍](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
