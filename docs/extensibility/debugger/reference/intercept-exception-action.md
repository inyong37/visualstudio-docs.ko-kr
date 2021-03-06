---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
description: INTERCEPT_EXCEPTION_ACTION 열거형은 Visual Studio 디버깅에서 예외를 가로챌 때 수행할 작업을 지정 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e80ed1b17f98326701b0ca0aacb8e114c9b49db4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606445"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
예외를 가로챌 때 수행할 작업을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

## <a name="parameters"></a>매개 변수

`IEA_INTERCEPT`\
현재 예외를 가로챌 수 있도록 합니다. 이 값은 현재 지원 되며 반드시 지정 해야 합니다.

## <a name="remarks"></a>설명
이러한 값은 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 메서드에 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
