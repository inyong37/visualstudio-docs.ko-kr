---
title: 식 계산기 구현 전략 | Microsoft Docs
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
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bb9135dda7b5c8240517efabb3a899022ba1d3d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541793"
---
# <a name="expression-evaluator-implementation-strategy"></a>식 계산기 구현 전략
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [식 계산기 구현 전략](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluator-implementation-strategy)합니다.  
  
> [!IMPORTANT]
>  Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 식 계산기 (EE)를 신속 하 게 만드는 한 가지 방법은 먼저 지역 변수를 표시 하는 데 필요한 최소한의 코드를 구현 하는 것은 **지역** 창입니다. 한다는 것을 알아야 하는 데 유용의 각 줄을 **지역** 이름, 형식 및 로컬 변수를 값 창에 표시 하 고 모든 세으로 표현 되는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체입니다. 이름, 형식 및 지역 변수 값에서 얻을 수 있습니다는 `IDebugProperty2` 개체를 호출 하 여 해당 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드. 지역 변수를 표시 하는 방법에 대 한 자세한 합니다 **지역** 창 참조 [지역 표시](../../extensibility/debugger/displaying-locals.md)합니다.  
  
## <a name="discussion"></a>토론  
 구현으로 가능한 구현 시퀀스 시작 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)합니다. 합니다 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 하며 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 메서드 구현 지역 변수를 표시 하는 데 필요 합니다. 호출 `IDebugExpressionEvaluator::GetMethodProperty` 반환을 `IDebugProperty2` 메서드를 나타내는 개체: 즉,는 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 개체입니다. 메서드 자체에 표시 되지 않습니다 합니다 **지역** 창입니다.  
  
 합니다 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 다음 메서드를 구현 해야 합니다. 디버그 엔진 (DE)를 전달 하 여 지역 변수 및 인수 목록을 가져오려면이 메서드를 호출 `IDebugProperty2::EnumChildren` 는 `guidFilter` 인수의 `guidFilterLocalsPlusArgs`합니다. `IDebugProperty2::EnumChildren` 호출 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 하 고 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), 단일 열거에 결과 결합 합니다. 참조 [지역 표시](../../extensibility/debugger/displaying-locals.md) 대 한 자세한 내용은 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [식 계산기 구현](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)
