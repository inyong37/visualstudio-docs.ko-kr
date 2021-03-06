---
title: 소스 제어 플러그 인 아키텍처 | Microsoft Docs
description: 소스 제어 플러그 인을 구현 하 고 연결 하 여 Visual Studio IDE에 소스 제어 지원을 추가 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e154e91ce552df9e54d45ea9210a0679edae5f28
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878068"
---
# <a name="source-control-plug-in-architecture"></a>소스 제어 플러그 인 아키텍처
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]소스 제어 플러그 인을 구현 하 고 연결 하 여 IDE (통합 개발 환경)에 소스 제어 지원을 추가할 수 있습니다. IDE는 잘 정의 된 소스 제어 Plug-In API를 통해 소스 제어 플러그 인에 연결 합니다. IDE는 도구 모음 및 메뉴 명령으로 구성 된 UI (사용자 인터페이스)를 제공 하 여 소스 제어 시스템의 버전 제어 기능을 노출 합니다. 소스 제어 플러그 인은 소스 제어 기능을 구현 합니다.

## <a name="source-control-plug-in-resources"></a>소스 제어 플러그 인 리소스
 소스 제어 플러그 인은 버전 관리 응용 프로그램을 만들고 IDE에 연결 하는 데 도움이 되는 리소스를 제공 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 소스 제어 플러그 인에는 IDE에 통합 될 수 있도록 소스 제어 플러그 인에서 구현 해야 하는 API 사양이 포함 되어 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 또한 소스 제어 플러그 인 API를 준수 하는 필수 기능의 구현을 보여 주는 기본 소스 제어 플러그 인을 구현 하는 코드 샘플 (c + +로 작성 됨)이 포함 되어 있습니다.

 소스 제어 플러그 인 api 사양을 사용 하면 소스 제어 플러그 인 API에 따라 구현 된 필요한 함수 집합을 사용 하 여 소스 제어 DLL을 만드는 경우 소스 제어 플러그 인 API 사양을 사용 하 여 원하는 소스 제어 시스템을 활용할 수 있습니다.

## <a name="components"></a>구성 요소
 다이어그램의 원본 제어 어댑터 패키지는 소스 제어 작업에 대 한 사용자의 요청을 소스 제어 플러그 인에서 지 원하는 함수 호출로 변환 하는 IDE의 구성 요소입니다. 이렇게 하려면 IDE 및 소스 제어 플러그 인에 IDE와 플러그 인 간에 정보를 전달 하는 효과적인 대화 상자가 있어야 합니다. 이 대화 상자를 실행 하려면 둘 다 같은 언어를 사용 해야 합니다. 이 설명서에 설명 된 소스 제어 플러그 인 API는이 교환에 대 한 일반적인 용어입니다.

 ![소스 코드 제어 아키텍처 다이어그램](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") VS와 소스 제어 플러그 인 간의 상호 작용을 보여 주는 아키텍처 다이어그램

 아키텍처 다이어그램에 표시 된 것 처럼 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다이어그램에서 VS shell으로 레이블이 있는 셸은 사용자의 작업 프로젝트 및 편집기 및 솔루션 탐색기와 같은 관련 구성 요소를 호스팅합니다. 소스 제어 어댑터 패키지는 IDE와 소스 제어 플러그 인 간의 상호 작용을 처리 합니다. 원본 제어 어댑터 패키지는 자체 소스 제어 UI를 제공 합니다. 이는 소스 제어 작업의 범위를 시작 하 고 정의 하기 위해 사용자가 상호 작용 하는 최상위 UI입니다.

 소스 제어 플러그 인에는 그림에 표시 된 것 처럼 두 부분으로 구성 될 수 있는 자체 UI가 있을 수 있습니다. "공급 업체 UI" 라는 상자는 소스 제어 플러그 인 작성자가 제공 하는 사용자 지정 사용자 인터페이스 요소를 나타냅니다. 이러한 작업은 사용자가 고급 소스 제어 작업을 호출할 때 소스 제어 플러그 인에서 직접 표시 됩니다. "도우미 UI" 라는 상자는 IDE를 통해 간접적으로 호출 되는 소스 제어 플러그 인 UI 기능의 집합입니다. 소스 제어 플러그 인은 IDE에서 제공 하는 특수 콜백 함수를 통해 UI 관련 메시지를 IDE에 전달 합니다. 도우미 UI는 IDE와의 원활한 통합을 용이 하 게 해줍니다 (종종 **고급** 단추를 사용 하 여). 따라서 보다 통합 된 최종 사용자 환경을 제공 합니다.

 소스 제어 플러그 인은 셸을 변경할 수 없으며 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , 그에 따라 소스 제어 어댑터 패키지 또는 IDE에서 제공 하는 소스 제어 UI를 변경할 수 없습니다. 최종 사용자에 게 통합 된 환경에 영향을 주는 다양 한 소스 제어 플러그 인 API 함수의 구현을 통해 제공 되는 유연성을 최대한 활용 해야 합니다. 소스 제어 플러그 인 API 설명서의 참조 섹션에는 일부 고급 소스 제어 플러그 인 기능에 대 한 정보가 포함 되어 있습니다. 이러한 기능을 이용 하려면 초기화 하는 동안 소스 제어 플러그 인에서 IDE에 대 한 고급 기능을 선언 하 고 각 기능에 대 한 특정 고급 함수를 구현 해야 합니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)
- [용어](../../extensibility/source-control-plug-in-glossary.md)
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
