---
title: EVALFLAGS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 088c63fb1683bdf277ed1c3c5aba06a3156efbbf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47550347"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [EVALFLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/evalflags)합니다.  
  
식 계산을 제어 하는 플래그를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>멤버  
 EVAL_RETURNVALUE  
 있는 경우 반환 값을 평가 하는 것을 지정 합니다.  
  
 EVAL_NOSIDEEFFECTS  
 파생 작업이 허용 되지 않음을 지정 합니다.  
  
 EVAL_ALLOWBPS  
 중단점에서 중지를 지정합니다.  
  
 EVAL_ALLOWERRORREPORT  
 오류 수를 보고 호스트를 지정 합니다. Internet Explorer에서 스크립트의 식 평가 위해 주로 사용 됩니다.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 함수를 호출 하는 대신 주소로 평가할 강제로 함수입니다.  
  
 EVAL_NOFUNCEVAL  
 함수를에서 확인할 수 없습니다. 예를 들어 합니다 `int` 식에서 토큰 `myExpression(int) + 10`합니다. 이 함수는 주소로 아니지만 값을 올바르게 평가할 수 있습니다.  
  
 EVAL_NOEVENTS  
 식 평가 중 발생 하는 이벤트를 보내지 세션 디버그 관리자 (SDM) 또는 IDE를 표시 하는 플래그입니다.  
  
## <a name="remarks"></a>설명  
 이러한 플래그에 대 한 인수로 전달 되는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 하 고 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 메서드.  
  
 이러한 플래그는 비트 OR 연산자를 사용 하 여 결합할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
