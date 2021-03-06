---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 632c3611f6c03a47a7d46e985eb6aa2685864a7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735119"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
중단점 요청에 대 한 문서 체크섬을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 패키지에서 구현 되 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 고 디버그 엔진에서 사용 됩니다.

## <a name="methods"></a>메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBreakpointChecksumRequest2` .

|메서드|설명|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|사용할 체크섬 알고리즘의 고유 식별자가 지정 된 경우 중단점 요청에 대 한 문서 체크섬을 검색 합니다.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|이 문서에 체크섬을 사용할 수 있는지 여부를 확인 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
