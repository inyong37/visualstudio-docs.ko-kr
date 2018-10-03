---
title: UI 자동화를 사용하여 코드 테스트 | Microsoft 문서
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
ms.assetid: ad9e3eaa-ab86-436e-95b8-dc20eb1f8b2a
caps.latest.revision: 87
ms.author: gewarren
manager: douge
ms.openlocfilehash: 92668aad54a032ccdbda2242ffcd132b356ea331
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47552632"
---
# <a name="use-ui-automation-to-test-your-code"></a>UI 자동화를 사용하여 코드 테스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [사용 하 여 UI 자동화를 테스트 프로그램 코드](https://docs.microsoft.com/visualstudio/test/use-ui-automation-to-test-your-code)합니다.  
  
UI(사용자 인터페이스)를 통해 응용 프로그램을 실행하는 자동화된 테스트를 CUIT(*코딩된 UI 테스트*)라고 합니다. 이러한 테스트는 UI 컨트롤의 기능 테스트를 포함합니다. 이러한 테스트를 통해 사용자 인터페이스를 비롯해 전체 응용 프로그램이 제대로 기능하는지 확인할 수 있습니다. 코딩된 UI 테스트는 특히 사용자 인터페이스(예: 웹 페이지)에 유효성 검사 또는 기타 논리가 있는 경우에 유용합니다. 또한 기존 수동 테스트를 자동화하는 데 자주 사용됩니다.  
  
 다음 그림과 같이 일반적인 개발 경험은 처음에는 간단하게 응용 프로그램을 빌드하고(F5) UI 컨트롤을 클릭해 보면서 제대로 작동하는지 확인하는 것으로 시작할 수 있습니다. 그런 다음 코딩된 테스트를 만들기로 결정할 수 있습니다. 그러면 응용 프로그램을 계속해서 수동으로 테스트할 필요가 없습니다. 응용 프로그램에서 테스트 중인 특정 기능에 따라 기능 테스트 또는 UI 수준에서 테스트를 포함하거나 포함하지 않을 수 있는 통합 테스트에 대한 코드를 작성할 수 있습니다. 일부 비즈니스 논리에 직접 액세스하려는 경우 단위 테스트를 코딩할 수 있습니다. 그러나 특정 상황에서는 응용 프로그램의 다양한 UI 컨트롤 테스트를 포함하는 것이 유용할 수 있습니다. 코딩된 UI 테스트는 초기 (F5) 시나리오를 자동화하여 코드 변경(code churn)이 응용 프로그램의 기능에 영향을 미치지 않는지 확인할 수 있습니다.  
  
 ![응용 프로그램 개발 중 테스트](../test/media/cuit-overview.png "CUIT_Overview")  
  
 코딩된 UI 테스트는 만들기 쉽습니다. CUIT 테스트 빌더가 백그라운드에서 실행되는 동안 테스트를 수동으로 간단하게 수행할 수 있습니다. 또한 특정 필드에 나타나야 하는 값을 지정할 수도 있습니다. CUIT 테스트 빌더는 사용자의 작업을 기록하고 이러한 작업으로부터 코드를 생성합니다. 테스트를 만든 후 작업 시퀀스를 수정할 수 있는 특수 편집기에서 테스트를 편집할 수 있습니다.  
  
 또는 Microsoft Test Manager에 기록된 테스트 사례가 있는 경우에서 해당 사례에서 코드를 생성할 수 있습니다. 자세한 내용은 [수동 테스트 기록 및 재생](http://msdn.microsoft.com/library/9792e72f-600e-441f-9d4e-6510e5965665)을 참조하세요.  
  
 특수 CUIT 테스트 빌더 및 편집기를 사용하면 사용자의 주요 기술이 코딩이 아니라 테스트하는 것이더라도 코딩된 UI 테스트를 쉽게 만들고 편집할 수 있습니다. 그러나 개발자가 보다 수준 높은 방식으로 테스트를 확장하려는 경우 쉽게 복사하고 변경할 수 있도록 코드가 구조화되어 있습니다. 예를 들어 웹 사이트에서 무언가를 구매하는 테스트를 기록한 다음 생성된 코드를 편집하여 여러 품목을 구매하는 루프를 추가할 수 있습니다.  
  
 **요구 사항**  
  
-   Visual Studio Enterprise  
  
 코딩된 UI 테스트에서 지원하는 플랫폼 및 구성에 대한 자세한 내용은 [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)을 참조하세요.  
  
 **항목 내용**  
  
-   [코딩된 UI 테스트 만들기](#VerifyingCodeUsingCUITCreate)  
  
    -   [기본 절차](#VerifyingCodeUsingCUITCreate)  
  
    -   [응용 프로그램 시작 및 중지](#starting)  
  
    -   [UI 컨트롤 속성의 유효성 검사](#VerifyingCodeUsingCUITGenerateAssertions)  
  
-   [코딩된 UI 테스트 사용자 지정](#VerifyingCodeCUITModify)  
  
    -   [생성된 코드](#generatedCode)  
  
    -   [코딩 UI 컨트롤 작업 및 속성](#actions)  
  
    -   [디버깅](#debugging)  
  
-   [다음 단계](#VerifyCodeUsingCUITWhatsNext)  
  
##  <a name="VerifyingCodeUsingCUITCreate"></a> 코딩된 UI 테스트 만들기  
  
1.  **코딩된 UI 테스트 프로젝트를 만듭니다.**  
  
     코딩된 UI 테스트는 코딩된 UI 테스트 프로젝트에 포함되어 있어야 합니다. 아직 코딩된 UI 테스트 프로젝트가 없으면 하나를 만듭니다. **솔루션 탐색기**의 솔루션 바로 가기 메뉴에서 **추가**, **새 프로젝트**를 차례로 선택하고 **Visual Basic** 또는 **Visual C#** 을 선택합니다. 그런 다음 **테스트**, **C코딩된 UI 테스트**를 차례로선택합니다.  
  
    -   ***코딩된 UI 테스트** 프로젝트 템플릿이 표시되지 않습니다.*  
  
         코딩된 UI 테스트를 지원하지 않는 Visual Studio 버전을 사용하는 중일 수 있습니다. 코딩된 UI 테스트를 만들려면 Visual Studio Enterprise를 사용해야 합니다.  
  
2.  **코딩된 UI 테스트 파일을 추가합니다.**  
  
     코딩된 UI 프로젝트를 방금 만든 경우 첫 번째 CUIT 파일이 자동으로 추가됩니다. 다른 테스트 파일을 추가하려면 코딩된 UI 테스트 프로젝트의 바로 가기 메뉴를 열고 **추가**를 가리킨 다음 **코딩된 UI 테스트**를 선택합니다.  
  
     ![코딩된 UI 테스트 만들기](../test/media/codedui-create.png "CodedUI_Create")  
  
     **코딩된 UI 테스트에 대한 코드 생성** 대화 상자에서 **작업 기록, UI 맵 편집 또는 어설션 추가**를 선택합니다.  
  
     ![기록 작업 선택](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")  
  
     코딩된 UI 테스트 빌더가 나타나고 Visual Studio가 최소화됩니다.  
  
     ![코딩된 UI 테스트 빌더](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")  
  
3.  **작업 시퀀스를 기록합니다**.  
  
     **기록을 시작하려면** **기록** 아이콘을 선택합니다. 필요한 경우 응용 프로그램 시작을 비롯하여 응용 프로그램에서 테스트하려는 작업을 수행합니다.  
  
     예를 들어 웹 응용 프로그램을 테스트 중인 경우 브라우저를 시작하고 웹 사이트로 이동해서 응용 프로그램에 로그인할 수 있습니다.  
  
     **기록을 일시 중지하려면**(예: 들어오는 메일을 처리해야 하는 경우) **일시 중지**를 선택합니다.  
  
    > [!WARNING]
    >  데스크톱에서 수행된 모든 작업이 기록됩니다. 기록에 중요한 데이터가 포함될 수 있는 작업을 수행하는 경우에는 기록을 일시 중지합니다.  
  
     실수로 기록한 **작업을 삭제하려면** **작업 편집**을 선택합니다.  
  
     작업을 복제하는 **코드를 생성하려면** **코드 생성**아이콘을 선택하고 코딩된 UI 테스트 메서드의 이름 및 설명을 입력합니다.  
  
4.  **텍스트 상자와 같은 UI 필드에서 값을 확인합니다**.  
  
     코딩된 UI 테스트 빌더에서 **어설션 추가**를 선택한 다음 실행 중인 응용 프로그램에서 UI 컨트롤을 선택합니다. 나타나는 속성 목록에서 속성(예: 텍스트 상자의 **텍스트**)을 선택합니다. 바로 가기 메뉴에서 **어설션 추가**를 선택합니다. 대화 상자에서 비교 연산자, 비교 값 및 오류 메시지를 선택합니다.  
  
     어설션 창을 닫고 **코드 생성**을 선택합니다.  
  
     ![코딩된 UI 테스트 대상 요소](../test/media/codedui-1.png "CodedUI_1")  
  
    > [!TIP]
    >  작업 기록과 값 확인을 번갈아 가며 수행합니다. 작업 또는 확인의 각 시퀀스 종료 시 코드를 생성합니다. 필요한 경우 나중에 새 작업 및 확인을 삽입할 수 있습니다.  
  
     자세한 내용은 [컨트롤 속성의 유효성 검사](#VerifyingCodeUsingCUITGenerateAssertions)를 참조하세요.  
  
5.  **생성된 테스트 코드를 확인합니다**.  
  
     생성된 코드를 보려면 UI 테스트 빌더 창을 닫습니다. 코드에서 각 단계에 지정한 이름을 확인할 수 있습니다. 코드는 만들어 놓은 CUIT 파일에 들어 있습니다.  
  
    ```csharp  
    [CodedUITest]  
    public class CodedUITest1  
    { ...  
      [TestMethod]  
      public void CodedUITestMethod1()  
      {  
          this.UIMap.AddTwoNumbers();  
          this.UIMap.VerifyResultValue();  
          // To generate more code for this test, select   
          // "Generate Code" from the shortcut menu.  
      }  
    }  
    ```  
  
6.  **작업 및 어설션을 더 추가합니다**.  
  
     테스트 메서드의 적절한 지점에 커서를 놓은 다음 바로 가기 메뉴에서 **코딩된 UI 테스트에 대한 코드 생성**을 선택합니다. 해당 지점에 새 코드가 삽입됩니다.  
  
7.  **테스트 작업 및 어설션의 정보를 편집합니다**.  
  
     UIMap.uitest를 엽니다. 이 파일은 코딩된 UI 테스트 편집기에서 열리며 기록한 작업의 모든 시퀀스와 어설션을 이 편집기에서 편집할 수 있습니다.  
  
     ![코딩된 UI 테스트 편집기](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")  
  
     자세한 내용은 [코딩된 UI 테스트 편집기를 사용하여 코딩된 UI 테스트 편집](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)을 참조하세요.  
  
8.  **테스트를 실행합니다**.  
  
     테스트 탐색기를 사용하거나 테스트 메서드에서 바로 가기 메뉴를 열고 **테스트 실행**을 선택합니다. 테스트 실행 방법에 대한 자세한 내용은 이 항목의 끝에 있는 [다음 단계](#VerifyCodeUsingCUITWhatsNext) 섹션의 [테스트 탐색기를 사용하여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md) 및 *실행 중인 코딩된 UI 테스트의 추가 옵션*을 참조하세요.  
  
 이 항목의 나머지 섹션에서는 이 절차의 단계에 대해 자세히 설명합니다.  
  
 보다 자세한 예제는 [연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)를 참조하세요. 이 연습에서는 간단한 WPF(Windows Presentation Foundation) 웹 응용 프로그램을 만들어, 코딩된 UI 테스트를 만들고 편집하고 유지 관리하는 방법을 보여 줍니다. 이 연습에서는 여러 타이밍 문제 및 제어 리팩터링으로 인해 중단된 테스트를 해결하기 위한 방법을 제공합니다.  
  
###  <a name="starting"></a> 테스트 대상 응용 프로그램 시작 및 중지  
 *각 테스트마다 응용 프로그램, 브라우저 또는 데이터베이스를 별도로 시작했다가 중지하고 싶지 않습니다. 어떻게 하면 이러한 문제를 피할 수 있나요?*  
  
-   ![필수 구성 요소](../test/media/prereq.png "Prereq") 테스트 중인 응용 프로그램 시작 작업을 기록하지 않으려는 경우 **기록** 아이콘을 선택하기 전에 응용 프로그램을 시작해야 합니다.  
  
-   ![필수 구성 요소](../test/media/prereq.png "Prereq")테스트 종료 시 테스트를 실행하는 프로세스가 종료됩니다. 테스트에서 응용 프로그램을 시작했다면 일반적으로 해당 응용 프로그램이 닫힙니다.  테스트 종료 시에도 응용 프로그램을 닫지 않으려면 솔루션에 .runsettings 파일을 추가하고 `KeepExecutorAliveAfterLegacyRun` 옵션을 사용해야 합니다. 자세한 내용은 [.runsettings 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)을 참조하세요.  
  
-   ![필수 구성 요소](../test/media/prereq.png "Prereq") [TestInitialize] 특성으로 식별되고 각 테스트 메서드 시작 시 코드를 실행하는 테스트 초기화 메서드를 추가할 수 있습니다. 예를 들어 TestInitialize 메서드에서 응용 프로그램을 시작할 수 있습니다.  
  
-   ![필수 구성 요소](../test/media/prereq.png "Prereq") [TestCleanup] 특성으로 식별되고 각 테스트 메서드 종료 시 코드를 실행하는 테스트 정리 메서드를 추가할 수 있습니다. 예를 들어 응용 프로그램을 닫는 메서드는 TestCleanup 메서드에서 호출될 수 있습니다.  
  
###  <a name="VerifyingCodeUsingCUITGenerateAssertions"></a> UI 컨트롤 속성의 유효성 검사  
 **코딩된 UI 테스트 빌더**를 사용해 테스트의 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>에 UI(사용자 인터페이스) 컨트롤을 추가하거나 UI 컨트롤에 어설션을 사용하는 확인 메서드에 대한 코드를 생성할 수 있습니다.  
  
 UI 컨트롤을 위한 어설션을 생성하려면 코딩된 UI 테스트 빌더에서 **어설션 추가** 도구를 선택하여 올바른지 확인하려는 테스트 중인 응용 프로그램의 컨트롤로 끌어 옵니다. 컨트롤 주위에 상자가 생기면 마우스를 놓습니다. `UIMap.Designer.cs` 파일에 컨트롤 클래스 코드가 즉시 생성됩니다.  
  
 ![코딩된 UI 테스트 대상 요소](../test/media/codedui-1.png "CodedUI_1")  
  
 이제 이 컨트롤의 속성이 **어설션 추가** 대화 상자에 나열됩니다.  
  
 특정 컨트롤로 이동하는 또 다른 방법은 화살표 **(<<)** 를 선택하여 **UI 컨트롤 맵**의 보기를 확장하는 것입니다. 부모, 형제 또는 자식 컨트롤을 찾으려면 맵에서 아무 곳이나 클릭한 다음 화살표 키를 사용해 트리 주위를 이동할 수 있습니다.  
  
 ![코딩된 UI 테스트 속성](../test/media/codedui-2.png "CodedUI_2")  
  
-   *응용 프로그램에서 컨트롤을 선택하면 아무런 속성도 표시되지 않거나 UI 컨트롤 맵에 컨트롤이 표시되지 않습니다.*  
  
     응용 프로그램 코드에서 확인하려는 컨트롤에는 고유한 ID(예: HTML ID 특성 또는 WPF UId)가 있어야 합니다. 이러한 ID를 추가하려면 응용 프로그램 코드를 업데이트해야 합니다.  
  
 다음으로, 확인하려는 UI 컨트롤의 속성 바로 가기 메뉴를 열고 **어설션 추가**를 가리킵니다. **어설션 추가** 대화 상자에서 어설션의 **비교 연산자**(예: <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>)를 선택하고 **비교 값**에 어설션 값을 입력합니다.  
  
 ![코딩된 UI 테스트 어설션](../test/media/codedui-3.png "CodedUI_3")  
  
 테스트에 필요한 어설션을 모두 추가했으면 **확인**을 선택합니다.  
  
 어설션에 대한 코드를 생성하고 UI 맵에 컨트롤을 추가하려면 **코드 생성** 아이콘을 선택합니다. 코딩된 UI 테스트 메서드의 이름과 메서드에 대한 주석으로 추가될 설명을 입력합니다. **추가 후 생성**을 선택합니다. 다음으로, **닫기** 아이콘을 선택해 **코딩된 UI 테스트 빌더**를 닫습니다. 그러면 다음 코드와 유사한 코드가 생성됩니다. 예를 들어 입력한 이름이 `AssertForAddTwoNumbers`이면 코드는 다음 예제와 같습니다.  
  
-   코딩된 UI 테스트 파일의 테스트 메서드에 assert 메서드 AssertForAddTwoNumbers에 대한 호출을 추가합니다.  
  
    ```  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        this.UIMap.AddTwoNumbers();  
        this.UIMap.AssertForAddTwoNumbers();  
    }  
    ```  
  
     이 파일을 편집하여 단계 및 어설션의 순서를 변경하거나 새 테스트 메서드를 만들 수 있습니다. 코드를 추가하려면 테스트 메서드에 커서를 올려 놓고 바로 가기 메뉴에서 **코딩된 UI 테스트에 대한 코드 생성**을 선택합니다.  
  
-   UI 맵(UIMap.uitest)에 `AssertForAddTwoNumbers` 메서드를 추가합니다. 이 파일은 어설션을 편집할 수 있는 코딩된 UI 테스트 편집기에서 열립니다.  
  
     ![코딩된 UI 테스트 편집기를 사용하여 어설션 편집](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")  
  
     자세한 내용은 [코딩된 UI 테스트 편집기를 사용하여 코딩된 UI 테스트 편집](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)을 참조하세요.  
  
     또한 UIMap.Designer.cs에서 생성된 어설션 메서드 코드를 볼 수도 있습니다. 그러나 이 파일은 편집하면 안 됩니다. 코드의 변경된 버전을 만들려면 메서드를 다른 파일(예: UIMap.cs)로 복사한 다음 메서드 이름을 바꾸고 거기서 메서드를 편집합니다.  
  
    ```  
    public void AssertForAddTwoNumbers()  
    {  
        ...  
    }  
    ```  
  
 *코딩된 UI 테스트 빌더에서 어설션 추가 도구를 선택하려고 하면 선택하려는 컨트롤이 포커스를 잃고 사라집니다. 어떻게 해야 컨트롤을 선택하나요?*  
 **키보드를 사용하여 숨겨진 컨트롤 선택**  
  
 경우에 따라 [컨트롤을 추가하고 해당 컨트롤의 속성에 대한 유효성 검사를 수행](#VerifyingCodeUsingCUITGenerateAssertions)할 때 키보드를 사용해야 할 수 있습니다. 예를 들어 상황에 맞는 메뉴 컨트롤을 사용하는 코딩된 UI 테스트를 기록하려는 경우 코딩된 UI 테스트 빌더에서 어설션 추가 메뉴를 선택하려고 하면 컨트롤의 메뉴 항목 목록이 포커스를 잃고 사라질 수 있습니다. 이러한 현상은 아래 그림에서도 확인할 수 있습니다. 여기서 어설션 추가 도구로 Internet Explorer의 상황에 맞는 메뉴를 선택하려고 하면 이 메뉴가 포커스를 잃고 사라집니다.  
  
 ![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")  
  
 키보드를 사용하여 UI 컨트롤을 선택하려면 해당 컨트롤 위에 마우스를 올려 둡니다. 그런 다음 **Ctrl** 키와 **I** 키를 동시에 누르고 있습니다. 키를 놓습니다. 코딩된 UT 테스트 빌더가 컨트롤을 기록합니다.  
  
> [!WARNING]
>  Microsoft Lync를 사용 중인 경우 코딩된 UI 테스트 빌더를 시작하려면 Lync를 닫아야 합니다. Microsoft Lync에서는 **Ctrl+I** 바로 가기 키가 정상적으로 작동하지 않습니다.  
  
 *컨트롤을 마우스로 가리키기를 기록할 수가 없습니다. 이 문제를 해결할 방법이 있나요?*  
 **수동으로 마우스로 가리키기 기록**  
  
 경우에 따라 코딩된 UI 테스트에서 사용 중인 특정 컨트롤을 사용하려면 키보드로 마우스 가리키기 이벤트를 기록해야 하는 경우가 있습니다. 예를 들어 Windows Form 또는WPF(Windows Presentation Foundation) 응용 프로그램을 테스트하는 경우 사용자 지정 코드가 있을 수 있습니다. 또는 사용자가 트리 노드를 마우스로 가리키면 트리 노드가 확장됨과 같이 컨트롤을 마우스로 가리키는 것에 대해 정의된 특별한 동작이 있을 수 있습니다. 이러한 상황을 테스트하려면 미리 정의된 키보드 키를 눌러 컨트롤을 마우스로 가리켰음을 코딩된 UI 테스트 빌더에 수동으로 알려야 합니다.  
  
 코딩된 UI 테스트를 수행하는 경우 컨트롤을 마우스로 가리킵니다. 그런 다음 키보드에서 Shift+R을 누른 채 Ctrl 키를 누르고 있습니다. 키를 놓습니다. 코딩된 UT 테스트 빌더가 마우스로 가리키기 이벤트를 기록합니다.  
  
 ![CodedUI&#95;Hover](../test/media/codedui-hover.png "CodedUI_Hover")  
  
 테스트 메서드를 생성한 후 다음 예제와 유사한 코드가 UIMap.Desinger.cs 파일에 추가됩니다.  
  
```csharp  
// Mouse hover '1' label at (87, 9)  
Mouse.Hover(uIItem1Text, new Point(87, 9));  
  
```  
  
 *내 환경의 다른 곳에서 마우스 가리키기 이벤트 캡처에 대한 키 할당이 사용 중입니다. 기본 키 할당을 변경할 수 있나요?*  
 **마우스로 가리키기 키보드 할당 구성**  
  
 필요한 경우 코딩된 UI 테스트에서 마우스 가리키기 이벤트를 적용하는 데 사용되는 Ctrl+Shift+R의 기본 키보드 할당을 다른 키로 사용하도록 구성할 수 있습니다.  
  
> [!WARNING]
>  일반적인 경우에는 마우스 가리키기 이벤트에 대한 키보드 할당을 변경할 필요가 없습니다. 키보드 할당을 다시 할당할 때에는 주의해야 합니다. Visual Studio 또는 테스트 중인 응용 프로그램 내의 다른 곳에서 선택한 키보드 할당이 이미 사용 중일 수 있습니다.  
  
 키보드 할당을 변경하려면 다음 구성 파일을 수정해야 합니다.  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 구성 파일에서 `HoverKeyModifier` 및 `HoverKey` 키 값을 변경하여 키보드 할당을 수정합니다.  
  
```  
<!-- Begin : Background Recorder Settings -->  
<!-- HoverKey to use. -->  
<add key="HoverKeyModifier" value="Control, Shift"/>  
<add key="HoverKey" value="R"/>  
  
```  
  
 *웹 사이트에서 마우스로 가리키기를 기록하는 데 문제가 있습니다. 이 문제를 수정할 수 있나요?*  
 **웹 브라우저에 대한 암시적 마우스로 가리키기 설정**  
  
 여러 웹 사이트에서 특정 컨트롤을 마우스로 가리키면 해당 컨트롤이 확장되어 추가 정보가 표시됩니다. 일반적으로 이러한 컨트롤은 데스크톱 응용 프로그램에서 메뉴처럼 보입니다. 이는 일반적인 패턴이므로 코딩된 UI 테스트에서는 웹 브라우징에 대한 암시적 가리키기를 사용합니다. 예를 들어 Internet Explorer에서 마우스로 가리키기를 기록하는 경우 이벤트가 종료됩니다. 이러한 이벤트는 중복 가리키기 기록으로 이어질 수 있습니다. 따라서 UI 테스트 구성 파일에서 `ContinueOnError`를 `true`로 설정하면 암시적 가리키기가 기록됩니다. 그러면 가리키기 이벤트가 실패해도 계속해서 재생할 수 있습니다.  
  
 웹 브라우저에서 암시적 가리키기를 기록하려면 다음 구성 파일을 엽니다.  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 다음 샘플에 표시된 것처럼 구성 파일에 있는 키 `RecordImplicitiHovers`의 값이 `true`로 설정되어 있는지 확인합니다.  
  
```  
<!--Use this to enable/disable recording of implicit hovers.-->  
<add key="RecordImplicitHover" value="true"/>  
  
```  
  
##  <a name="VerifyingCodeCUITModify"></a> 코딩된 UI 테스트 사용자 지정  
 코딩된 UI 테스트를 만든 후 Visual Studio에서 다음 도구 중 하나를 사용해 편집할 수 있습니다.  
  
-   **코딩된 UI 테스트 빌더:** 코딩된 UI 테스트 빌더를 사용하여 테스트에 컨트롤 및 유효성 검사를 더 추가할 수 있습니다. 이 항목의 [컨트롤 추가 및 해당 컨트롤 속성에 대한 유효성 검사](#VerifyingCodeUsingCUITGenerateAssertions) 섹션을 참조하세요.  
  
-   **코딩된 UI 테스트 편집기:** 코딩된 UI 테스트 편집기에서는 코딩된 UI 테스트를 쉽게 수정할 수 있습니다. 코딩된 UI 테스트 편집기를 사용하면 테스트 메서드를 찾아서 보고 편집할 수 있습니다. 또한 UI 작업을 편집하고 UI 컨트롤 맵에서 관련 컨트롤을 편집할 수도 있습니다. 자세한 내용은 [코딩된 UI 테스트 편집기를 사용하여 코딩된 UI 테스트 편집](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)을 참조하세요.  
  
-   **코드 편집기:**  
  
    -   이 항목의 [UI 컨트롤 작업 및 속성 코딩](#VerifyingCodeCUITActionsandProperties) 섹션에서 설명하는 것처럼 테스트에서 컨트롤에 대한 코드를 수동으로 추가합니다.  
  
    -   코딩된 UI 테스트를 만든 후 데이터 기반이 되도록 수정할 수 있습니다. 자세한 내용은 [데이터 기반의 코딩된 UI 테스트 만들기](../test/creating-a-data-driven-coded-ui-test.md)를 참조하세요.  
  
    -   코딩된 UI 테스트 재생 시 창이 나타나거나 진행률 표시줄이 사라지는 등의 특정 이벤트가 발생할 때까지 기다리도록 테스트에 지시할 수 있습니다. 이렇게 하려면 적절한 UITestControl.WaitForControlXXX() 메서드를 추가합니다. 사용 가능한 메서드의 전체 목록을 보려면 [코딩된 UI 테스트가 재생 중 특정 이벤트를 기다리도록 지정](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)을 참조하세요. WaitForControlEnabled 메서드를 사용하여 컨트롤이 사용하도록 설정될 때까지 기다리는 코딩된 UI 테스트에 대한 예제는 [연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)를 참조하세요.  
  
    -   코딩된 UI 테스트에는 Internet Explorer 9 및 Internet Explorer 10에 포함된 일부 HTML5 컨트롤에 대한 지원이 포함됩니다. 자세한 내용은 [코딩된 UI 테스트에서 HTML5 컨트롤 사용](../test/using-html5-controls-in-coded-ui-tests.md)을 참조하세요.  
  
    -   **코딩된 UI 테스트 코딩 지침:**  
  
        -   [코딩된 UI 테스트 분석](../test/anatomy-of-a-coded-ui-test.md)  
  
        -   [최선의 코딩된 UI 테스트 방법](../test/best-practices-for-coded-ui-tests.md)  
  
        -   [여러 UI 맵이 포함된 대형 응용 프로그램 테스트](../test/testing-a-large-application-with-multiple-ui-maps.md)  
  
        -   [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)  
  
###  <a name="generatedCode"></a> 생성된 코드  
 **코드 생성**을 선택하면 다음과 같이 여러 코드 조각이 생성됩니다.  
  
-   **테스트 메서드의 줄**  
  
    ```csharp  
    [CodedUITest]  
    public class CodedUITest1  
    { ...  
      [TestMethod]  
      public void CodedUITestMethod1()  
      {  
          this.UIMap.AddTwoNumbers();  
          // To generate more code for this test, select   
          // "Generate Code" from the shortcut menu.      }  
    }  
    ```  
  
     이 메서드를 마우스 오른쪽 단추로 클릭하여 기록된 작업 및 유효성 검사를 추가할 수 있습니다. 또한 수동으로 편집하여 코드를 확장하거나 수정할 수 있습니다. 예를 들어 코드의 일부를 루프로 묶을 수 있습니다.  
  
     테스트 메서드를 새로 추가하고 해당 메서드에 동일한 방식으로 코드를 추가할 수도 있습니다. 각 테스트 메서드에는 `[TestMethod]` 특성이 있어야 합니다.  
  
-   **UIMap.uitest의 메서드**  
  
     이 메서드에는 기록한 작업에 대한 세부 정보 또는 확인한 값이 포함됩니다. 이 코드는 UIMap.uitest를 열어 편집할 수 있습니다. 이 파일은 기록된 작업을 삭제 또는 리팩터링할 수 있는 특수 편집기에서 열립니다.  
  
     또한 생성된 메서드를 UIMap.Designer.cs에서 확인할 수도 있습니다. 다음 메서드는 테스트 실행 시 기록한 작업을 수행합니다.  
  
    ```csharp  
    // File: UIMap.Designer.cs  
    public partial class UIMap  
    {  
      /// <summary>  
      /// Add two numbers  
      /// </summary>  
      public void AddTwoNumbers()  
      { ...   }  
    }  
    ```  
  
    > [!WARNING]
    >  테스트를 추가로 만들면 다시 생성되므로 이 파일은 편집하면 안 됩니다.  
  
     메서드를 UIMap.cs로 복사하여 이러한 메서드의 변경된 버전을 만들 수 있습니다. 예를 들어 다음과 같이 테스트 메서드에서 호출할 수 있는 매개 변수화된 버전을 만들 수 있습니다.  
  
    ```csharp  
    // File: UIMap.cs  
    public partial class UIMap // Same partial class  
    {  
      /// <summary>  
      /// Add two numbers – parameterized version  
      /// </summary>  
      public void AddTwoNumbers(int firstNumber, int secondNumber)  
      { ...   // Code modified to use parameters.  
      }  
    }  
    ```  
  
-   **UIMap.uitest의 선언**  
  
     이러한 선언은 테스트에서 사용하는 응용 프로그램의 UI 컨트롤을 나타내고 생성된 코드에서 컨트롤을 작동하고 컨트롤의 속성에 액세스하는 데 사용됩니다.  
  
     또한 자체 코드를 작성할 때 이러한 선언을 사용할 수도 있습니다. 예를 들어 웹 응용 프로그램이 테스트 메서드에서 하이퍼링크를 선택하거나 텍스트 상자에 값을 입력하거나 필드 값에 따라 분기해 다른 테스트 작업을 수행하도록 할 수 있습니다.  
  
     코딩된 UI 테스트 여러 개와 UI 맵 개체 및 파일 여러 개를 추가하여 큰 응용 프로그램을 쉽게 테스트할 수 있습니다. 자세한 내용은 [여러 UI 맵이 포함된 대형 응용 프로그램 테스트](../test/testing-a-large-application-with-multiple-ui-maps.md)를 참조하세요.  
  
 생성된 코드에 대한 자세한 내용은 [코딩된 UI 테스트 분석](../test/anatomy-of-a-coded-ui-test.md)을 참조하세요.  
  
###  <a name="actions"></a> UI 컨트롤 작업 및 속성 코딩  
 코딩된 UI 테스트에서 UI 테스트 컨트롤 작업 시 이러한 컨트롤은 작업과 속성의 두 부분으로 나뉩니다.  
  
-   첫 번째 부분은 UI 테스트 컨트롤에 대해 수행할 수 있는 작업으로 구성됩니다. 예를 들어 코딩된 UI 테스트는 UI 테스트 컨트롤에서 마우스 클릭을 시뮬레이트하거나 UI 테스트 컨트롤에 영향을 주기 위해 키보드에 입력된 키를 시뮬레이션할 수 있습니다.  
  
-   두 번째 파트는 UI 테스트 컨트롤에 대한 속성 얻기 및 설정 가능으로 구성됩니다. 예를 들어 코딩된 UI 테스트는 `ListBox`에서 항목 수를 얻거나 선택한 상태로 `CheckBox`를 설정할 수 있습니다.  
  
 **UI 테스트 컨트롤의 작업 액세스**  
  
 마우스 클릭 또는 키보드 작업과 같은 UI 테스트 컨트롤에 대한 작업을 수행하려면 다음과 같이 <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> 및 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> 클래스에서 메서드를 사용합니다.  
  
-   UI 테스트 컨트롤에 대해 마우스 클릭과 같은 마우스 기반 작업을 수행하려면 <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>을 사용합니다.  
  
     `Mouse.Click(buttonCancel);`  
  
-   편집 컨트롤에 입력과 같은 키보드 기반 작업을 수행하려면 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>을 사용합니다.  
  
     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`  
  
 **UI 테스트 컨트롤의 속성 액세스**  
  
 UI 컨트롤 관련 속성 값을 얻고 설정하기 위해 컨트롤의 속성 값을 직접 얻거나 설정할 수 있습니다. 또는 얻거나 설정하려는 특성 속성의 이름과 함께 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> 및 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> 메서드를 사용할 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>는 적절한 <xref:System.Type>으로 캐스팅할 수 있는 개체를 반환합니다. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>는 속성의 값에 대해 개체를 수락합니다.  
  
##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>UI 테스트 컨트롤에서 속성을 직접 얻거나 설정하려면  
  
-   T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList 또는 T:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox와 같이 T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl에서 파생된 컨트롤을 사용하여 다음과 같이 해당 컨트롤의 속성 값을 직접 얻거나 설정할 수 있습니다.  
  
    ```  
    int i = myHtmlList.ItemCount;  
    myWinCheckBox.Checked = true;  
    ```  
  
##### <a name="to-get-properties-from-ui-test-controls"></a>UI 테스트 컨트롤에서 속성을 얻으려면  
  
-   컨트롤에서 속성 값을 얻으려면 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>를 사용합니다.  
  
-   얻으려는 컨트롤의 속성을 지정하려면 각 컨트롤에 있는 `PropertyNames` 클래스의 적절한 문자열을 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>에 대한 매개 변수로 사용합니다.  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>는 적절한 데이터 형식을 반환하지만 이 반환 값은 <xref:System.Object>로 캐스팅됩니다. 그런 다음 반환 <xref:System.Object>는 적절한 형식으로 캐스팅되어야 합니다.  
  
     예제:  
  
     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`  
  
##### <a name="to-set-properties-for-ui-test-controls"></a>UI 컨트롤의 속성을 설정하려면  
  
-   컨트롤에서 속성을 설정하려면 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>를 사용합니다.  
  
-   설정할 컨트롤의 속성을 지정하려면 `PropertyNames` 클래스의 적절한 속성을 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>에 대한 첫 번째 매개 변수로 사용하고 속성 값은 두 번째 매개 변수로 사용합니다  
  
     예제:  
  
     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`  
  
###  <a name="debugging"></a> 디버깅  
 코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트를 분석할 수 있습니다. 코딩된 UI 테스트 로그는 코딩된 UI 테스트 실행에 대한 중요한 정보를 필터링하고 기록합니다. 로그 서식을 통해 문제를 신속하게 디버깅할 수 있습니다. 자세한 내용은 [코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)을 참조하세요.  
  
##  <a name="VerifyCodeUsingCUITWhatsNext"></a> 다음 단계  
 **코딩된 UI 테스트 실행을 위한 추가 옵션:** 이 항목의 앞에서 설명한 것처럼 Visual Studio에서 직접 코딩된 UI 테스트를 실행할 수 있습니다. 또한 [!INCLUDE[TCMext](../includes/tcmext-md.md)] 또는 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]에서 자동화된 UI 테스트를 실행할 수 있습니다. 코딩된 UI 테스트가 자동화된 경우 다른 자동화된 테스트와 달리 코딩된 UI 테스트를 실행할 때는 테스트와 데스크톱 사이에 상호 작용이 필요합니다.  
  
-   [방법: Microsoft Visual Studio에서 테스트 실행](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)  
  
-   [Microsoft Test Manager에서 자동화된 테스트 실행](http://msdn.microsoft.com/en-us/0632f265-63fe-4859-a413-9bb934c66835)  
  
-   [방법: 응용 프로그램을 빌드한 후 예약된 테스트 구성 및 실행](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)  
  
-   [빌드 프로세스에서 테스트 실행](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)  
  
-   [명령줄에서 자동화된 테스트 실행](http://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)  
  
-   [방법: 데스크톱과 상호 작용하는 테스트를 실행하도록 테스트 에이전트 설정](~/E:/Repos/visualstudio-docs-pr/docs/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)  
  
-   [&#91;사용되지 않음&#93; 부하 테스트에서 코딩된 UI 테스트 사용](http://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)  
  
 **사용자 지정 컨트롤에 대한 지원 추가:** 코딩된 UI 테스트 프레임워크에서는 가능한 모든 UI를 지원하지는 않으므로 테스트하려는 UI가 지원되지 않을 수도 있습니다. 예를 들어 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]의 UI에 대한 코딩된 UI 테스트는 바로 만들 수 없습니다. 그러나 코딩된 UI 테스트 프레임워크에 대한 확장을 만들어 사용자 지정 컨트롤을 지원할 수 있습니다.  
  
-   [컨트롤의 코딩된 UI 테스트 사용](../test/enable-coded-ui-testing-of-your-controls.md)  
  
-   [Microsoft Excel을 지원하도록 코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)  
  
 코딩된 UI 테스트는 일반적으로 수동 테스트를 자동화하는 데 사용됩니다. 추가 지침은 [Visual Studio 2012를 사용한 지속적인 업데이트 테스트 – 5장: 시스템 테스트 자동화](http://go.microsoft.com/fwlink/?LinkID=255196)를 참조하세요. 수동 테스트에 대한 자세한 내용은 [&#91;사용되지 않음#93; Microsoft Test Manager를 사용하여 수동 테스트 사례 만들기](http://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e)를 참조하세요. 자동화된 시스템 테스트에 대한 자세한 내용은 [Microsoft Test Manager를 사용하여 자동화된 테스트 만들기](http://msdn.microsoft.com/en-us/7b5075ee-ddfe-411d-b1d4-94283550a5d0)를 참조하세요.  
  
## <a name="external-resources"></a>외부 리소스  
  
### <a name="guidance"></a>지침  
 [Visual Studio 2012를 사용한 연속 배달 테스트 - 2장: 단위 테스트: 내부 테스트](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Visual Studio 2012를 사용한 지속적인 업데이트 테스트 - 5장: 시스템 테스트 자동화](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>FAQ  
 [코딩된 UI 테스트 FAQ - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [코딩된 UI 테스트 FAQ - 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>포럼  
 [Visual Studio UI 자동화 테스트(CodedUI 포함)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [코드 품질 향상](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [코딩된 UI 테스트 분석](../test/anatomy-of-a-coded-ui-test.md)   
 [최선의 코딩된 UI 테스트 방법](../test/best-practices-for-coded-ui-tests.md)   
 [여러 UI 맵이 포함된 대형 응용 프로그램 테스트](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [코딩된 UI 테스트 편집기를 사용하여 코딩된 UI 테스트 편집](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)   
 [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Visual Studio 2010에서 코딩된 UI 테스트 업그레이드](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)   
 [기존 작업 기록에서 코딩된 UI 테스트 생성](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)


