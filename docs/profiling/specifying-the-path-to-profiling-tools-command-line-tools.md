---
title: 프로파일링 명령줄 도구의 경로 지정
description: 프로파일링 도구 명령줄 도구의 경로가 PATH 환경 변수에 추가되지 않은 경우 프로파일링 도구 명령줄 도구의 경로를 지정합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa1cb81d46f0977de2db9d78c6db53f542faa70f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720035"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>프로파일링 도구 명령줄 도구의 경로 지정

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구의 경로가 PATH 환경 변수에 추가되지 않았습니다. 32비트 컴퓨터에는 도구가 단일 디렉터리에 있습니다. 64비트 컴퓨터에는 프로파일링 도구가 32비트 및 64비트 버전으로 있습니다.

## <a name="32-bit-computers"></a>32비트 컴퓨터

네이티브 코드의 경우 Visual Studio 프로파일러 API는 *VSPerf.dll* 에 있습니다. 헤더 파일, *VSPerf.h* 및 가져오기 라이브러리, *VSPerf.lib* 는 *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* 디렉터리에 있습니다.

 관리되는 코드의 경우 프로파일러 API는 *Microsoft.VisualStudio.Profiler.dll* 에 있습니다. 이 DLL은 *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* 디렉터리에 있습니다.

## <a name="64-bit-computers"></a>64비트 컴퓨터

64비트 컴퓨터에서 프로파일링된 애플리케이션의 대상 플랫폼에 따라 경로를 지정합니다.

- 32비트 애플리케이션의 경우 기본 프로파일러 도구 디렉터리는 다음과 같습니다.

     (네이티브) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     (관리형) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- 64비트 애플리케이션의 경우 기본 프로파일러 도구가 위치한 디렉터리는 다음과 같습니다.

     (네이티브) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     (관리형) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
