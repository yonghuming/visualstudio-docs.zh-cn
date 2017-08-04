---
title: "使用“创建单元测试”命令创建单元测试方法存根 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Get started
ms.assetid: 21FE4D68-9E7F-4BB1-BD69-B0D09A941F09
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 0194688e9eec258e415a30a8915379affc5f89de
ms.contentlocale: zh-cn
ms.lasthandoff: 06/02/2017

---
# <a name="get-started-with-microsoft-intellitest"></a>Microsoft IntelliTest 入门

* 如果首次使用 IntelliTest：
  * 观看[第 9 频道视频](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * 阅读 [MSDN 杂志的概述](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * 阅读[文档](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)
* 在 [stackoverflow](http://stackoverflow.com/questions/tagged/intellitest) 上提问
* 阅读此参考手册的其余部分
* 打印此页以供快速参考

<a name="important-attributes"></a>
## <a name="important-attributes"></a>重要属性

* [PexClass](attribute-glossary.md#pexclass) 标记包含 PUT 的类型
* [PexMethod](attribute-glossary.md#pexmethod) 标记 PUT
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) 标记非 null 参数 

```
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) 将测试项目绑定到一个项目
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) 指定要检测的程序集

```
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

<a name="helper-classes"></a>
## <a name="important-static-helper-classes"></a>重要的静态帮助程序类

* [PexAssume](static-helper-classes.md#pexassume) 评估假设（输入筛选）
* [PexAssert](static-helper-classes.md#pexassert) 评估断言
* [PexChoose](static-helper-classes.md#pexchoose) 生成新选项（其他输入）
* [PexObserve](static-helper-classes.md#pexobserve) 将实时值记录到生成的测试中

```
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>是否获得反馈？

在 [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest) 上发布想法和功能请求。

