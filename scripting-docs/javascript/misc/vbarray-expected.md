---
title: VBArray가 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b4e6521e5d363c21311b19e2ecc1679981acac3
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862694"
---
# <a name="vbarray-expected"></a>VBArray가 필요합니다.
Visual Basic safeArray가 아닌 개체를 제공 했습니다.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays는 읽기 전용이므로 직접 만들 수 없습니다. SafeArray 인수는 VBArray 값 이며 생성자에 전달 되기 전에 VBArray 값을 가져와야 합니다 `VBArray` . 이 작업은 기존 ActiveX 또는 다른 개체에서 값을 검색하는 방식으로만 수행할 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- **Vbarray 생성자에** **vbarray** 개체만 전달 하는지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [VBArray 개체](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [배열 사용](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)