---
title: "语言服务器协议概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aeef820575a4fb055318fe11d401e85c9958bad
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="language-server-protocol"></a>语言服务器协议

## <a name="what-is-the-language-server-protocol"></a>语言服务器协议是什么？

支持丰富的编辑功能喜欢源代码自动完成功能或**转到定义**编辑器或 IDE 中的编程语言为传统上非常困难和耗时。 通常，它需要的编程语言的编辑器或 IDE 中编写域模型 （扫描仪、 一个分析器、 类型检查程序、 一个生成器和的详细信息）。 例如，提供对 C/c + + Eclipse IDE 中支持的 Eclipse CDT 插件是用 Java 编写由于 Eclipse IDE 本身用 Java 编写。 以下这种方法，它将表示为 Visual Studio 在 C# 中实现 typescript 为 Visual Studio Code，C/c + + 域模型和单独的域模型。

创建特定于语言的域模型，还有容易得多，如果一个开发工具，可以重复使用现有的特定于语言的库。 但是，这些库通常实现编程语言本身 （例如，好 C/c + + 域模型在 C/c + + 中实现）。 将 C/c + + 库集成到编辑器编写 typescript 就从技术上讲但难做到。

### <a name="language-servers"></a>语言服务器

另一种方法是在其自己的进程中运行库，并使用进程间通信与它交流。 来回发送的消息形成一种协议。 语言服务器协议 (LSP) 是标准化开发工具和语言服务器进程之间交换的消息的乘积。 使用语言服务器或恶魔不是一个新的或 novel 的想法。 编辑器 Vim 等 Emacs 这样做了一段时间，以提供语义的自动完成支持。 LSP 的目的是简化这些种类的集成，并为公开的各种工具的语言功能提供有用的框架。

具有一种通用协议可让入有条不紊地开发工具通过重复使用的现有实施的语言的域模型编程语言功能的集成。 无法用 PHP、 Python 或 Java 编写语言服务器后端并 LSP 允许它很容易集成到各种工具。 协议的工作原理在常见的抽象级别以便工具可以提供丰富的语言服务，而无需完全了解特定于基础的域模型的细微差别。

## <a name="how-work-on-the-lsp-started"></a>如何在启动 LSP 上工作

通过逐步发展 LSP 和现在它是在版本 3.0。 它启动时的语言服务器概念已拾取 OmniSharp 为 C# 提供丰富的编辑功能。 最初，OmniSharp JSON 负载与使用 HTTP 协议和已集成到多个编辑器包括[Visual Studio Code](https://code.visualstudio.com)。

时间大致相同，Microsoft 开始使用 TypeScript 语言服务器，例如 Emacs 和 Sublime Text 的编辑器中支持 TypeScript 知道上。 在此实现中，编辑器通过 stdin/stdout 与 TypeScript 服务器进程通信，并且用于请求和响应的 JSON 负载启发而开发出由 V8 调试器协议。 TypeScript 服务器已经被集成到 TypeScript Sublime 插件和 VS 代码，以进行丰富 TypeScript 编辑。

采用集成两个不同的语言服务器后, VS Code 团队开始浏览对于编辑器和 Ide 的一种通用语言服务器协议。 一种通用协议启用的语言提供程序，以创建单语言版服务器可由不同 Ide 使用。 语言服务器使用者只具有实现协议的客户端一次。 这会导致双赢情形语言提供程序和语言使用者。

开始使用 TypeScript 服务器使用的语言协议，很多个常规和非特定语言。 协议已具有用于灵感 VS Code 语言 API 的多语言功能。 这种协议本身支持 JSON rpc 由于其简单性和支持的库，针对许多编程语言的远程调用。

VS Code 团队 dogfooded 通过实现多个 linter 语言服务器协议。 Linter 语言服务器响应链接形式 （扫描） 文件的请求，并返回一组的检测到的警告和错误。 目标是链接形式到一个文件作为在文档中，这意味着在编辑器会话期间，有许多 linting 请求的用户编辑。 若要使注册的服务器和运行，以便新的 linting 进程不需要为每个用户编辑启动道理。 多台 linter 服务器上实现，包括 VS Code ESLint 和 TSLint 扩展。 这两个 linter 服务器都同时在 TypeScript/JavaScript 中实现并在 Node.js 上运行。 它们共享的库，实现协议的客户端和服务器的一部分。

