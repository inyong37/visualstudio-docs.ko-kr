---
title: 형식 시각화 도우미 및 사용자 지정 뷰어 | Microsoft Docs
description: 특정 형식의 데이터를 표시 하는 사용자 지정 뷰어 및 형식 시각화 요소와 이러한 구성 요소 간의 차이점에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac759dd245da8d803cb943dd6398d9ae642aaf23
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995943"
---
# <a name="type-visualizer-and-custom-viewer"></a>형식 시각화 도우미 및 사용자 지정 뷰어
형식 시각화 도우미는 특정 형식의 데이터를 표시 하는 구성 요소입니다. 형식은 모두 시각화 도우미를 구현 하는 사용자에 게 달려 있습니다. 최종 사용자 또는 시각화 도우미의 타사 공급자 여야 합니다.

 사용자 지정 뷰어는 특정 형식의 데이터를 표시 하는 사용자 지정 식 계산기의 일부입니다. 이 형식은 완전히 사용자 지정 뷰어의 구현자에 의해 결정 됩니다. 즉, 형식은 식 계산기 (EE)의 구현자에 따라 결정 됩니다.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>식 계산기에서 형식 시각화 도우미 지원
 EE는 시각화 도우미에 액세스할 수 있는 인터페이스 집합 (예: [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 및 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md))을 지원 하 여 형식 시각화 도우미를 지원 합니다. 그러나 EE는 형식 시각화 도우미 자체의 구현을 담당 하지 않습니다. EE는 형식 정보에 대 한 외부 시각화 도우미만 액세스할 수 있습니다. 이러한 시각화 도우미는 EE와 함께 제공 되 고 다른 타사 공급 업체 또는 최종 사용자가 제공 하는 Visual Studio의 적절 한 장소에 설치 될 수 있습니다.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>식 계산기의 사용자 지정 뷰어 지원
 EE는 EE 자체에서 데이터 형식 보기를 위한 코드를 제공 하는 사용자 지정 뷰어를 지원할 수도 있습니다. 사용자 지정 뷰어는 원하는 형식으로 데이터를 표시 하는 모든 의무를 처리 하는 [Idebugcustomviewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 인터페이스를 구현 합니다. 뷰어는 표시에 대 한 모든 권한을 가지 며 데이터를 수정 하도록 허용할 수도 있습니다. EE에서 제공 하는 모든 사용자 지정 뷰어는 제품이 배송 될 때 EE와 함께 제공 됩니다.

## <a name="see-also"></a>참고 항목
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
- [식 계산기](../../extensibility/debugger/expression-evaluator.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
