---
title: 사용자 지정 디버그 엔진 만들기 | Microsoft Docs
description: 이러한 문서를 사용 하 여 특정 런타임 아키텍처의 디버깅을 허용 하는 디버그 엔진을 만드는 방법을 알아보세요.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 673b08bf5680e04c90376c9eb3d63f6f03df9723
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914194"
---
# <a name="create-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 만들기
DE (디버그 엔진)는 특정 런타임 아키텍처의 디버깅을 허용 하는 구성 요소입니다. 일반적으로 런타임 환경 마다 하나의 DE-DE 구현이 있습니다.

> [!NOTE]
> Transact-sql 및 JScript에 대 한 별도의 DE 구현이 있지만 VBScript 및 JScript는 단일 DE를 공유 합니다.

 DE는 인터프리터 또는 운영 체제와 함께 작동 하 여 실행 제어, 중단점 및 식 계산으로 이러한 디버깅 서비스를 제공 합니다. 이러한 서비스는 DE 인터페이스를 통해 구현 되며 디버거가 여러 작업 모드 간에 전환 될 수 있습니다. 자세한 내용은 [운영 모드](../../extensibility/debugger/operational-modes.md)를 참조 하세요.

 DE를 만드는 과정은 다음 단계로 구성 됩니다.

1. Visual Studio를 사용 하 여 DE 등록

2. 디버깅할 프로그램 사용

3. 실행 제어 및 상태 평가 구현

4. 이벤트 보내기

5. 종료 및 분리 설정

## <a name="in-this-section"></a>섹션 내용
 [사용자 지정 디버그 엔진 등록](../../extensibility/debugger/registering-a-custom-debug-engine.md) 디버그 엔진을 사용할 수 있도록 Visual Studio에 등록 하는 데 필요한 단계에 대해 설명 합니다.

 [디버깅할 프로그램 사용](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) DE가 프로그램을 디버깅 하려면 먼저 DE를 시작 하거나 기존 프로그램에 연결 해야 함을 설명 합니다.

 [실행 제어 및 상태 평가 구현](../../extensibility/debugger/execution-control-and-state-evaluation.md) 응용 프로그램을 디버깅 하는 데 실행 제어 기능을 구현 해야 하는 이유에 대해 설명 합니다.

 [이벤트 전송](../../extensibility/debugger/sending-events.md) DCOM을 기반으로 하는 이벤트 모델과 디버거 간의 통신을 설명 합니다.

 [종료 및 분리 설정](../../extensibility/debugger/termination-and-detaching.md) 디버깅할 응용 프로그램에 중단점, 예외, 런타임 오류 또는 무한 루프가 없음을 의미 하는 정상적인 종료를 수행 하는 방법을 설명 합니다.

 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md) 디버깅 세션에서 발생 하는 이벤트의 호출 순서를 문서화 합니다.

 [방법: 사용자 지정 디버그 엔진 디버깅](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) 사용자 지정 DE를 디버깅 하는 방법을 설명 합니다.

## <a name="see-also"></a>참고 항목
- [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
