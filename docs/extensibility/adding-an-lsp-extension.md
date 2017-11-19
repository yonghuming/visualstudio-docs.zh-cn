---
title: "添加语言服务器协议扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e38c040e732571e3343c30d84745d2602a1088d
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="adding-a-language-server-protocol-extension"></a>添加语言服务器协议扩展

语言服务器协议 (LSP) 是一种常见协议，JSON RPC v2.0，用于提供各种代码编辑器向 service 功能的语言的形式。 使用协议时，开发人员可以编写单语言版服务器以提供 IntelliSense，错误诊断等服务功能的语言，查找所有引用，到各种支持 LSP 的代码编辑器等。 传统上，可以通过以下任一方法添加在 Visual Studio 中的语言服务使用 TextMate 语法文件提供基本功能，如语法突出显示，或通过编写自定义的语言服务使用完整的 Visual Studio 扩展性 Api 集到提供更丰富的数据。 现在，对 LSP 提供了一个第三个选项的支持。

![Visual Studio 中的语言服务器协议服务](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>语言服务器协议

这种协议本身的详细信息，请参阅文档[此处](https://github.com/Microsoft/language-server-protocol)。 Visual Studio 语言服务器协议实现为预览版，并支持应视为实验。 预览版本处于扩展的形式 ([语言服务器协议客户端预览版](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview))，**但只能安装此扩展上预览通道的 Visual Studio**。 更高版本的 Visual Studio 将包括对语言服务器协议，此时预览标志将删除的内置支持。 **对于生产用途，不应使用预览版。**

有关详细信息如何创建示例语言服务器或如何将现有语言服务器集成到 Visual Studio 代码，请参阅文档[此处](https://code.visualstudio.com/docs/extensions/example-language-server)。

![语言服务器协议实现](media/lsp-implementation.png)

本文介绍如何在 Visual Studio 中使用的基于 LSP 语言服务器创建的扩展。 它假定你已开发了 LSP 基于语言服务器，并且只是想要将其集成到 Visual Studio。

有关 Visual Studio 中的支持，语言服务器能够与客户端 (Visual Studio) 通过以下机制：

* 标准输入/输出流
* 命名的管道
* 套接字

LSP 和它支持 Visual Studio 中的目的是不是 Visual Studio 产品的一部分的载入语言服务。 它不是扩展 （如 C# 中) 在 Visual Studio 中的现有语言服务。 若要扩展现有的语言，请参阅语言服务的可扩展性指南 (例如， ["Roslyn".NET Compiler Platform](https://docs.microsoft.com/visualstudio/extensibility/dotnet-compiler-platform-roslyn-extensibility))。

## <a name="language-server-protocol-features-supported"></a>支持的语言服务器协议功能

LSP 支持以下功能在 Visual Studio 中到目前为止：

消息 | 在 Visual Studio 中具有支持
--- | ---
初始化 | 是
已初始化 | 
关机 | 是
退出 | 是
$/ cancelRequest | 是
窗口/分隔开多个 | 是
窗口/showMessageRequest | 是
窗口/logMessage | 是
遥测/事件 |
客户端/registerCapability |
客户端/unregisterCapability |
工作区/didChangeConfiguration | 是
工作区/didChangeWatchedFiles | 是
工作区/符号 | 是
工作区/executeCommand |
工作区/applyEdit |
textDocument/publishDiagnostics | 是
textDocument/didOpen | 是
textDocument/didChange | 是
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave |
textDocument/didClose | 是
textDocument/完成 | 是
完成/解决 | 是
textDocument/悬停 |
textDocument/signatureHelp |
textDocument/引用 | 是
textDocument/documentHighlight |
textDocument/documentSymbol | 是
格式设置 textDocument / | 是
textDocument/rangeFormatting | 是
textDocument/onTypeFormatting |
textDocument/定义 | 是
textDocument/codeAction |
textDocument/codeLens |
codeLens/解决 |
textDocument/documentLink |
documentLink/解决 |
textDocument/重命名 |

## <a name="getting-started"></a>入门

### <a name="create-a-vsix-project"></a>创建 VSIX 项目

若要创建语言服务扩展使用基于 LSP 语言服务器，首先请确保你有**Visual Studio 扩展开发**安装 VS 实例的工作负荷。

接下来通过导航到创建新的空白 VSIXProject**文件** > **新项目** > **Visual C#**  >  **扩展性** > **VSIX 项目**:

![创建 vsix 项目](media/lsp-vsix-project.png)

对于预览版本，对 LSP VS 支持将 VSIX 形式 ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview))。 扩展开发人员想要创建使用 LSP 语言服务器的扩展，必须上此 VSIX 使依赖关系。 这意味着，对于客户希望安装的语言服务器扩展**必须首先安装语言服务器协议客户端预览版 VSIX。**

若要定义 VSIX 依赖项，打开你的 VSIX 的 VSIX 清单设计器 （例如，通过双击打开 source.extension.vsixmanifest 文件中在你的项目中），并导航到**依赖关系**:

![添加对语言服务器协议客户端引用](media/lsp-reference-lsp-dependency.png)

创建新的依赖关系，如下所示：

![定义语言服务器协议客户端依赖关系](media/lsp-define-lsp-dependency.png)

* **源**： 手动定义
* **名称**： 语言服务器协议客户端预览版
* **标识符**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **版本范围**: [1.0,2.0)
* **如何为依赖关系解析**： 由用户安装
* **下载 URL**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

>**请注意**:**下载 URL**应该始终填写以便安装你的扩展的用户了解如何安装必需的依赖关系。

### <a name="language-server-and-runtime-installation"></a>语言服务器和运行时安装

默认情况下，对语言服务器本身或需要执行它们的运行时，将不包含为在 Visual Studio 中支持基于 LSP 语言服务器创建的扩展。 扩展开发人员负责分发语言服务器和所需的运行时。 有多种，若要这样做：

* 为内容文件，可以在 VSIX 中嵌入语言服务器。
* 创建 MSI 安装语言服务器和/或需要运行时。
* 提供有关应用商店的通知用户如何获取运行时和语言的服务器的说明。

### <a name="textmate-grammar-files"></a>TextMate 语法文件

LSP 不包括有关如何提供语言的文本着色的规范。 若要提供自定义 Visual Studio 中的语言着色，扩展开发人员可以使用 TextMate 语法文件。 若要添加自定义 TextMate 语法或主题文件，请按照下列步骤：

1. 创建一个名为在你的扩展"语法"文件夹 （也可以是你选择的任何名称）。

2. "语法"文件夹中，包括你想要提供自定义着色任何 *.tmlanguage 或 *.tmtheme 文件。

3. 右键单击文件并选择**属性**。 更改对指定的生成操作**内容**和**包括在 VSIX 中的**属性为 true。

4. 创建一个.pkgdef 文件并添加与此类似的行：

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. 右键单击文件并选择**属性**。 更改对指定的生成操作**内容**和**包括在 VSIX 中的**属性为 true。

这将"语法"文件夹作为名为 MyLang 的存储库源添加包的安装目录 （MyLang 是只需消除歧义的名称，可以是任何唯一的字符串）。 作为潜力选取的所有语法 （.tmlanguage 文件） 和此目录中的主题文件 （.tmtheme 文件），并且会取代 TextMate 与提供的内置语法。 如果语法文件声明的扩展匹配所打开的文件的扩展名，将步骤 TextMate。

## <a name="creating-a-simple-language-client"></a>创建简单的语言，客户端

### <a name="main-interface---ilanguageclienthttpsdocsmicrosoftcomdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>主接口- [ILanguageClient](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

创建 VSIX 项目之后，将以下 NuGet 程序包添加到你的项目：

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

你可以然后创建一个新类来实现[ILanguageClient](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)接口，连接到基于 LSP 语言服务器的语言客户端所需的主要接口。

下面是一个示例：

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }
    }
}
```

需要实现的主要方法为[OnLoadedAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017)和[ActivateAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)。 [OnLoadedAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) Visual Studio 已加载你的扩展，并且你语言的服务器是否准备好启动时调用。 在此方法中，你可以调用[StartAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)立即要指示应启动语言服务器，或可以执行其他逻辑，还可以调用委托[StartAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)更高版本。 **若要激活语言服务器必须在某一时刻调用 StartAsync。**

[ActivateAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)是通过调用最终调用的方法[StartAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委托; 它包含用于启动语言服务器并建立连接的逻辑。 连接对象需要返回其中包含用于写入到服务器或从服务器读取的流。 将捕获并显示给用户通过 Visual Studio 中的信息栏消息此处引发任何异常。

### <a name="activation"></a>激活

语言客户端类实现后，你将需要定义为其定义如何将加载到 Visual Studio 和激活的两个属性：

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio 将使用[MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) 以管理其扩展性点。 [导出](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx)属性指示到 Visual Studio 中，此类应选取作为一个扩展点并在适当时加载。

若要使用 MEF，你必须定义 MEF 为 VSIX 清单中的资产。

打开你的 VSIX 清单设计器并导航到**资产**选项卡：

![添加 MEF 资产](media/lsp-add-asset.png)

单击新建以创建新的资产：

![定义 MEF 资产](media/lsp-define-asset.png)

* **类型**: Microsoft.VisualStudio.MefComponent
* **源**： 当前解决方案中的项目
* **项目**: [项目]

### <a name="content-type-definition"></a>内容类型定义

当前加载你 LSP 基于语言的服务器扩展的唯一方法是通过文件内容类型。 即，定义语言客户端类时 (可实现[ILanguageClient](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017))，你将需要定义类型的文件，打开时，将加载你的扩展。 如果不打开任何你定义的内容类型匹配的文件，将不加载你的扩展。

通过定义一个或多个 ContentTypeDefinition 类完成此操作：

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

在上面的示例中，为以.bar 文件扩展名结尾的文件创建的内容类型定义。 内容类型定义给定名称"栏"和**必须**派生自[CodeRemoteContentTypeName](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)。

在添加的内容类型定义之后, 你可以然后定义何时加载你语言的客户端扩展语言客户端类中：

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

添加对 LSP 语言服务器的支持不需要你在 Visual Studio 中实现您自己的项目系统。 客户可以在 Visual Studio，若要开始使用你语言服务中打开单个文件或文件夹。 事实上，支持 LSP 语言服务器旨在仅在打开的文件夹/文件方案中工作。 如果实现自定义项目系统，某些功能，例如设置，将无法工作。

## <a name="advanced-features"></a>高级的功能

### <a name="settings"></a>设置

支持自定义语言服务器特定设置可用于在 Visual Studio 中，LSP 支持预览版本，但它正在仍进行完善。 设置都特定于语言服务器支持，通常控制如何语言服务器发出数据。 例如，语言服务器可能具有的最大报告的错误数的设置。 扩展插件作者可以定义默认值，对于特定项目的用户可以更改。

请按照以下步骤来将对设置的支持添加到你 LSP 语言服务的扩展操作：

1. 添加 JSON 文件 (例如，"MockLanguageExtensionSettings.json") 在项目中包含的设置和其默认值。 例如: 

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. 在 JSON 文件上右键单击并选择**属性**。 更改**生成**操作保存到"内容"和"包括在 VSIX 中的属性为 true。

3. 实现 ConfigurationSections 并返回的 JSON 文件中定义的设置的前缀的列表 （在 Visual Studio Code 中，这将映射到在 package.json 中的配置节名称）：

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. 将.pkgdef 文件添加到项目 （添加新的文本文件并将文件扩展名更改为.pkgdef）。 Pkgdef 文件应包含此信息：

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. 右键单击.pkgdef 文件，然后选择**属性**。 更改**生成**的"内容"和"包括在 VSIX"属性为 true 的操作。

6. 打开`source.extension.vsixmanifest`文件并添加中的资产**资产**选项卡：

  ![编辑 vspackage 资产](media/lsp-add-vspackage-asset.png)

  * **类型**: Microsoft.VisualStudio.VsPackage
  * **源**： 在文件系统上的文件
  * **路径**: [pkgdef 文件路径]

### <a name="user-editing-of-settings-for-a-workspace"></a>用户编辑的工作区设置

1. 用户打开包含你的服务器拥有的文件的工作区。
2. 用户调用"VSWorkspaceSettings.json"的".vs"文件夹中添加文件。
3. 用户将行添加到该服务器提供的设置的 VSWorkspaceSettings.json 文件。 例如: 

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```

