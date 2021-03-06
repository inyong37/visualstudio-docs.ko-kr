---
title: new() 사용
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b2091c046efac9f5676e5d2d99ef798283b95f6e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403556"
---
# <a name="use-new"></a>`new()` 사용

적용 대상:

- C#

**내용:** `new()`을 사용하십시오.

**시기:** `var`을 사용할 수 없는 필드 또는 `var`을 사용하지 않는 코드 스타일 기본 설정이 있습니다.

**이유:** 따라서 형식을 두 번 반복하여 반복되는 코드를 작성할 필요가 없습니다.

## <a name="how-to"></a>방법

1. 필드 선언에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. **‘new(...)’ 사용** 을 선택합니다.

    ![‘new(...)’ 사용](media/use-new.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
