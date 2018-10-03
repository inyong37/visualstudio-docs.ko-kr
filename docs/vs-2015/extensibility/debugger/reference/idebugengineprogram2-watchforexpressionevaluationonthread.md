---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
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
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d67290ea7bf88f8cdf01e88444cd69ec25d73a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47543532"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [IDebugEngineProgram2::WatchForExpressionEvaluationOnThread](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread)합니다.  
  
허용 하거나 허용 하지 않습니다 프로그램을 중지 하는 경우에 특정 스레드에서 발생 되는 식 계산.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pOriginatingProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 식을 평가 하는 프로그램을 나타내는 개체입니다.  
  
 `dwTid`  
 [in] 스레드의 식별자를 지정합니다.  
  
 `dwEvalFlags`  
 [in] 플래그의 조합을 합니다 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 평가 수행 하는 방법을 지정 하는 열거형입니다.  
  
 `pExprCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체 식 평가 중에 발생 하는 디버그 이벤트를 보내는 데 사용 됩니다.  
  
 `fWatch`  
 [in] 0이 아닌 경우 (`TRUE`)를 구분 하는 스레드에서 식 평가 허용 `dwTid`이 고, 그렇지 않으면 0 (`FALSE`) 해당 스레드에서 식 평가 허용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 세션 디버그 관리자 (SDM)로 식별 되는 프로그램을 요청 하는 경우는 `pOriginatingProgram` 매개 변수 식을 평가 하려면이 메서드를 호출 하 여 다른 모든 연결 된 프로그램에 알립니다.  
  
 한 프로그램에서 식 계산 함수 평가 또는 모든 평가 인해 다른에서 실행 되도록 코드 않을 `IDispatch` 속성입니다. 이 때문에이 메서드는 실행 하 고이 프로그램에서 스레드를 중지할 수 있습니다 하는 경우에 완료 식 평가 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