### <a name="custom-messages"></a>自定义消息

有就地的 Api，以便于将消息传递到和从语言服务器不属于标准语言服务器协议的接收消息。 若要处理的自定义消息，实现[ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)语言客户端类中的接口。 [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)库用于传输语言客户端和服务器之间的自定义消息。 因为你 LSP 语言的客户端扩展就像任何其他 Visual Studio 扩展一样，你可以决定将其他功能 （即不受 LSP） 添加到 Visual Studio （使用其他 Visual Studio Api） 自定义消息都可通过扩展中。

#### <a name="receiving-custom-messages"></a>接收自定义消息

若要从语言服务器接收的自定义消息，实现[CustomMessageTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017)属性[ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)并返回一个知道如何处理你的自定义消息的对象. 下面的示例：

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>发送自定义消息

若要将自定义消息发送到语言服务器，实现[AttachForCustomMessageAsync](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017)方法[ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)。 当你语言的服务器已启动并准备好接收消息时，会调用此方法。 A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)对象作为一个参数，然后，可以保持，以将消息发送到语言服务器使用传递[VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Api。 下面的示例：

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
}
```

### <a name="middle-layer"></a>中间层

有时扩展开发人员可能想要截获 LSP 消息发送到和接收到来自语言服务器。 例如，扩展开发人员可能想要更改的特定 LSP 消息，发送的消息参数或修改从 LSP 的功能 （例如完成） 语言服务器返回的结果。 如果这是必需的扩展开发人员可以使用 MiddleLayer API 截获 LSP 消息。

每个 LSP 消息具有截获自己中间层接口。 若要截获某个特定消息，请创建实现该消息的中间层接口的类。 然后，实现[ILanguageClientCustomMessage](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)语言客户端类中接口，并返回中的对象的实例[MiddleLayer](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017)属性。 下面的示例：

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{

    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
}
```

