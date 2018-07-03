---
title: 如何建置協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- building, orchestrations
- building, solutions
- building, projects
- solutions, building
- projects, building
- orchestrations, building
ms.assetid: f12d5da0-fbae-4f0e-85bf-1ca2e9bf7d62
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9000c986e95270328d9c31ef4f5e3bda7f1576e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987327"
---
# <a name="how-to-build-orchestrations"></a>如何建置協調流程
在您完成協調流程繪製後，就可以將 BizTalk 專案建置到封裝可執行協調流程的組件中。  
  
 在建置程序期間，BizTalk 協調流程設計師會檢視每個圖形以判斷它是否完整且正確，若不是，則在工作清單中報告錯誤。  
  
 在 Visual Studio 中建置時有數個選項可使用：  
  
- 您可以建置協調流程所在的整個解決方案。  
  
- 您可以在解決方案中建置單一專案。  
  
- 您可以在建置專案或解決方案時略過協調流程。  
  
  若您要建置其他元件 (包括其他協調流程)，但不想建置某個特定的協調流程，則您可以在協調流程的 .odx 檔案之檔案屬性中指示不想建置它，如此就會略過它。  
  
### <a name="to-build-an-orchestration"></a>建置協調流程  
  
-   在建立協調流程之後，您需要先建置包含它的 BizTalk 專案，才能測試或使用協調流程。 您可以建置整個解決方案，或是在解決方案中建置單一專案。  
  
### <a name="to-build-a-solution"></a>建置解決方案  
  
-   在 [方案總管] 中，以滑鼠右鍵按一下方案，然後選取**建置方案**。  
  
### <a name="to-build-a-project"></a>建置專案  
  
-   以滑鼠右鍵按一下專案，然後選取**建置**。  
  
### <a name="to-build-a-project-or-solution-without-compiling-a-particular-orchestration"></a>建置專案或解決方案，而不編譯特定協調流程  
  
-   按一下對應的.odx 檔案到協調流程，然後在 [屬性] 視窗中，按一下**建置動作**屬性，並選取**無**。