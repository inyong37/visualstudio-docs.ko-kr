---
title: 클래스 다이어그램에 UML 작업의 속성 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: e977ede02f355724f1a93f82f1c688de27e36fa6
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592715"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>UML 클래스 다이어그램 작업의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [클래스 다이어그램에 UML 작업의 속성](https://docs.microsoft.com/visualstudio/modeling/properties-of-operations-on-uml-class-diagrams)합니다.  
  
UML 클래스 다이어그램을 추가할 수 있습니다 *operations* 클래스 및 인터페이스에 있습니다. 작업은 클래스 또는 인터페이스 인스턴스에서 수행할 수 있는 메서드 또는 함수입니다.  
  
 작업을 추가 하는 클래스 또는 인터페이스를 마우스 오른쪽 단추로 클릭, 가리킨 **추가**를 클릭 하 고 **작업**합니다.  
  
 다이어그램에 클래스 작업이 표시되지 않으면 클래스 또는 인터페이스 맨 위에 있는 확장 펼침 단추를 클릭합니다. 표시 되는 경우는 **작업이** 헤더를 클릭 **[+]** 작업 섹션을 확장 합니다.  
  
## <a name="signature-of-an-operation"></a>작업 서명  
 작업 서명은 UML 클래스 다이어그램의 클래스 또는 인터페이스에서 서명을 나타내는 텍스트 줄입니다. 이 형식 지정자의 형식은 다음과 같습니다.  
  
 \+ OperationName (매개 변수 1: Type1 [*],...): ReturnType [\*]  
  
 \+ 공용 표시 여부를 나타냅니다. 기타 허용되는 값은 -(private), #(protected), ~(package)입니다.  
  
 `OperationName` 에 밑줄이 표시는 **정적** 속성은 true이 고 기울임꼴인지 경우는 **추상** 속성이 true입니다.  
  
 정의된 반환 형식이 없으면 `: ReturnType`이 생략됩니다.  
  
 `[*]`는 매개 변수 또는 반환 형식의 복합성을 나타냅니다. 복합성이 1이면 생략됩니다.  
  
 이러한 속성에 대한 자세한 내용은 다음 섹션을 참조하세요.  
  
## <a name="properties"></a>속성  
 UML 클래스 다이어그램의 클래스 또는 인터페이스에 있는 작업의 속성입니다.  
  
 작업의 속성을 보려면 다이어그램에서 클래스 또는 인터페이스의 작업을 마우스 오른쪽 단추로 클릭 하 고 클릭 **속성**합니다. 속성에 표시 된 **속성** 창입니다.  
  
|속성|기본값|설명|  
|--------------|-------------|-----------------|  
|**이름**|(새 이름)|포함하는 형식 내에서 고유해야 합니다.|  
|**매개 변수**|(없음)|형식 목록을 _이름_**:**_형식_**하십시오** _이름_**:**  _형식_**,...** 클릭 **[...]**  목록을 편집 합니다.<br /><br /> 형식은 기본 형식 또는 모델에 정의된 형식일 수 있습니다. 이 속성에 새 형식의 이름을 입력하면 형식이 UML 모델 탐색기의 **지정되지 않은 형식** 섹션에 추가됩니다.|  
|**반환 형식**|(없음)|**(없음)** , 기본 형식 또는 모델에 정의 된 형식입니다. 이 속성에 새 형식의 이름을 입력하면 형식이 UML 모델 탐색기의 **지정되지 않은 형식** 섹션에 추가됩니다.|  
|**사후 조건**|(없음)|작업 실행 전후에 시스템 상태 간의 관계를 지정하는 선택적 조건입니다.|  
|**사전 조건**|(없음)|작업 실행이 시작되기 전에 시스템 상태에 대한 가정을 지정하는 선택적 조건입니다.|  
|**본문 조건**|(없음)|작업에서 반환되는 값에 대한 선택적 제약 조건입니다.|  
|**표시 유형**|Public|허용되는 값 및 서명에 나타나는 문자는 다음과 같습니다.<br /><br /> **+ Public** - 전체적으로 표시됩니다.<br /><br /> **- Private** - 소유하는 형식 외부에 표시되지 않습니다.<br /><br /> **# Protected** - 소유자로부터 파생된 형식에 표시됩니다.<br /><br /> **~ Package** - 같은 패키지 내의 다른 형식에 표시됩니다.|  
|**서명**|+*이름*)|이 작업의 표시 유형, 이름, 매개 변수 및 반환 형식을 요약합니다. 다이어그램에서 서명을 편집하거나 개별 속성을 편집하여 이러한 속성을 변경할 수 있습니다.|  
|**작업 항목**|0 associated|연결된 작업 항목 개수입니다. 읽기 전용입니다.<br /><br /> 자세한 내용은 [모델 요소에 연결 하 고 작업 항목](../modeling/link-model-elements-and-work-items.md)합니다.|  
|**동시성**|순차|**순차** -작업이 동시성 제어 없이 디자인 되었거나 합니다. 이 작업을 동시에 호출할 경우 오류가 발생할 수 있습니다.<br /><br /> **보호 된** -다른 인스턴스가 완료 될 때까지 작업이 자동으로 차단 됩니다.<br /><br /> **동시** -작업은 여러 호출을 동시에 실행할 수 있도록 디자인 되었습니다.|  
|**정적**|False|true이면 이 작업이 이 형식의 모든 인스턴스 간에 공유됩니다.<br /><br /> true이면 다이어그램에서 작업 이름에 밑줄이 추가됩니다.|  
|**추상 클래스**|False|true이면 이 작업과 연결된 코드가 없습니다. 따라서 소유 클래스가 추상 클래스입니다.|  
|**리프는**|False|디자이너가 파생 클래스에서 이 작업을 재정의할 수 없도록 설정합니다.|  
|**쿼리는**|False|true이면 이 작업에 의해 시스템 상태가 크게 변경되지 않습니다. 따라서 예를 들어 시스템 상태를 확인하는 테스트에서 사용할 수 있습니다.|  
|**다중성**|1|**1** -지정 된 형식의 단일 값입니다.<br /><br /> **0..1** -수 `null`입니다.<br /><br /> \* -지정 된 형식의 값의 컬렉션입니다.<br /><br /> **1..\***  -하나 이상의 값을 포함 하는 컬렉션입니다.<br /><br /> *n* `..` *m* -포함 된 컬렉션 `n` 고 `m` 값입니다.|  
|**정렬**|False|true이면 컬렉션이 순차적 목록을 구성합니다. 에 대 한 **복합성** 개.|  
|**고유한**|False|true이면 컬렉션에 중복 값이 없습니다. 에 대 한 **복합성** 개.|  
  
## <a name="see-also"></a>참고 항목  
 [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)   
 [UML 클래스 다이어그램 형식의 속성](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML 클래스 다이어그램 특성의 속성](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML 클래스 다이어그램 연결의 속성](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)


