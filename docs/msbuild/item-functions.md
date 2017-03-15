---
title: "项函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 项函数"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 项函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

从 MSBuild 4.0 开始，任务和目标中的代码可以调用项函数，以获取有关项目中的项的信息。  这些函数简化了获取 Distinct\(\) 项的过程，比循环访问各个项的速度更快。  
  
## 字符串项目功能  
 在 .NET Framework 可以使用字符串的方法和属性来操作任何项的值。  对于 <xref:System.String> 方法，指定方法的名称。  对于 <xref:System.String> 属性，请在“get\_”之后指定属性名。  
  
 具有多个项的字符串，字符串方法或属性在每个字符串运行。  
  
 下面的示例演示如何使用这些字符串项目功能。  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## 内部项目功能  
 下表列出了可用于项的内部函数。  
  
|功能|示例|描述|  
|--------|--------|--------|  
|`Count`|`@(MyItem->Count())`|返回项目的计数。|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|返回 `Path.DirectoryName` 等效的每个项。|  
|`Distinct`|`@(MyItem->Distinct())`|返回具有不同的 `Include` 值的项。  元数据将被忽略。  比较不区分大小写。|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|返回具有不同的 `itemspec` 值的项。  元数据将被忽略。  比较是区分大小写的。|  
|`Reverse`|`@(MyItem->Reverse())`|返回以相反的顺序项目。|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|返回 `boolean` 指示任何项目是否具有给定元数据名称和值。  比较不区分大小写。|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|返回与其清除的元数据的项。  仅 `itemspec` 保留。|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|返回与给定的元数据名称的项。  比较不区分大小写。|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|返回包含元数据名称元数据的值。|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|返回具有给定元数据名称和值的项。  比较不区分大小写。|  
  
 下面的示例演示如何使用内部项目功能。  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## 请参阅  
 [项](../msbuild/msbuild-items.md)