中间层功能是仍在开发和尚未不全面。

## <a name="sample-lsp-language-server-extension"></a>示例 LSP 语言服务器扩展

若要查看使用 LSP 客户端 API 在 Visual Studio 中的一个扩展示例的源代码，请参阅 VSSDK 扩展性示例[LSP 示例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)。

## <a name="faq"></a>FAQ

**我想要生成自定义项目系统来补充以提供更丰富的功能支持在 Visual Studio 中，我 LSP 语言服务器如何我该转到有关执行此操作？**

对 Visual Studio 中的基于 LSP 语言服务器支持依赖于[打开文件夹功能](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/)和专门用于不需要自定义项目系统。 您可以构建按照说明进行操作你自己的自定义项目系统[此处](https://github.com/Microsoft/VSProjectSystem)，但某些功能，例如设置，可能无法工作。 LSP 语言服务器的默认初始化逻辑是文件夹的传入的当前已经打开的根文件夹位置，因此如果你使用自定义项目系统，你可能需要在初始化，以确保你的语言服务器会提供自定义逻辑正常启动。

**如何添加调试器支持？**

我们将提供支持[常见调试协议](https://code.visualstudio.com/docs/extensionAPI/api-debugging)的未来版本中。

**如果已存在 VS 受支持的语言安装的服务 (例如，JavaScript)，可以仍安装 LSP 语言服务器扩展，提供了附加功能 （如 linting)？**

是，但并非所有功能都正常工作。 为 LSP 语言服务器扩展的最终目标是能够语言服务本身不支持的 Visual Studio。 你可以创建扩展提供更多支持使用 LSP 语言服务器，但某些功能，例如 IntelliSense、 将不会顺畅的体验。 通常我们建议用于提供新的语言体验 LSP 语言服务器扩展不扩展现有的。

**其中将我已完成的 LSP 语言服务器 VSIX 的发布？**

请参阅应用商店说明[此处](walkthrough-publishing-a-visual-studio-extension.md)。
