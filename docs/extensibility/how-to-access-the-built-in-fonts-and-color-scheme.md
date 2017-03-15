---
title: "如何︰ 访问内置字体和配色方案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "访问内置的字体"
  - "字体和颜色控件 [Visual Studio SDK] 类别"
  - "访问内置方案的颜色"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何︰ 访问内置字体和配色方案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 集成的开发环境 \(IDE\) 具有与编辑器窗口相关联的字体和颜色方案。 您可以访问通过这种方案 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 接口。  
  
 若要使用的内置字体和颜色方案，VSPackage 必须︰  
  
-   定义要用于默认字体和颜色服务类别。  
  
-   默认字体和颜色服务器注册该类别。  
  
-   告知 IDE 特定窗口通过使用内置的显示项和类别 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` 和 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 接口。  
  
 IDE 窗口的句柄作为使用生成类别。 该类别的名称显示在 **显示其设置︰** 下拉列表框中的 **字体和颜色** 属性页。  
  
### 若要定义使用内置的字体和颜色的类别  
  
1.  创建一个任意的 GUID。  
  
     此 GUID 用于唯一标识某一类别**。**IDE 的默认字体和颜色规范，将重新使用此类别。  
  
    > [!NOTE]
    >  当检索使用的字体和颜色数据 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 或其他接口，VSPackages 迁移使用此 GUID 来引用内置的信息。  
  
2.  类别的名称必须添加到 VSPackage 的资源 \(.rc\) 文件，请在字符串表，以便可将其本地化根据需要在 IDE 中显示时。  
  
     有关详细信息，请参阅[Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string)。  
  
### 若要注册使用内置的字体和颜色的类别  
  
1.  构造一个特殊类型的类别中的以下位置的注册表条目︰  
  
     \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\*\< Visual Studio 版本 \>*\\FontAndColors\\*\< 类别 \>*\]  
  
     *\< 类别 \>* 是该类别的非本地化名称。  
  
2.  填充注册表以具有四个值中使用的常用字体和颜色方案︰  
  
    |名称|类型|数据|描述|  
    |--------|--------|--------|--------|  
    |类别|REG\_SZ|GUID|一个标识包含常用的字体和颜色方案的类别的任意 GUID。|  
    |package|REG\_SZ|GUID|{} F5E7E71D\-1401\-11D1\-883B\-0000F87579D2<br /><br /> 此 GUID 可供使用的默认字体和颜色配置的所有 Vspackage。|  
    |NameID|REG\_DWORD|ID|VSPackage 中的可本地化的类别名称的资源 ID。|  
    |ToolWindowPackage|REG\_SZ|GUID|VSPackage 实现的 GUID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 接口。|  
  
3.  
  
### 若要启动使用系统提供的字体和颜色  
  
1.  创建的实例 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` 作为窗口的实现和初始化的一部分的接口。  
  
2.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> 方法来获取实例 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 接口对应于当前 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 实例。  
  
3.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 两次。  
  
    -   使用一次调用 `VSEDITPROPID_ViewGeneral_ColorCategory`作为参数。  
  
    -   使用一次调用 `VSEDITPROPID_ViewGeneral_FontCategory` 作为参数。  
  
     此设置，并将默认字体和颜色服务公开为窗口中的属性。  
  
## 示例  
 下面的示例启动使用内置的字体和颜色。  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## 请参阅  
 [使用字体和颜色](../extensibility/using-fonts-and-colors.md)   
 [获取字体和文本着色的颜色信息](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)   
 [字体和颜色概述](../extensibility/font-and-color-overview.md)