---
title: 'IDebugProcess2:: GetProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12e575979e5bd1527dfa0d8e15b290d6b78e36ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723910"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
이 프로세스에 대 한 GUID를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>매개 변수
`pguidProcessId`\
제한이 이 프로세스에 대 한 GUID를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 GUID (Globally Unique IDentifier)는 시스템에서 실행 중인 다른 모든 프로세스에서이 프로세스를 식별 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
