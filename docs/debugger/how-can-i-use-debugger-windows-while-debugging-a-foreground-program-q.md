---
title: 전경 앱을 디버깅하는 동안 디버거 창 사용 | Microsoft Docs
Description: 포그라운드에 유지해야 하는 프로그램을 디버그하는 경우 원격 디버깅을 사용하여 백그라운드로 전환되지 않도록 합니다.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f39f7dfbd463c48675f4b8c98612dfab3f33de3c
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398742"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>전경 프로그램을 디버깅하는 동안 디버거 창을 어떻게 사용합니까?
## <a name="problem-description"></a>문제 설명
 화면 그림에 대한 문제를 디버깅하려고 합니다. 이 문제를 살펴 보려면 프로그램을 전경에 유지해야 하는데 이 때 디버깅 창에 액세스할 수 없습니다. 어떻게 해야 합니까?

## <a name="solution"></a>솔루션
 다른 컴퓨터가 있을 경우 원격 디버깅을 사용할 수 있습니다. 컴퓨터 두 대를 설치하면 호스트에서 디버거가 작동하는 동안 원격 컴퓨터에서 화면 그림을 볼 수 있습니다. 원격 디버깅에 대한 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.

## <a name="see-also"></a>참조
- [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)