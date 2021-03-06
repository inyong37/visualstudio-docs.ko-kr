---
title: NotifyDebuggerOfWaitCompletion 메서드 | Microsoft Docs
description: 디버거에서 중단점 대상으로 사용 되는 자리 표시자 인 NotifyDebuggerOfWaitCompletion 메서드에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606634"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion 메서드
디버거에서 중단점 대상으로 사용 되는 자리 표시자 메서드입니다. 이 메서드는 인라인 또는 최적화 되지 않아야 합니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

## <a name="syntax"></a>구문

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>설명
 작업에 대 한 모든 조인 작업은 디버거 알림 비트가 설정 된 경우이 메서드를 호출 해야 합니다.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참고 항목
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
