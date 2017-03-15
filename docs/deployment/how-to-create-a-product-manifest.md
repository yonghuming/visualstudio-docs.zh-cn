---
title: "如何：创建产品清单 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "依赖项, 自定义引导程序包"
  - "系统必备, 自定义引导程序包"
  - "产品文件 [ClickOnce]"
  - "产品文件 [Windows Installer]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：创建产品清单
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要为您的应用程序部署系统必备组件，您可以创建一个引导程序包。  引导程序包包含单个产品清单文件以及与每个区域设置一一对应的程序包清单。  程序包清单包含程序包中专用于本地化的内容，  其中包括字符串、最终用户许可协议和语言包。  
  
 有关产品清单的更多信息，请参见[如何：创建程序包清单](../deployment/how-to-create-a-package-manifest.md)。  
  
## 创建产品清单  
  
#### 创建产品清单  
  
1.  为引导程序包创建目录。  此示例使用 C:\\package。  
  
2.  在 Visual Studio 中，创建一个名为 `product.xml` 的新 XML 文件，并将其保存到 C:\\package 文件夹中。  
  
3.  添加以下 XML 以描述程序包的 XML 命名空间和产品代码。  用程序包的唯一标识符替换产品代码。  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  添加 XML 以指定程序包具有依赖项。  此示例使用对于 Microsoft Windows Installer 3.1 的依赖项。  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  添加 XML 以列出引导程序包中的所有文件。  此示例使用程序包文件名 CorePackage.msi。  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  将 CorePackage.msi 文件复制或移动到 C:\\package 文件夹。  
  
7.  添加 XML 以使用引导程序命令安装程序包。  引导程序会自动将 **\/qn** 标记添加到 .msi 文件中，这将在无提示的情况下进行安装。  对于 .exe 文件，引导程序将使用 shell 来运行 .exe 文件。  下面的 XML 没有为 CorePackage.msi 显示任何参数，但您可以在 Arguments 特性中放置命令行参数。  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  添加以下 XML 以检查是否已安装此引导程序包。  用可再发行组件的 GUID 替换产品代码。  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. 添加 XML 以更改引导程序的行为，具体取决于是否已安装引导程序组件。  如果已安装该组件，则引导程序包不会运行。  以下 XML 会检查当前用户是否为管理员，原因是该组件需要管理特权。  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. 添加 XML 以设置安装成功时和需要重新启动时的退出代码。  以下 XML 演示了 Fail 和 FailReboot 退出代码，它们指示引导程序将不再继续安装程序包。  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. 添加以下 XML 以结束引导程序的命令部分。  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. 将 C:\\package 文件夹移到 Visual Studio 引导程序目录中。  对于 Visual Studio 2010，该目录为 \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages。  
  
## 示例  
 产品清单包含自定义系统必备组件的安装说明。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)