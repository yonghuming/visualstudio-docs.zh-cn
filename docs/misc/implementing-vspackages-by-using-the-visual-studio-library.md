---
title: "使用 Visual Studio 库实现 VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 库, 实现 Vspackage"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# 使用 Visual Studio 库实现 VSPackage
`IVsPackageImpl` 类在 Visual Studio 库中提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 接口的一个最小实现。  `IVsPackageImpl` 负责大多数 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>维护方法。  可能需要重写提供了一个有意义的实现的其他方法包括:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包模板生成讨论的所有代码示。  可以节省时间使用模板生成您的 VSPackage。  
  
 通常实现使用 Visual Studio 库的包继承 ATL 的 [CComObjectRootEx Class](/visual-cpp/atl/reference/ccomobjectrootex-class) 和 [CComCoClass Class](/visual-cpp/atl/reference/ccomcoclass-class) 和 Visual Studio 库的 IVsPackageImpl 的 VSPackage 类。  例如，下面是从 Reference.Package 示例的 VSPackage 类声明:  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 显示的 `IVsPackageImpl` 模板参数是一些类和指向标识 VSPackage 的 GUID。  
  
## 支持与 COM 映射的 QI  
 获取添加 ATL 支持 `QueryInterface`支持，其 COM 映射必须列表该类实现的接口。  例如，下面是一些类的 COM 映射。 Reference.Package 示例:  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 有关 COM 映射的更多信息，请参见 [Implementing CComObjectRootEx](/visual-cpp/atl/implementing-ccomobjectrootex) 和 [COM\_INTERFACE\_ENTRY Macros](../Topic/COM_INTERFACE_ENTRY%20Macros.md)。  
  
## 支持使用注册表映射注册  
 Visual Studio 库使用 ATL 样式 .RGS 文件支持 COM 对象的注册。  若要支持在 .RGS 文件的标记替换， Visual Studio 库使用注册表映射。  注册表映射列出要替换的符号并支持使用字符串表资源的 ID。  
  
 例如，下面是一些类的注册表映射。 Reference.Package 示例:  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## 请参阅  
 [VSSDK 示例](../misc/vssdk-samples.md)