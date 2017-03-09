---
title: "如何：设置 VSPackage (C++) 外观方案 | Microsoft Docs"
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
  - "“关于”对话框"
  - "VSPackage, 初始屏幕"
  - "VSPackage, 外观方案"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 如何：设置 VSPackage (C++) 外观方案
若要显示 **帮助** 对话框和初始屏幕， Vspackage 必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> 接口。  执行此操作提供下列信息。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   名称  
  
-   ID，例如序列化的或版本号  
  
-   信息  
  
-   徽标图标  
  
 `IVsInstalledProductImpl` 类获取模板参数这些信息。  每个模板参数是 ID.  前三是字符串资源 ID，第四列是图标的资源 ID。  
  
## 示例  
 VSPackage 类的以下类声明是从 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 若要测试 VSPackage，请参见 [如何：测试帮助主题和初始屏幕](../misc/how-to-test-the-help-about-and-splash-screens.md)。  
  
## 请参阅  
 [Vspackage 外观方案](/visual-cpp/misc/vspackage-branding)