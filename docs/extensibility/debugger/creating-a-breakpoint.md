---
title: 중단점 만들기 | Microsoft Docs
description: 중단점을 바인딩하는 데 필요한 모듈이 로드 될 때 세션 디버그 관리자에서 수행 하는 메서드 호출에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba192a0cda2e63453984d3de7d6007744cc401b7
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914230"
---
# <a name="create-a-breakpoint"></a>중단점 만들기
다음에서는 중단점을 만드는 프로세스에 대해 설명 합니다.

## <a name="methods-in-breakpoint-creation"></a>중단점 생성의 메서드
 중단점을 바인딩하는 데 필요한 모듈이 로드 되 면 세션 디버그 관리자 (SDM)는 다음 메서드를 호출 합니다.

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **Canbind** 는 사용자가 **중단점 창에서 중단점을** 만드는 경우에만 호출 됩니다.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>참고 항목
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