## <a name="how-the-lsp-works"></a>LSP 的工作原理

语言服务器运行在其自己的进程，并如 Visual Studio 或 VS Code 的工具与通过 JSON RPC 使用的语言协议对服务器进行通信。 语言服务器操作系统的专用的过程中的另一个优点是避免与单个进程模型相关的性能问题。 实际的传输通道可以是 stdio、 套接字、 命名的管道或节点 ipc 如果客户端和服务器用 Node.js 编写。

一种工具和语言服务器期间例程的通信方式的一个示例下面编辑会话：

![lsp 流关系图](media/lsp-flow-diagram.png)

* **用户将在该工具中打开文件 （也称为文档）**： 该工具将通知语言服务器，该文档已打开 (textDocument/didOpen)。 从现在起，文档的内容方面的真相已不再在文件系统上，但保留的内存中的工具。

* **用户所做的编辑**： 该工具将通知有关文档更改 (textDocument/didChange) 的服务器并由语言服务器更新程序的语义信息。 发生这种情况，如语言服务器分析此信息并通知检测到的错误和警告 (textDocument/publishDiagnostics) 的工具。

* **用户在编辑器中的符号上执行"转到定义"**： 该工具会发送两个参数的 textDocument/定义请求: (1) 文档 URI 和 （2） 的文本位置中从转到定义请求初始化到服务器之前的位置。 服务器响应文档 URI 和文档内部的符号的定义的位置。

* **用户关闭文档 （文件）**： 从工具，通知现在不再在内存，当前的内容现在是最新文件系统上文档的语言服务器发送 textDocument/didClose 通知。

此示例演示如何与语言服务器级别的编辑器功能，如"转到定义"，"查找所有引用"协议的通信方式。 协议使用的数据类型是编辑器或 IDE 数据类型，如当前打开文本文档和光标的位置。 数据类型不在编程语言域模型通常提供抽象语法树和编译器符号 （例如，解析类型、 命名空间，...） 级别中。这极大地简化了协议。

现在让我们看一下更多详细信息中的 textDocument/定义请求。 下面是转到客户端工具和 c + + 文档中的"转到定义"请求的语言服务器之间的负载。

这是请求：

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

这是操作的响应：

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

回顾，描述级别中，而不是编辑器的在编程语言模型的级别的数据类型是编辑器的成功的语言服务器协议原因之一。 它是要简单得标准化文本文档 URI 或与跨不同的编程语言标准化抽象语法树和编译器符号比较光标位置。

在用户使用不同的语言，VS Code 通常启动每种编程语言的语言的服务器。 下面的示例显示会话用户 Java 和 SASS 文件上的工作位置。

![java 和 sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>功能

不是每个语言服务器可以支持由协议定义的所有功能。 因此，客户端和服务器宣布通过功能及其支持的功能集。 例如，一台服务器宣布，它可以处理 textDocument/定义请求中，但它可能不处理工作区/symbol 请求。 同样，客户端可以公告均能够提供即将保存之前保存文档，以便服务器可以计算文本的编辑将编辑过的文档自动设置格式的通知。

## <a name="integrating-a-language-server"></a>集成了语言服务器

语言服务器的实际集成到特定工具未定义的语言服务器协议，并为从左到工具实现器。 一些工具将具有扩展，它可以启动并与任何一种语言服务器通信的集成语言服务器以一般方式。 其他人，如 VS Code 中，创建每个语言服务器的自定义扩展，以便扩展是仍能够提供一些自定义的语言功能。

若要简化语言服务器和客户端实现，还有库或 Sdk 的客户端和服务器的部分。 不同语言提供了这些库。 例如，没有[语言客户端 npm 模块](https://www.npmjs.com/package/vscode-languageclient)为了便于语言服务器的集成到 VS Code 扩展，另一个[语言服务器 npm 模块](https://www.npmjs.com/package/vscode-languageserver)编写使用 Node.js 的语言服务器。 这是当前[列表](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations)支持库。

## <a name="using-the-language-server-protocol-in-visual-studio"></a>使用 Visual Studio 中的语言服务器协议

* [添加语言服务器协议扩展](adding-an-lsp-extension.md)-了解如何将语言服务器集成到 Visual Studio。
