---
title: Menus 요소 | Microsoft Docs
description: Menus 요소는 VSPackage가 구현 하는 모든 메뉴와 도구 모음을 정의 합니다. 이 문서에는 예제가 포함 되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abc5621784579c295393d77c792013dd0c737871
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615579"
---
# <a name="menus-element"></a>Menus 요소
VSPackage가 구현 하는 모든 메뉴와 도구 모음을 정의 합니다.

## <a name="syntax"></a>구문

```xml
<Menus>
  <Menu>... </Menu>
  <Menu>... </Menu>
</Menus>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage가 구현 하는 모든 메뉴와 도구 모음을 정의 합니다.|
|[Menu 요소](../extensibility/menu-element.md)|단일 메뉴 또는 도구 모음을 나타냅니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[Commands 요소](../extensibility/commands-element.md)|VSPackage의 명령 컬렉션을 나타냅니다.|

## <a name="example"></a>예제

```xml
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>참고 항목
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
