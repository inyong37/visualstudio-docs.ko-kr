---
title: 워크플로 디자이너-Assign 활동 디자이너
description: Assign 활동 디자이너를 사용 하 여 Assign 활동을 만들고 구성 하는 방법과 Assign 활동에서 변수 또는 인수에 값을 할당 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d8601951cfaba3f246e8488ab23c9b6ccad0d01
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438193"
---
# <a name="assign-activity-designer"></a>Assign 활동 디자이너

**Assign** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Assign> .

## <a name="the-assign-activity"></a>Assign 활동

<xref:System.Activities.Statements.Assign> 활동은 변수 또는 인수에 값을 할당합니다.

### <a name="using-the-assign-activity-designer"></a>Assign 활동 디자이너 사용

**Assign** 활동 디자이너 **는 도구 상자** 의 **기본 형식** 범주에 있습니다 .이 범주에 액세스 하려면 **도구 상자** 탭을 클릭 하거나, **보기** 메뉴에서 **도구 상자** 를 선택 하거나, CTRL + ALT + X를 선택 합니다.

**Assign** 활동 디자이너를 **도구 상자** 에서 끌어다와 같이 활동을 배치할 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . **Assign** 활동 디자이너를 삭제 하면 <xref:System.Activities.Statements.Assign> Default **DisplayName** 이 assign 인 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **Assign** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

### <a name="the-assign-properties"></a>Assign 속성

다음 표에서는 <xref:System.Activities.Statements.Assign> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|거짓|<xref:System.Activities.Statements.Assign> 활동의 이름입니다. 기본값은 Assign입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Assign.To%2A>|참|<xref:System.Activities.Statements.Assign.Value%2A>가 할당되는 변수 또는 인수입니다. 값은 유효한 Visual Basic 식별자 여야 합니다. 속성을 설정 하려면 **Assign** 활동 디자이너의 **대상** 상자 또는 속성 표에 Visual Basic 식을 입력 합니다.|
|<xref:System.Activities.Statements.Assign.Value%2A>|참|변수에 할당된 값입니다. 을 설정 하려면 <xref:System.Activities.Statements.Assign.Value%2A> **Assign** 활동 디자이너의 **값** 상자 또는 속성 표에 Visual Basic 식을 입력 합니다.|

## <a name="see-also"></a>참조

- [기본 형식](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)