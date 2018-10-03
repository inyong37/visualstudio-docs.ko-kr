---
title: UsedCommands 요소 | Microsoft Docs
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
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8a3f4719b6d35be56ba447279d3a85d2a3f5118
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47553183"
---
# <a name="usedcommands-element"></a>UsedCommands 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [UsedCommands 요소](https://docs.microsoft.com/visualstudio/extensibility/usedcommands-element)합니다.  
  
UsedCommands 요소 UsedCommand 요소 및 기타 UsedCommands 그룹화를 그룹화합니다.  
  
 UsedCommands 요소는 선택 사항입니다. 패키지 외부에 정의 된 명령을 호출 하지 않으면.vsct 파일의이 섹션을 포함할 필요가 없습니다.  
  
## <a name="syntax"></a>구문  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[UsedCommand 요소](../extensibility/usedcommand-element.md)|다른 코드에서 구현 되는 명령입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[CommandTable 요소](../extensibility/commandtable-element.md)|통합된 개발 환경 (IDE)에 VSPackage가 제공 하는 명령 (예: 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자)를 나타내는 모든 요소를 정의 합니다.|  
  
## <a name="example"></a>예제  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>참고 항목  
 [UsedCommand 요소](../extensibility/usedcommand-element.md)   
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
