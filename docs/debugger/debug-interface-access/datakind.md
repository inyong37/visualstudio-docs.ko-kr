---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31be0615fd7d1da279ecf414260af21cb8239dc8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745283"
---
# <a name="datakind"></a>DataKind
데이터 값의 특정 범위를 나타냅니다.

## <a name="syntax"></a>구문

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>요소
DataIsUnknown 데이터 기호를 확인할 수 없습니다.

DataIsLocal 데이터 항목은 지역 변수입니다.

DataIsStaticLocal 데이터 항목은 정적 지역 변수입니다.

DataIsParam 데이터 항목은 정식 매개 변수입니다.

DataIsObjectPtr 데이터 항목은 개체 포인터 (`this`)입니다.

DataIsFileStatic 데이터 항목은 파일 범위 변수입니다.

DataIsGlobal 데이터 항목이 전역 변수입니다.

DataIsMember 데이터 항목은 개체 멤버 변수입니다.

DataIsStaticMember 데이터 항목은 클래스 정적 변수입니다.

DataIsConstant 데이터 항목은 상수 값입니다.

## <a name="remarks"></a>주의
이 열거형의 값은 [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) 메서드에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
