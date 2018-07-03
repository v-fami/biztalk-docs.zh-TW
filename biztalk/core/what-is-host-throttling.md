---
title: 何謂主控件節流？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host throttling, outbound
- host throttling, inbound
- host throttling, about host throttling
ms.assetid: 36d1818b-c8a2-4f23-bfb3-c034ee242f69
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be272ae705fa85af7e240b5c296dae8d9c304de2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983711"
---
# <a name="what-is-host-throttling"></a>何謂主控件節流？
大部分在 BizTalk Server 上執行的處理會在稱為 BizTalk Server 主控件執行個體的邏輯實體中發生，當做 Windows 服務或外掛式主控件程序在 BizTalk Server 上執行。 為管理主控件執行個體程序對資源的使用，BizTalk Server 會利用一種透過主控件執行個體管理訊息流程和處理的可調式節流機制。  
  
 此節流機制會節制主控件執行個體的工作負載，以確保工作負載不超過主控件執行個體或任何下游主控件執行個體的容量。 此節流機制也會防止爭用內容的情況，這種情況會降低主控件執行個體程序或其他系統程序的整體效能。 當一或多個程序耗用有限的資源，對本身和 (或) 其他程序造成損害時，就會發生爭用內容。 例如，過度使用記憶體或執行緒可能造成記憶體配置失敗或高度執行緒內容切換，有可能會影響程序效能。 類似這種爭用內容的情況可能對 BizTalk Server 的整體效能造成損害。  
  
 主控件節流機制還可偵測是否未充分使用可用的資源。 若未充分使用可用資源，節流機制會允許主控件執行個體處理額外訊息。 若可用資源處於過度使用或未充分使用的狀態，主控件節流機制會持續監控，並且透過主控件執行個體調整訊息流程。  
  
 BizTalk Server 主控件節流機制可協助確保系統在最佳且可承受的層級作業。  
  
 主控件節流組態參數是在 [BizTalk Server 管理] 主控台中，以每個主控件為基礎而設定的。 請注意，為主控件設定的節流組態參數，可以套用至儲存在對應主控件執行個體中的任何或所有接收處理常式、傳送處理常式或協調流程。 若您要設定只能套用至特定接收處理常式、傳送處理常式或協調流程的節流參數，則應該執行下列動作：  
  
-   建立一個新的主控件並適當地設定節流參數。  
  
-   設定要在此主控件中執行的接收處理常式、傳送處理常式或協調流程。  
  
-   建立這個主控件的一或多個執行個體，以在您的 BizTalk Server 上執行。  
  
## <a name="inbound-host-throttling"></a>輸入主控件節流  
 輸入主控件節流，也稱為*訊息發佈節流*在 BizTalk Server 中，會套用至主控件執行個體，包含接收配接器或協調流程，將訊息發佈到 MessageBox 資料庫。 輸入主控件節流情況會在下列情況下觸發：  
  
- 記憶體數量、 執行緒數目或主控件執行個體所使用的資料庫連線數目超過中定義的閾值**設定儀表板**適用於 BizTalk 群組和選取**設定**。 這些值來測量的效能監控計數器底下**biztalk： 訊息代理程式**效能物件類別。  
  
- 下游主控件無法處理已發佈的訊息。 這會增加的值**DB 中的訊息計數**參數。 臨界值**DB 中的訊息計數**值的節流條件是可在設定的觸發程序**主機**選項**設定儀表板**。 在資料庫中的訊息計數可以測量與**資料庫的大小**下方計數器**biztalk： 訊息代理程式**效能物件類別。  
  
- **訊息發佈內送速率**主控件執行個體超過**訊息發佈外寄速率\\*** 指定**速率增加因數**值。 **速率增加因數**值定義於**設定儀表板**，**主機**，然後**速率型節流**。 訊息發佈內送和外寄速率可以測量與相對應的效能監視器計數器底下**biztalk： 訊息代理程式**效能物件類別。  
  
- 已修改預設節流行為。 [針對 BizTalk Server 效能調整使用設定儀表板](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)描述影響節流行為的不同值。  
  
  根據節流情況嚴重性的不同，會執行下列動作：  
  
- 實作主控件執行個體處理邏輯中的漸進延遲。 當「結束點管理員」(EPM) 執行緒收到來自傳輸配接器的訊息批次時，和 (或) EPM 提交一個要發佈的訊息批次至 MessageBox 資料庫時，可能會實作延遲。 處理延遲的持續時間以及持續時間遞增的速率會隨著節流情況的嚴重性增加。  
  
