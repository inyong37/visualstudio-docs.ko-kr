---
title: Icon 요소 (Visual Studio 템플릿) | Microsoft Docs
description: 아이콘 요소와 아이콘 역할을 하는 이미지 파일의 경로 및 파일 이름을 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 059105b9d188c0e7a81252172aa2d1bf7002420c
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672694"
---
# <a name="icon-element-visual-studio-templates"></a>Icon 요소 (Visual Studio 템플릿)
템플릿에 대 한 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 되는 아이콘 역할을 하는 이미지 파일의 경로와 파일 이름을 지정 합니다.

 \<VSTemplate> \<TemplateData>
 \<Icon>

## <a name="syntax"></a>구문

```
<Icon>
    IconFileName
</Icon>
```

```
<Icon Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|`Package`|고급 사용자 시나리오에 대 한 선택적 특성입니다.<br /><br /> Visual Studio 패키지를 ID를 지정하는 GUID입니다.|
|`ID`|고급 사용자 시나리오에 대 한 선택적 특성입니다.<br /><br /> Visual Studio 리소스 ID를 지정합니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 `Package` 및 `ID` 특성이 사용되는 경우가 아니면 텍스트 값은 필수입니다.

 텍스트는 **새 프로젝트** 대화 상자에 표시 되는 템플릿 아이콘의 경로 및 파일 이름을 제공 합니다.

## <a name="remarks"></a>설명
 `Icon`은 `TemplateData`의 필수 자식 요소입니다.

## <a name="example"></a>예제
 다음 예제에서는 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
