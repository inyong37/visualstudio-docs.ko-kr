---
title: 레거시 언어 서비스의 코드 주석 처리 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3314d27ce81e48237fa69b332b203d557d0a11d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47542142"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 주석 처리
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [레거시 언어 서비스의 코드 주석 처리](https://docs.microsoft.com/visualstudio/extensibility/internals/commenting-code-in-a-legacy-language-service)합니다.  
  
프로그래밍 언어는 일반적으로 주석을 추가 하거나 코드를 주석 처리 하는 수단을 제공 합니다. 주석을 코드에 대 한 추가 정보를 제공 하지만 컴파일 또는 해석 하는 중에 무시 되는 텍스트의 섹션을입니다.  
  
 관리 되는 패키지 프레임 워크 (MPF) 클래스는 선택한 텍스트를 주석 처리 및 주석 처리 제거에 대 한 지원을 제공합니다.  
  
## <a name="comment-styles"></a>주석 스타일  
 주석의 일반 스타일 두 가지가 있습니다.  
  
1.  한 줄에 주석 인 줄 주석입니다.  
  
2.  블록 주석에서 주석에서 여러 줄을 포함할 수는 경우입니다.  
  
 줄 주석은 일반적으로 시작 문자 (또는 문자), 블록 주석 하는 동안 시작 및 끝 문자를 포함할 수 있습니다. 예를 들어 C#에서는 줄 주석 시작 / /, 블록 주석 시작 및 / * 끝나는 \*/입니다.  
  
 사용자가 명령을 선택할 때 **주석 선택** 에서 합니다 **편집** -> **고급** 메뉴 명령으로 라우팅됩니다는 <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.Source> 클래스입니다. 사용자가 명령을 선택할 때 **주석 선택**, 명령이 라우팅되는 <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> 메서드.  
  
## <a name="supporting-code-comments"></a>지원 코드 주석  
 언어 서비스 지원 코드 설명을 통해 할 수 있습니다는 `EnableCommenting` 라는 매개 변수를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 합니다. 이 설정의 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> 의 속성을 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스. 언어 servicce 기능을 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 반환 하는 방법을 <xref:Microsoft.VisualStudio.Package.CommentInfo> 언어에 대 한 주석 문자를 사용 하 여 구조입니다. C#-스타일 줄 주석 문자는 기본값입니다.  
  
### <a name="example"></a>예제  
 여기서는의 구현 예제는 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 메서드.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)   
 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
