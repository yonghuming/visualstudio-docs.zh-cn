---
title: "MSBuild Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild 属性"
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Properties1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

属性是可以用于配置生成的名称 / 值对。 属性可用于将值传递给任务，计算条件，以及存储在整个项目文件将被引用的值。  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>定义和引用项目文件中的属性  
 属性的声明方式创建有作为的子对象的属性名称的元素 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 元素。 例如，下面的 XML 创建一个名为属性 `BuildDir` ，其值为 `Build`。  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 在整个项目文件中，属性引用的使用语法 $(`PropertyName`)。 例如上, 一示例中的属性是使用引用 $(BuildDir)。  
  
 通过将重新定义该属性，可以更改属性值。  `BuildDir` 属性可以使用下面的 XML 赋予新值︰  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 属性的计算在项目文件中出现的顺序。 新值 `BuildDir` 必须在分配的旧值之后声明。  
  
## <a name="reserved-properties"></a>保留的属性  
 MSBuild 保留了一些属性名称，用于存储有关项目文件和 MSBuild 二进制文件的信息。 使用 $ 表示法，就像任何其他属性来引用这些属性时。 例如，$(MSBuildProjectFile) 返回项目文件，其中包括文件扩展名的完整文件名。  
  
 有关详细信息，请参阅 [如何︰ 引用的名称或项目文件的位置](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) 和 [MSBuild 保留和已知属性](../msbuild/msbuild-reserved-and-well-known-properties.md)。  
  
## <a name="environment-properties"></a>环境属性  
 就像引用保留的属性，可引用在项目文件中的环境变量。 例如，若要使用 `PATH` 在项目文件中，使用 $（路径） 的环境变量。 如果项目包含具有相同的名称作为环境属性的属性定义，在项目中的属性将覆盖环境变量的值。  
  
 每个 MSBuild 项目都有一个独立环境块：它只能识别对自己块的读写操作。  在计算或生成项目文件之前，MSBuild 只在初始化属性集合时读取环境变量。 在此之后，环境属性是静态的，也就是说，每个生成工具使用相同的名称和值启动。  
  
 若要获取从生成工具的环境变量的当前值，请使用 [属性函数](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable。 为首选的方法，但是，是使用任务参数 <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>。 可将此字符串数组中的环境属性集传递给生成工具，而不影响系统环境变量。  
  
> [!TIP]
>  并非所有的环境变量都被读入并成为初始属性。 系统将忽略变量名称不是有效 MSBuild 属性名称的所有环境变量（例如“386”）。  
  
 有关详细信息，请参阅 [如何︰ 在生成中使用环境变量](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)。  
  
## <a name="registry-properties"></a>注册表属性  
 您可以读取系统注册表值通过使用以下语法，其中 `Hive` 是注册表配置单元 (例如 HKEY_LOCAL_MACHINE) `Key` 是键名称 `SubKey` 是子项的名称，和 `Value` 是子项的值。  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 若要获取默认子项的值，请省略 `Value`。  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 可以使用此注册表值来初始化生成属性。 例如，若要创建一个表示 Visual Studio web 浏览器主页的生成属性，请使用以下代码︰  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>全局属性  
 MSBuild，可以使用命令行上设置属性 **/property** (或 **/p**) 切换。 这些全局属性值将覆盖在项目文件中设置的属性值。 这包括环境属性，但不包括保留的属性，不能更改。  
  
 下面的示例设置全局 `Configuration` 属性设置为 `DEBUG`。  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 此外可设置或修改为子项目中的多项目生成通过使用全局属性 `Properties` MSBuild 任务的属性。 有关详细信息，请参阅 [MSBuild 任务](../msbuild/msbuild-task.md)。  
  
 如果您在项目标记中使用 `TreatAsLocalProperty` 特性指定一个属性，则全局属性值不会重写项目文件中设置的属性值。 有关详细信息，请参阅 [Project 元素 (MSBuild)](../msbuild/project-element-msbuild.md) 和 [如何︰ 生成具有不同的选项相同的源文件](../msbuild/how-to-build-the-same-source-files-with-different-options.md)。  
  
## <a name="property-functions"></a>属性函数  
 从 .NET Framework 版本 4 开始，可以使用属性函数来计算 MSBuild 脚本。 可以读取系统时间、 比较字符串、 匹配正则表达式和生成脚本中执行许多其他操作，而无需使用 MSBuild 任务。  
  
 可以使用字符串 （实例） 方法来操作任何属性值，并且可以调用许多系统类的静态方法。 例如，您可以生成将属性设置为当天日期，如下所示。  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 有关详细信息，以及属性函数的列表，请参阅 [属性函数](../msbuild/property-functions.md)。  
  
## <a name="creating-properties-during-execution"></a>在执行过程中创建属性  
 属性位于之外 `Target` 元素生成的计算阶段分配值。 在后续执行阶段，但属性可创建或修改，如下所示︰  
  
-   任何任务也可以发出一个属性。 若要发出一个属性， [任务](../msbuild/task-element-msbuild.md) 元素必须具有子元素 [输出](../msbuild/output-element-msbuild.md) 具有元素 `PropertyName` 属性。  
  
-   属性也可以发出 [CreateProperty](../msbuild/createproperty-task.md) 任务。 这种用法中已弃用。  
  
-   在.NET Framework 3.5 中，启动 `Target` 元素都可能包含 `PropertyGroup` 可以包含以下属性声明的元素。  
  
## <a name="storing-xml-in-properties"></a>在属性中存储 XML  
 属性可以包含任意 XML，这有助于在将值传递给任务或显示日志记录信息。 下面的示例演示 `ConfigTemplate` 属性，它具有一个包含 XML 和其他属性值的引用。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 通过使用其相应属性的值替换属性引用。 属性值分配它们的显示顺序。 因此，在此示例中， `$(MySupportedVersion)`, ，`$(MyRequiredVersion)`, ，和 `$(MySafeMode)` 应已定义。  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>另请参阅  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)  
 [如何︰ 在生成中使用环境变量](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)   
 [如何︰ 引用的名称或项目文件的位置](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md)   
 [如何︰ 生成具有不同的选项相同的源文件](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild 保留属性和已知属性](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Property 元素 (MSBuild)](../msbuild/property-element-msbuild.md)