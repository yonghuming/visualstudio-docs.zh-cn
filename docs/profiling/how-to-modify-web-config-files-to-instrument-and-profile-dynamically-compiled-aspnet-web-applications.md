---
title: "如何：修改 Web.Config 文件以检测和分析动态编译的 ASP.NET Web 应用程序 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 247913d77f9d698f27d7bc1983802314dda021e3

---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>如何：修改 Web.Config 文件以检测和分析动态编译的 ASP.NET Web 应用程序
使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具检测方法，可以从动态编译的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序收集详细计时数据、.NET 内存分配数据和 .NET 对象生存期数据。  
  
 本主题介绍如何修改 web.config 配置文件才能检测和分析 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序。  
  
> [!NOTE]
>  使用采样分析方法时或要检测预编译的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 模块时，不必修改 web.config 文件。  
  
 web.config 文件的根元素为 **configuration** 元素。 若要检测和分析动态编译的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序，必须添加或修改以下元素：  
  
-   **configuration/runtime/assemblyBinding/dependentAssembly** 元素，它标识控制分析的 Microsoft.VisualStudio.Enterprise.ASPNetHelper 程序集。 **dependentAssembly** 元素包含两个子元素：**assemblyIdentity** 和 **codeBase**。  
  
-   **configuration/system.web/compilation** 元素，它标识目标程序集的探查器处理后编译步骤。  
  
-   标识分析工具位置的两个 **add** 元素将被添加到 **configuration/appSettings** 节。  
  
 建议创建原始 web.config 文件的副本，该副本可用于还原应用程序的配置。  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>添加 ASPNetHelper 程序集作为 configuration/runtime/assemblyBinding/dependentAssembly 元素  
  
1.  如有必要，请添加 **runtime** 元素作为 **configuration** 元素的子元素；否则，请转到下一步。  
  
     **runtime** 元素没有任何属性。 **configuration** 元素只能有一个 **runtime** 子元素。  
  
2.  如有必要，请添加 **assemblyBinding** 元素作为 **runtime** 元素的子元素；否则，请转到下一步。  
  
     **runtime** 元素只能有一个 **assemblyBinding** 元素。  
  
3.  将下列属性名称和值添加到 **assemblyBinding** 元素：  
  
    |特性名|特性值|  
    |--------------------|---------------------|  
    |**Xmlns**|**urn:schemas-microsoft-com:asm.v1**|  
  
4.  添加 **dependentAssembly** 元素作为 **assemblyBinding** 元素的子元素。  
  
     **dependentAssembly** 元素没有任何属性。  
  
5.  添加 **assemblyIdentity** 元素作为 **dependentAssembly** 元素的子元素。  
  
6.  将下列属性名称和值添加到 **assemblyIdentity** 元素：  
  
    |特性名|特性值|  
    |--------------------|---------------------|  
    |**name**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**culture**|**Neutral**|  
  
7.  添加 **codeBase** 元素作为 **dependentAssembly** 元素的子元素。  
  
8.  将下列属性名称和值添加到 **codeBase** 元素：  
  
    |特性名|特性值|  
    |--------------------|---------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` 是 Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll 的文件 URL。 如果 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安装在默认位置，则 **href** 值应为 `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>将探查器后续处理步骤添加到 configuration/system.web/compilation 元素  
  
1.  如有必要，请添加 **system.web** 元素作为 **configuration** 元素的子元素；否则，请转到下一步。  
  
     **system.web** 元素没有任何属性。 **configuration** 元素只能有一个 **system.web** 子元素。  
  
2.  如有必要，请添加 **compilation** 元素作为 **system.web** 元素的子元素；否则，请转到下一步。  
  
     **system.web** 元素只能有一个 **compilation** 子元素。  
  
3.  从 **compilation** 元素中删除任何现有属性，并添加以下属性名称和值：  
  
    |特性名|特性值|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>将探查器位置设置添加到 configuration/appSettings 元素  
  
1.  如有必要，请添加 **appSettings** 元素作为 **configuration** 元素的子元素；否则，请转到下一步。  
  
     **appSettings** 元素没有任何属性。 **configuration** 元素只能有一个 **appSettings** 子元素。  
  
2.  添加 **add** 元素作为 **appSettings** 元素的子元素。  
  
3.  将下列属性名称和值添加到 **add** 元素：  
  
    |特性名|特性值|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**值**|`PerformanceToolsFolder` **\VSInstr.Exe**|  
  
4.  再添加一个 **add** 元素作为 **appSettings** 元素的子元素。  
  
5.  将下列属性名称和值添加到此 **add** 元素：  
  
    |特性名|特性值|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**值**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` 是探查器可执行文件的路径。 如果 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安装在默认位置，则该值将为 **C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>示例  
 下面是一个完整的 web.config 文件，该文件允许检测和分析动态编译的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序。 此示例假定修改前文件中没有其他设置。  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [如何：检测动态编译的 ASP.NET 应用程序并收集详细计时数据](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [如何：检测动态编译的 ASP.NET 应用程序并收集内存数据](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)


<!--HONumber=Feb17_HO4-->