- 「結束點管理員」(EPM) 可使用的執行緒數目是有限制的。 EPM 接收來自配接器的訊息批次，並發佈訊息至 MessageBox 資料庫。 依照預設，EPM 設定為每一 CPU 使用 20 個執行緒。 若主控件節流機制偵測到輸入處理的負荷情況非常高，則會暫時減少 EPM 可用的執行緒數目，直到負荷情況已排除。 EPM 不能處理來自傳輸配接器的訊息或傳遞訊息批次到 MessageBox 資料庫，除非某個 EPM 執行緒可對輸入訊息批次提供服務。  
  
- 當適用時，降低記憶體和其他資源的使用率。 BizTalk Server 可以傳送指示給其他服務類別，藉由凍結執行排程、縮小記憶體快取大小以及限制需要大量記憶體的執行緒之使用量，以限制記憶體使用率。  
  
  **從配接器到 MessageBox 的輸入的訊息流程**  
  
  ![輸入從配接器到 MessageBox 的訊息流程](../core/media/inboundmsgflow.gif "InboundMsgFlow")  
  
## <a name="outbound-host-throttling"></a>輸出主控件節流  
 輸出主控件節流，也稱為*訊息處理節流*在 BizTalk Server 中，會套用至包含協調流程或傳送配接器，接收、 傳遞或處理訊息，已建立的主控件執行個體發佈至 MessageBox。 輸出主控件節流情況會在下列情況下觸發：  
  
- 記憶體數量、 執行緒數目或主控件執行個體所使用的資料庫連線數目超過中定義的閾值**資源型節流**在**設定儀表板**. 這些值來測量的效能監控計數器底下**biztalk： 訊息代理程式**效能物件類別。  
  
- **訊息傳遞內送速率**主控件執行個體超過**訊息傳遞外寄速率**\*指定**速率增加因數**值. **速率增加因數**上定義值**速率型節流**索引標籤**設定儀表板**。 訊息傳遞內送和外寄速率可以測量與對應的效能監控計數器底下**biztalk： 訊息代理程式**效能物件類別。  
  
- 主控件執行個體同時處理的訊息數目超過**程序中的每一 CPU 的訊息**\*方塊上可用的 Cpu 數目。 **內含式訊息**上定義的閾值**資源型節流**索引標籤**設定儀表板**。 主控件執行個體同時處理的訊息數目可以測量與**內含式訊息計數**下方的效能計數器**biztalk： 訊息代理程式**效能物件類別目錄。  
  
- 已修改預設節流行為。 [針對 BizTalk Server 效能調整使用設定儀表板](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)描述影響節流行為的不同值。  
  
  根據節流情況嚴重性的不同，會執行下列動作：  
  
- 在傳遞訊息到輸出傳輸配接器或用來處理訊息的協調流程引擎之前，會實作主控件執行個體處理邏輯中的漸進延遲。 處理延遲的持續時間以及持續時間遞增的速率會隨著節流情況的嚴重性增加。  
  
- 記憶體中的佇列所能保存的訊息數目是有限制的。 記憶體中的佇列，是從 MessageBox 傳遞訊息到「訊息代理程式」，再從「訊息代理程式」傳遞訊息到 XLANG 與傳送配接器時的暫時預留位置。 依照預設，記憶體中的佇列設定為每一 CPU 保留 100 個訊息。 當佇列已滿時，除非釋放記憶體中的佇列，否則不會再從 MessageBox 清除訊息佇列。  
  
- 「訊息代理程式」執行緒集區大小是有限制的。 藉由限制「訊息代理程式」執行緒集區的大小，主控件節流機制可有效降低傳遞至 XLANG 與配接器的訊息數量。  
  
   可以修改預設訊息代理程式執行緒集區大小變更**最多的引擎執行緒**值**一般**索引標籤**設定儀表板**。 如需有關如何修改此值的詳細資訊，請參閱 <<c0> [ 如何修改一般設定](../core/how-to-modify-general-settings.md)。  
  
- 當適用時，降低記憶體和其他資源的使用率。 BizTalk Server 可以傳送指示給其他服務類別，藉由凍結執行排程、縮小記憶體快取大小以及限制需要大量記憶體的執行緒之使用量，以限制記憶體使用率。  
  
  **從 MessageBox 到配接器與 XLANG 的輸出訊息流程**  
  
  ![配接器與 XLANG 的輸出訊息流向](../core/media/outboundmsgflow.gif "OutboundMsgFlow")  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何實作主控件節流](../core/how-biztalk-server-implements-host-throttling.md)   
 [針對 BizTalk Server 效能調整使用設定儀表板](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)