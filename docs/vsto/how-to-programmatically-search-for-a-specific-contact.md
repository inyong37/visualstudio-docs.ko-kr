---
title: '방법: 프로그래밍 방식으로 특정 연락처 검색'
description: Visual Studio를 사용 하 여 Microsoft Outlook에서 특정 연락처를 프로그래밍 방식으로 검색 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6813a137558a245c66d4b24deac07b1a6a77796a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524604"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>방법: 프로그래밍 방식으로 특정 연락처 검색
  이 예제에서는 특정 연락처에 대해 성 및 이름으로 Outlook 연락처 폴더를 검색합니다. 이 예제에서는 **John Evans** 라는 이름의 연락처가 연락처 폴더에 있다고 가정합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>참고 항목
- [연락처 항목 작업](../vsto/working-with-contact-items.md)
- [VSTO 추가 기능 프로그래밍 시작](../vsto/getting-started-programming-vsto-add-ins.md)
