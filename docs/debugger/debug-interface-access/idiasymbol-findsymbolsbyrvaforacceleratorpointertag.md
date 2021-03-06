---
title: 'IDiaSymbol:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0d05946db816e6bd209e364e11d5091163941a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741149"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
해당 태그 값이 지정 된 경우이 메서드는 지정 된 상대 가상 주소에이 스텁 함수에 포함 된 기호의 열거형을 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>매개 변수
 `tagValue`

진행 Pointee 기호 레코드를 찾을 포인터 태그 값입니다.

 `rva`

진행 지정 된 태그 값을 사용 하 여 pointee 변수에 해당 하는 기호를 필터링 하는 데 사용 되는 rva입니다.

 `ppResult`

제한이 결과를 사용 하 여 초기화 되는 `IDiaEnumSymbols` 인터페이스 포인터에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 액셀러레이터 키 함수에 해당 하는 `IDiaSymbol` 인터페이스에 대해서만이 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)