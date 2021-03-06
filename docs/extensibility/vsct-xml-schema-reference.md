---
title: VSCT XML 스키마 참조 | Microsoft Docs
description: VSCT XML 스키마 참조 문서에서는 각에 대해 허용 되는 자식 요소 및 특성을 사용 하 여 명령 테이블 컴파일러 스키마 요소에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56d6c1309dc5b9a52de0bc0b54a764eceaf37d96
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863985"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 스키마 참조
각에 대해 허용 되는 자식 요소 및 특성을 포함 하는 명령 테이블 컴파일러 스키마 요소 테이블을 제공 합니다.

 XML 기반 명령 테이블 구성 (VSPackage) 파일은 IDE (통합 개발 환경)에 제공 되는 명령 요소를 정의 합니다. 이러한 요소에는 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 포함 됩니다.

> [!NOTE]
> VSCT 컴파일러는. vsct 파일에서 전처리기를 실행할 수 있습니다. 일반적으로 c + + 전처리기 이므로 c + + 파일에서 사용 되는 것과 동일한 구문을 포함 하는 및 매크로를 정의할 수 있습니다. 이에 대 한 예는 **새 프로젝트** 마법사에서 VSPackage 프로젝트에 대해 만드는 vsct 파일에 제공 됩니다.

## <a name="optional-elements"></a>선택적 요소
 일부 VSCT 요소는 선택 사항입니다. 인수를 `Parent` 지정 하지 않으면 Group_Undefined 0입니다. 이 (가) 포함 됩니다. 인수를 `Icon` 지정 하지 않으면 guidOfficeIcon: msotcidNoIcon이 포함 됩니다. 바로 가기 키가 정의 된 경우 일반적으로 사용 되지 않는 에뮬레이션은 선택 사항입니다.

 비트맵 항목은 인수에서 비트맵 스트립의 위치를 지정 하 여 컴파일 타임에 포함 될 수 있습니다 `href` . 비트맵 스트립은 DLL의 리소스에서 추출 하지 않고 병합 중에 복사 됩니다. 인수를 제공 하는 경우 `href` `usedList` 인수는 선택 사항이 되며 비트맵 스트립의 모든 슬롯을 사용 하는 것으로 간주 됩니다.

 모든 GUID 및 ID 값은 심볼 이름을 사용 하 여 정의 해야 합니다. 이러한 이름은 헤더 파일 또는 VSCT 섹션에서 정의할 수 있습니다 \<Symbols> . 기호화 된 이름은 요소를 통해 포함 되거나 요소에 \<Include> 의해 참조 되는 로컬 이어야 합니다 \<Extern> . \<Extern>#Define 기호 값의 단순 패턴을 따르는 경우 요소에 지정 된 헤더 파일에서 기호화 된 이름을 가져옵니다. 기호가 이전에 정의 된 경우 값은 다른 기호가 될 수 있습니다. GUID 정의는 OLE 또는 c + + 형식을 따라야 합니다. ID 값은 다음 줄에 표시 된 것 처럼 0x가 앞에 오는 10 진수 또는 10 진수 일 수 있습니다.

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xcb}}

  XML 주석을 사용할 수도 있지만 라운드트립 그래픽 사용자 인터페이스 (GUI) 도구는 이러한 주석을 삭제할 수 있습니다. 요소의 콘텐츠는 \<Annotation> 형식에 관계 없이 유지 됩니다.

## <a name="schema-hierarchy"></a>스키마 계층 구조
 . Vsct 파일에는 다음과 같은 주요 요소가 있습니다.

- [CommandTable 요소](../extensibility/commandtable-element.md)

- [Extern 요소](../extensibility/extern-element.md)

- [Include 요소](../extensibility/include-element.md)

- [Define 요소](../extensibility/define-element.md)

- [Commands 요소](../extensibility/commands-element.md)

- [CommandPlacements 요소](../extensibility/commandplacements-element.md)

- [VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)

- [KeyBindings 요소](../extensibility/keybindings-element.md)

- [UsedCommands 요소](../extensibility/usedcommands-element.md)

- [부모 요소](../extensibility/parent-element.md)

- [Icon 요소](../extensibility/icon-element.md)

- [Strings 요소](../extensibility/strings-element.md)

- [명령 플래그 요소](../extensibility/command-flag-element.md)

- [기호 요소](../extensibility/symbols-element.md)

- [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>추가 정보
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vspackage의 명령 라우팅](../extensibility/internals/command-routing-in-vspackages.md)
