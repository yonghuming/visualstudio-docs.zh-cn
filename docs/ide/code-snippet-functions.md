---
title: "代码段函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码段 [Visual Studio], 函数"
  - "IntelliSense 代码段, 函数"
  - "代码段 [Visual Studio], 函数"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 代码段函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以对 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 代码段使用三个函数。  函数是在代码段的 [Function](http://msdn.microsoft.com/zh-cn/572c5549-5821-4e15-8ecd-0fa86c1c65df) 元素中指定的。  有关创建代码段的信息，请参见[代码段](../ide/code-snippets.md)。  
  
## 函数  
 下表描述了可用于代码段中的 `Function` 元素的函数。  
  
|功能|说明|Language|  
|--------|--------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|为 `EnumerationLiteral` 参数指定的枚举成员生成一个 switch 语句和一组 case 语句。  `EnumerationLiteral` 参数必须是对枚举文本或枚举类型的引用。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|返回包含已插入代码段的类的名称。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|在已调用该代码段的上下文中将 *TypeName* 参数缩减为其最简单的形式。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## 示例  
 下面的示例演示如何使用 `GenerateSwitchCases` 函数。  插入此代码段并将枚举输入到 `$switch_on$` 文本中时，`$cases$` 文本将为枚举中的每个值都生成一个 `case` 语句。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 示例  
 下面的示例演示如何使用 `ClassName` 函数。  插入此代码段时，`$classname$` 文本将替换为代码文件中处于该位置的封闭类的名称。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 示例  
 此示例演示如何使用 `SimpleTypeName` 函数。  将此代码段插入到代码文件中时，`$SystemConsole$` 文本将替换为调用该代码段的上下文中的 <xref:System.Console> 类型的最简单形式。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 请参阅  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/zh-cn/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [代码段架构参考](../ide/code-snippets-schema-reference.md)