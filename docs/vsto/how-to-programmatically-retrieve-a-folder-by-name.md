---
title: '방법: 프로그래밍 방식으로 이름으로 폴더 검색'
description: Visual Studio를 사용 하 여 이름별로 폴더를 프로그래밍 방식으로 검색 한 다음 폴더의 내용을 표시 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4e615897fedcbfa41ad7958e93354718d9ccfbc
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528571"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>방법: 프로그래밍 방식으로 이름으로 폴더 검색
  이 예제에서는 명명 된 사용자 지정 폴더에 대 한 참조를 가져온 다음 폴더의 내용을 표시 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 사항이 필요합니다.

- TestFolder 라는 폴더

## <a name="see-also"></a>참고 항목
- [폴더 작업](../vsto/working-with-folders.md)
- [방법: 프로그래밍 방식으로 특정 폴더 내에서 검색](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [방법: 프로그래밍 방식으로 특정 연락처 검색](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [방법: 프로그래밍 방식으로 사용자 지정 폴더 항목 만들기](../vsto/how-to-programmatically-create-custom-folder-items.md)
