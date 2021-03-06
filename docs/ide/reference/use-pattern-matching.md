---
title: 패턴 일치 사용
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8cafcb7e4e108258ddfb274ba957024b92fadb01
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403557"
---
# <a name="use-pattern-matching"></a>패턴 일치 사용

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 패턴 일치를 사용합니다.

**시기:** 새로운 [C# 패턴 일치](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-9#pattern-matching-enhancements) 기능을 사용하려고 합니다.

**이유:** 이 리팩터링은 코드를 더욱 명확하고 간결하게 만듭니다.

## <a name="how-to"></a>방법

1. 문 내에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. ‘패턴 일치 사용’을 선택합니다.

    ![클래스를 추상으로 설정](media/use-pattern-matching-not-syntax.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
