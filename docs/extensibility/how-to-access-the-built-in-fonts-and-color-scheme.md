---
title: "如何︰ 访问的内置的字体和配色方案 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: f646bb0a1606bd5944c945c5db89083fa265afbd
ms.contentlocale: zh-cn
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>如何︰ 访问的内置的字体和配色方案
Visual Studio 集成的开发环境 (IDE) 有与编辑器窗口相关联的字体和颜色的架构。 你可以访问通过此方案<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 若要使用的内置的字体和颜色方案，VSPackage 必须︰  
  
-   定义要用于默认字体和颜色服务类别。  
  
-   默认字体和颜色服务器注册的类别。  
  
-   建议 IDE 特定窗口通过使用内置的显示项和类别`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer`和`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer`接口。  
  
 IDE 使用窗口的句柄作为生成的类别。 类别的名称显示在**显示其设置︰**中的下拉列表框**字体和颜色**属性页。  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>若要定义使用内置的字体和颜色的类别  
  
1.  创建一个任意 GUID。  
  
     此 GUID 用于唯一标识某一类别**。** IDE 的默认字体和颜色规范，将重新使用此类别。  
  
    > [!NOTE]
    >  检索与的字体和颜色数据时<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>或其他接口，Vspackage 使用此 GUID 来引用内置的信息。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
2.  以便可以进行本地化根据需要在 IDE 中显示时，类别的名称必须添加到 VSPackage 的资源 (.rc) 文件，请在字符串表。  
  
     有关详细信息，请参阅[添加或删除字符串](/cpp/windows/adding-or-deleting-a-string)。  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>若要注册使用内置的字体和颜色的类别  
  
1.  构造一个特殊类型的类别中的以下位置的注册表条目︰  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 1>*\FontAndColors\\*\<类别 1>*]  
  
     *\<类别 1>*是类别的非本地化名称。  
  
2.  填充注册表以具有四个值中使用的常用字体和颜色方案︰  
  
    |名称|类型|数据|描述|  
    |----------|----------|----------|-----------------|  
    |类别|REG_SZ|GUID|用于标识包含常用的字体和颜色方案的类别的任意 GUID。|  
    |包|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> 使用默认的字体和颜色配置的所有 Vspackage 都使用此 GUID。|  
    |NameID|REG_DWORD|Id|在 VSPackage 中的可本地化的类别名称的资源 ID。|  
    |ToolWindowPackage|REG_SZ|GUID|VSPackage 实现的 GUID<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
  
3.  
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>若要启动使用系统提供的字体和颜色  
  
1.  创建的实例`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer`窗口的实现和初始化的一部分的接口。  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>方法来获取的实例`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer`接口对应于当前<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>实例。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>  
  
3.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>两次。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>  
  
    -   调用一次与`VSEDITPROPID_ViewGeneral_ColorCategory`作为自变量。  
  
    -   调用一次与`VSEDITPROPID_ViewGeneral_FontCategory`作为自变量。  
  
     此设置，并将默认字体和颜色服务公开为窗口的属性。  
  
## <a name="example"></a>示例  
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
  
## <a name="see-also"></a>另请参阅  
 [使用字体和颜色](../extensibility/using-fonts-and-colors.md)   
 [获取字体和文本着色的颜色信息](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)   
 [字体和颜色概述](../extensibility/font-and-color-overview.md)
