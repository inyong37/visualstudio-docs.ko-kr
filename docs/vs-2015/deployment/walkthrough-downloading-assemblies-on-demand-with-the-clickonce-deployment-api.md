---
title: '연습: ClickOnce 배포 API에서 요청 시 어셈블리 다운로드 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8b5779ee2c1cd57d08627038ab7b65cc760afb5e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47543481"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>연습: ClickOnce 배포 API에서 요청 시 어셈블리 다운로드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [연습: ClickOnce 배포 API를 사용 하 여 요청 시 어셈블리 다운로드](https://docs.microsoft.com/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api)합니다.  
  
기본적으로 모든 어셈블리에 포함 된를 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 응용 프로그램을 처음 실행할 때 다운로드 됩니다. 그러나 소수의 사용자가 사용 되는 응용 프로그램 부분을 할 수 있습니다. 이 경우 해당 형식 중 하나를 만들 때에만 어셈블리를 다운로드하고자 할 수 있습니다. 다음 연습에서는 특정 어셈블리를 "optional"로 응용 프로그램에서 표시 하는 방법에 설명 하 고의 클래스를 사용 하 여 다운로드 하는 방법의 <xref:System.Deployment.Application> 네임 스페이스는 CLR (공용 언어 런타임)을 요구 하는 경우.  
  
> [!NOTE]
>  이 절차를 사용하려면 완전 신뢰 상태에서 응용 프로그램을 실행해야 합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 완료 하려면 다음 구성 요소 중 하나가 필요 합니다.  
  
-   Windows SDK입니다. Windows SDK는 Microsoft 다운로드 센터에서 다운로드할 수 있습니다.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>프로젝트 만들기  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>요청 시 어셈블리를 사용 하는 프로젝트를 만들려면  
  
1.  다음과 라는 디렉터리를 만듭니다.  
  
2.  Windows SDK 명령 프롬프트를 열고 또는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 프롬프트입니다.  
  
3.  다음과 디렉터리로 변경 합니다.  
  
4.  다음 명령을 사용 하 여 공개/개인 키 쌍을 생성 합니다.  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  메모장 이나 다른 텍스트 편집기를 사용 하 라는 클래스를 정의 `DynamicClass` 라는 단일 속성만 사용 하 여 `Message`입니다.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6.  텍스트 라는 파일로 저장 `ClickOnceLibrary.cs` 또는 `ClickOnceLibrary.vb`다음과 디렉터리로 사용 하는 언어에 따라 합니다.  
  
7.  파일을 어셈블리로 컴파일하십시오.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  어셈블리의 공개 키 토큰을 가져오기, 다음 명령을 사용 합니다.  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. 텍스트를 사용 하 여 새 파일을 편집기 만들고 다음 코드를 입력 합니다. 이 코드는 필요한 경우 ClickOnceLibrary 어셈블리를 다운로드 하는 Windows Forms 응용 프로그램을 만듭니다.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. 코드에서 호출을 찾습니다 <xref:System.Reflection.Assembly.LoadFile%2A>합니다.  
  
11. 설정`PublicKeyToken` 이전에 검색 된 값입니다.  
  
12. 로 파일을 저장 `Form1.cs` 또는 `Form1.vb`합니다.  
  
13. 다음 명령을 사용 하 여 실행 파일로 컴파일하십시오.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>어셈블리를 선택 사항으로 표시  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe를 사용 하 여 ClickOnce 응용 프로그램에 선택적으로 어셈블리를 표시 하려면  
  
1.  MageUI.exe를 사용 하 여에 설명 된 대로 응용 프로그램 매니페스트를 만듭니다 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)합니다. 응용 프로그램 매니페스트는 다음 설정을 사용 합니다.  
  
    -   응용 프로그램 매니페스트 이름을 `ClickOnceOnDemand`입니다.  
  
    -   에 **파일** 페이지 ClickOnceLibrary.dll 행에서 설정 합니다 **파일 형식** 열을 **None**합니다.  
  
    -   에 **파일** ClickOnceLibrary.dll 행 형식에서에서 페이지 `ClickOnceLibrary.dll` 에 **그룹** 열입니다.  
  
2.  MageUI.exe를 사용 하 여에 설명 된 대로 배포 매니페스트를 만듭니다 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)합니다. 배포 매니페스트는 다음 설정을 사용 합니다.  
  
    -   배포 매니페스트의 이름을 `ClickOnceOnDemand`입니다.  
  
## <a name="testing-the-new-assembly"></a>새 어셈블리 테스트  
  
#### <a name="to-test-your-on-demand-assembly"></a>요청 시 어셈블리를 테스트하려면  
  
1.  업로드에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 웹 서버에 배포 합니다.  
  
2.  배포 된 응용 프로그램 시작 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 매니페스트의 URL를 입력 하 여 웹 브라우저에서 합니다. 호출 하는 경우에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 `ClickOnceOnDemand`, adatum.com의 루트 디렉터리에 업로드 하 여, URL은 다음과 같습니다.  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  기본 폼이 나타나면 <xref:System.Windows.Forms.Button>을 누릅니다. 문자열 "Hello, World!" 라는 메시지 상자 창에 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Deployment.Application.ApplicationDeployment>


