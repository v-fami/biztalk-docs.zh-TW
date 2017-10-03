---
title: "協調流程偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging, Orchestration Debugger
- debugging, orchestrations
- Orchestration Debugger, about Orchestration Debugger
- Orchestrations Debugger
- orchestrations, debugging
- debugging, HAT
- HAT, debugging
ms.assetid: aae99cfd-d3dd-41c8-ae7a-b2733352cd69
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c231513ad75520fcadd88e5dd7d88104ddeeced5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-an-orchestration"></a>偵錯協調流程
「協調流程偵錯工具」能讓您依圖形逐步追蹤單一協調流程執行個體的活動。 它會顯示「協調流程偵錯工具」中建立之轉換的協調流程檢視。  
  
 您存取在 BizTalk Server 管理主控台的 [群組概觀] 頁面中的協調流程偵錯工具。  這是透過快顯功能表的追蹤查詢輸出中以滑鼠右鍵按一下任何服務或與協調流程類型的執行個體相關聯的訊息。 一旦您在我此頁面上，您可以來回切換協調流程偵錯工具和訊息流程 檢視之間。  
  
 「協調流程偵錯工具」提供下列功能：  
  
-   顯示轉換的協調流程檢視，您可以在其中重新執行該特定協調流程的每一個處理步驟。  
  
-   可讓您在任何協調流程圖形之前設定中斷點並繼續執行。  
  
-   可讓您查看特定變數與訊息資料。  
  
-   當執行個體在「協調流程偵錯工具」中開啟時，自動啟用特定協調流程執行個體的所有追蹤選項。  
  
-   它提供您繼續、在偵錯下繼續，以及終止特定協調流程執行個體的能力。  
  
    > [!NOTE]
    >  當您解除部署組件時，資料庫會保留該解除部署組件的追蹤選項與中斷點資訊。 若您之後部署相同的組件，就會還原該組件的選項與中斷點資訊。  
  
 使用「協調流程偵錯工具」有兩種模式：  
  
-   [協調流程偵錯工具中的報告模式](../core/reporting-mode-in-orchestration-debugger.md)  
  
-   [協調流程偵錯工具中的互動模式](../core/interactive-mode-in-orchestration-debugger.md)  
  
 根據服務的狀態而有不同的能力。 您可以從任何檢視叫用目前於「在中斷點」狀態的任何服務執行個體，以執行互動式偵錯。 如需偵錯協調流程的資訊，請參閱[如何叫用協調流程偵錯工具和訊息流程檢視](../core/how-to-invoke-the-orchestration-debugger-and-the-message-flow-views.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [協調流程偵錯工具使用者介面](../core/orchestration-debugger-user-interface.md)  
  
-   [使用協調流程偵錯工具時的考量](../core/considerations-when-using-orchestration-debugger.md)  
  
-   [使用協調流程偵錯工具檢視](../core/working-with-the-orchestration-debugger-view.md)