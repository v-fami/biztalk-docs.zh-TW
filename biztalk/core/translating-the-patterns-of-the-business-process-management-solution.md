---
title: 轉譯商務程序管理解決方案的模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- artifacts, patterns
- patterns [process management solutions], orchestration boundaries
- patterns [process management solutions], translating patterns to artifacts
- orchestrations, patterns
- orchestrations, boundaries
ms.assetid: 69f37732-f235-4bbb-bc85-31b4971c95ce
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23603e66e80461baecea88648100442eb9da0166
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279094"
---
# <a name="translating-the-patterns-of-the-business-process-management-solution"></a>轉譯商務程序管理解決方案的模式
本節描述解決方案如何將模式圖轉譯為 BizTalk Server 成品。  
  
 ![商務程序管理解決方案模式](../core/media/bts-cp-business-process-management-patterns.gif "bts_cp_Business_Process_Management_Patterns")  
  
## <a name="connections"></a>連接  
 連線是解決方案元件之間的訊息路徑。 最簡易的開始處是服務介面。 BizTalk Server 可讓您輕鬆地將協調流程呈現為 Web 服務。 公開為 web 服務的協調流程的相關資訊，請參閱[如何對應至 Web 服務的協調流程](../core/how-to-map-orchestrations-to-web-services.md)。  
  
 其他的連線存在，服務與前置處理區段之間、 前置處理區段和程序管理員，以及程序管理員和處理階段之間。 連線也包含階段和後端系統之間以及前置處理和歷程記錄資料庫及服務系統之間的連線。  
  
> [!NOTE]
>  轉譯程式會對應至 BizTalk 對應。 對應是，管線的組件或**轉換**協調流程圖形。  
  
 在決定要建立同步或非同步的程序管理員連線時，必須仔細考慮。 與信用檢查不同，程序中的訂單 (例如電報服務訂購) 不太可能很快就結束。 若程序管理員連線為非同步且需要相互關聯，則管理程序的邏輯會比較複雜。 實際上，此解決方案透過發佈訊息到 MessageBox，使用程序管理員的非同步連線。  
  
 程序管理員和階段之間的連線取捨，代表著節省伺服器資源和簡化邏輯之間相似的取捨關係。 階段的處理時間較程序管理員短。 每個階段在繼續下一個階段的處理之前，都必須先完成其處理。 不過，由於我們可能會修改階段，所以程序管理員無法嚴密地連至階段。 在應用程式中，連線可描述為受限制的發佈-訂閱模型。 程序管理員透過單一專用連接埠傳送訊息至階段。 然後，階段會篩選以識別其專用訊息。  
  
## <a name="determining-orchestration-boundaries"></a>判斷協調流程界限  
 這個模式分為三個主要部分： 前置處理訊息、 管理商務程序和商務程序本身。 前置處理包含處理 Web 服務連線、將訊息轉譯為回應訊息、通知服務系統、在歷程記錄資料庫中建立項目，以及傳輸訊息至程序管理員。 在應用程式中，前置處理由單一協調流程處理。 管理商務程序由另一個協調流程處理。 受管理的商務程序會分成適當的階段。 每個階段都會對應到協調流程，以允許訂單程序中代表變更的新增和刪除動作。 訂單處理階段設計的相關資訊，請參閱 < 分割商務程序 」，在[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。  
  
## <a name="translating-the-components-into-orchestrations"></a>將元件轉譯為協調流程  
 第一個協調流程， **OrderBroker**，簡單直接地轉譯圖表。 協調流程是用來建構程序管理員的通知訊息和訂單訊息之主要對應圖形。 如需協調流程圖形的完整清單，請參閱[協調流程圖形](../core/orchestration-shapes.md)。  
  
 程序管理員的邏輯及其附屬組件則比較複雜。 如需程序管理員協調流程中，邏輯**OrderManager**，請參閱[程序管理員邏輯](../core/process-manager-logic.md)。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案中的模式](../core/patterns-in-the-business-process-management-solution.md)   
 [使用模式進行設計： 商務程序管理解決方案](../core/designing-with-patterns-the-business-process-management-solution.md)   
 [商務程序管理解決方案的模式目錄](../core/pattern-catalog-for-the-business-process-management-solution.md)