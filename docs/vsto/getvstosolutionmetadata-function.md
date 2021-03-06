---
title: GetVstoSolutionMetadata 함수
description: GetVstoSolutionMetadata API가 Office 인프라를 지 원하는 방법을 알아보고 코드에서 직접 사용할 수 없습니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 205bde9352e2a037b4a08108d8cfce3460034e66
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845039"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata 함수
  이 API는 Office 인프라를 지원 하며 사용자 코드에서 직접 사용 하기 위한 것이 아닙니다.

## <a name="syntax"></a>구문

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|사용 하지 마세요.|
|*Pp솔루션 정보*|사용 하지 마세요.|

## <a name="return-value"></a>반환 값
 함수가 성공 하면 **S_OK** 반환 됩니다. 함수가 실패 하면 오류 코드를 반환 합니다.
