---
title: 'IDebugCustomAttributeQuery2:: EnumCustomAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b00ead2236a36c2fa12e1ad154b9f853aa2224d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732595"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
이 필드에 연결 된 모든 사용자 지정 특성에 대 한 열거자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 사용자 지정 특성의 목록을 나타내는 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 개체를 반환 합니다. 그렇지 않으면 사용자 지정 특성이 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 필드에 사용자 지정 특성이 없는 경우 S_OK 또는 S_FALSE을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 필드에는 여러 사용자 지정 특성이 있을 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
