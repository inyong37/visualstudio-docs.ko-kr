---
title: 텍스트 템플릿 유틸리티 메서드
description: Visual Studio에서 코드를 작성할 때 사용할 수 있는 다양 한 텍스트 템플릿 유틸리티 메서드에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b0015e68f7d78c2b33eaeb9e0bfb404acaed834
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362017"
---
# <a name="text-template-utility-methods"></a>텍스트 템플릿 유틸리티 메서드

Visual Studio 텍스트 템플릿에서 코드를 작성할 때 항상 사용할 수 있는 몇 가지 방법이 있습니다. 이러한 메서드는에 정의 되어 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 있습니다.

> [!TIP]
> 또한 일반 (전처리 되지 않은) 텍스트 템플릿에서 호스트 환경에서 제공 하는 다른 메서드 및 서비스를 사용할 수 있습니다. 예를 들어 파일 경로를 확인 하 고, 오류를 기록 하 고, Visual Studio 및 로드 된 모든 패키지에서 제공 하는 서비스를 가져올 수 있습니다. 자세한 내용은 [텍스트 템플릿에서 Visual Studio에 액세스](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))를 참조 하세요.

## <a name="write-methods"></a>Write 메서드

`Write()` `WriteLine()` 식 코드 블록을 사용 하는 대신 및 메서드를 사용 하 여 표준 코드 블록 내에 텍스트를 추가할 수 있습니다. 다음 두 코드 블록은 기능적으로 동일 합니다.

### <a name="code-block-with-an-expression-block"></a>식 블록이 포함 된 코드 블록

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>WriteLine ()을 사용 하는 코드 블록

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

중첩 된 컨트롤 구조의 긴 코드 블록 내에서 식 블록 대신 이러한 유틸리티 메서드 중 하나를 사용 하는 것이 유용할 수 있습니다.

`Write()`및 `WriteLine()` 메서드에는 두 개의 오버 로드가 있습니다. 하나는 단일 문자열 매개 변수를 사용 하 고 다른 하나는 복합 서식 문자열과 문자열에 포함할 개체의 배열을 사용 합니다 (예: `Console.WriteLine()` 메서드). 다음 두 가지 사용은 `WriteLine()` 기능적으로 동일 합니다.

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>들여쓰기 메서드

들여쓰기 메서드를 사용 하 여 텍스트 템플릿의 출력 형식을 지정할 수 있습니다. 클래스에는 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> `CurrentIndent` 텍스트 템플릿의 현재 들여쓰기를 표시 하는 문자열 속성과 `indentLengths` 추가 된 들여쓰기의 목록 필드가 있습니다. 메서드를 사용 하 여 들여쓰기를 추가 `PushIndent()` 하 고 메서드를 사용 하 여 들여쓰기를 뺄 수 있습니다 `PopIndent()` . 모든 들여쓰기를 제거 하려면 메서드를 사용 `ClearIndent()` 합니다. 다음 코드 블록에서는 이러한 메서드를 사용 하는 방법을 보여 줍니다.

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

이 코드 블록은 다음과 같은 출력을 생성 합니다.

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Error 및 warning 메서드

오류 및 경고 유틸리티 메서드를 사용 하 여 Visual Studio 오류 목록에 메시지를 추가할 수 있습니다. 예를 들어 다음 코드는 오류 목록에 오류 메시지를 추가 합니다.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>호스트 및 서비스 공급자에 대 한 액세스

속성은 `this.Host` 템플릿을 실행 하는 호스트에서 노출 하는 속성에 대 한 액세스를 제공할 수 있습니다. 을 사용 하려면 `this.Host` `hostspecific` 지시문에서 특성을 설정 해야 합니다 `<@template#>` .

`<#@template ... hostspecific="true" #>`

의 유형은 `this.Host` 템플릿이 실행 되는 호스트 유형에 따라 달라 집니다. Visual Studio에서 실행 되는 템플릿에서로 캐스팅 하 여 `this.Host` `IServiceProvider` IDE와 같은 서비스에 액세스할 수 있습니다. 예를 들어:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>다른 유틸리티 메서드 집합 사용

텍스트 생성 프로세스의 일부로 템플릿 파일은 항상로 명명 되 고에서 상속 되는 클래스로 변환 됩니다 `GeneratedTextTransformation` <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . 대신 다른 메서드 집합을 사용 하려는 경우 고유한 클래스를 작성 하 고 템플릿 지시문에서 지정할 수 있습니다. 클래스는에서 상속 해야 합니다 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

지시문을 사용 `assembly` 하 여 컴파일된 클래스를 찾을 수 있는 어셈블리를 참조 합니다.
