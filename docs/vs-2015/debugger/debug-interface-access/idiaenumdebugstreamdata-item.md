---
title: 'Idiaenumdebugstreamdata:: Item | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee6e481cafaed07dde23ff763741eac4622b50d9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47542147"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [idiaenumdebugstreamdata:: Item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumdebugstreamdata-item)합니다.  
  
지정된 된 레코드를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 인덱스입니다.  
 [in] 검색할 레코드의 인덱스입니다. 인덱스는 0에서 범위 `count`-1로, 여기서 `count` 반환한 [idiaenumdebugstreamdata:: Get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)합니다.  
  
 cbData  
 [in] 바이트의 데이터 버퍼의 크기입니다.  
  
 pcbData  
 [out] 반환 된 바이트 수를 반환 합니다. 하는 경우 `data` 됩니다 `NULL`, 다음 `pcbData` 지정된 된 레코드에서 사용 가능한 데이터의 바이트의 총 수를 포함 합니다.  
  
 데이터]  
 [out] 디버그 스트림 레코드 데이터를 사용 하 여 입력 되는 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_INVALIDARG` 잘못 된 매개 변수에 대 한 경우에 `index` 매개 변수 범위를 벗어났습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [Idiaenumdebugstreamdata:: Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [Idiaenumdebugstreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [Idiaenumdebugstreamdata:: Get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)


