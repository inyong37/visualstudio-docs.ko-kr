---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b2bf9265954b234cf31e9b07a0ed45bc5b78435
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47553344"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [IDebugCustomAttributeQuery2::IsCustomAttributeDefined](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined)합니다.  
  
사용자 지정 특성을 이름별 있는지 여부를 결정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszCustomAttributeName`  
 [in] 검색할 사용자 지정 특성의 이름을 포함 하는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 S_ok이 고, 사용자 지정 특성은이 필드에 정의 되어 있으면 그렇지 S_FALSE를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 사용자 지정 특성을 사용 하 여 연결 된 특성 바이트를 가져오려면 호출 합니다 [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
