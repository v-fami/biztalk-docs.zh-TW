---
title: "訂單流程程序管理員透過 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: e2b51eff-44b5-440f-a7d1-0872543e5f27
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8556bce43ba4a951d0045d22f76d4bd222fcd8f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="order-flow-through-the-process-manager"></a>透過處理序管理員的訂單流程
本章節描述如何 Southridge Video 訂單程序管理員**OrderManager**協調流程、 處理訂單。 本節會透過協調流程來產生新訂單。 本節也討論協調流程如何處理訂單的更新。  
  
> [!NOTE]
>  商務程序管理員解決方案只包含一個程序管理員，即使該程序管理員是已寫入的，這樣它才能使用一種以上的管理員。  
  
 **OrderManager**協調流程會協調實作商務程序以處理訂單的附屬協調流程。 **OrderManager**傳送的順序透過兩個階段，結合，驗證訂單、 傳送資訊到功能群組、 傳送訂單到訂單系統，透過遠端元件和更新訂單歷程記錄。 您可以新增、 刪除或修改這些階段，而不必變更**OrderManager**。  
  
> [!NOTE]
>  由於大小和範圍**OrderManager**協調流程中，您可以閱讀此節與 Microsoft Visual Studio 中開啟協調流程。  
  
## <a name="order-manager-structure"></a>訂單管理員結構  
 **OrderManager**啟動協調流程的接收圖形開始協調流程。 下圖顯示的一般結構**OrderManager**協調流程。  
  
 ![封鎖圖表的訂單管理員](../core/media/ordermanagerblockdiagram.gif "OrderManagerBlockDiagram")  
  
 第一個接收圖形會分成兩個主要分支。 右邊的分支會處理新的訂單。 左邊的分支會處理訂單取消作業。 它可接受使用者輸入，因為它有可能**OrderManager**訂單已完成之後，接收訂單取消作業。 這就是左邊主要分支處理的狀況。 分支藉由設定終止處理的旗標並將警告新增到事件日誌，來處理外掛式取消作業。 當右邊的分支內正在處理訂單時，協調流程會處理抵達的訂單取消作業。  
  
 訂單處理分支會進行部分初始化，然後進入兩個巢狀迴圈。 在訂單處理過程中，每個階段都會執行一次外部迴圈。 當階段正在處理時會執行內部迴圈。 訂單管理員也會接聽內部迴圈中訂單的可能更新。 在迴圈終止後，訂單管理員會傳送一個完成訊息。  
  
 訂單處理階段使用動態、 自我相互關聯的連接埠可通訊回到**OrderManager**協調流程。 這樣可簡化的相互關聯**OrderManager**與階段執行個體，因為它不需要使用相互關聯集。 如需自我相互關聯連接埠的詳細資訊，請參閱[連接埠繫結](../core/port-bindings.md)。  
  
## <a name="receiving-orders"></a>接收訂單  
 **OrderManager**接收訂單訊息從**OrderBroker**協調流程透過**FromBrokerPort**連接埠。 這個連接埠直接繫結至 MessageBox 資料庫。 協調流程有兩個**接收**圖形連接至連接埠： 一個用於新訂單，一個用於更新訂單。  
  
 **OrderManger**決定哪些訊息篩選條件運算式為基礎的程序。 篩選條件運算式中，訊息狀態欄位與訂單管理員類型欄位中，測試值**OrderMgrType**。 如果 [狀態] 欄位等於 ACCEPTED，而**OrderMgrType**是 cableorder，那麼順序是新和預期的這個程序管理員。  
  
 新訂單會啟動協調流程的一個新執行個體。 **OrderManager**接下來會檢查要求中的類型**決策**圖形。 如果類型是「終止」，協調流程會執行左邊的分支並終止訂單。 否則，協調流程會繼續處理訂單。 請注意，這包含接聽與此特定訂單相關的後續訊息。  
  
## <a name="initialization-for-new-orders"></a>新訂單的初始化  
 之後**OrderManager**協調流程接收初始訊息，並開始主要右邊分支，它會取得從其組態資訊**SSOConfigStore**。 它會透過定義中的單一物件**公用程式**組件。 組態值是物件的屬性。 物件會管理組態值的本機快取，與服務導向架構解決方案相似。 如需單一物件的詳細資訊，請參閱[使用 SSO 有效率地在商務程序管理解決方案中](../core/using-sso-efficiently-in-the-business-process-management-solution.md)。  
  
 如同服務導向解決方案，商務程序管理解決方案會使用密碼存放區，因為它在安裝了 BizTalk 就會出現，SSO 會快取組態資訊，如此一來這些值便能使用，並可保護資料庫連接字串和密碼這類的資訊。 基於上述所有原因，密碼存放區是非常適合放置組態資訊的位置，即使單一登入不是用於管理與後端應用程式的連線。  
  
> [!NOTE]
>  協調流程會在開始處理之前，先擷取組態資訊。 這可確保協調流程在凍結及稍後解除凍結時會使用相同的組態。 如需凍結的詳細資訊，請參閱[協調流程凍結和解除凍結](../core/orchestration-dehydration-and-rehydration.md)。  
  
 訂單管理員會使用從組態資料的一個值： **TotalStages**，訂單處理程序的階段總數。 管理員會將此值指派給區域變數， **numStages**。 它也會設定連接到外部迴圈中，兩個變數**階段**和**停止**。 **階段**指出目前的階段，而且是外部迴圈; 計數器**停止**停止值。  
  
 最後，管理員會將設定**orderStatus**變數為 「 已啟動並進入外部處理迴圈。  
  
## <a name="new-order-processing-loops"></a>新的訂單處理迴圈  
 外部迴圈的值為長時間執行**階段**變數是的值小於**numStages**變數。 外部迴圈會驅動每個階段的處理。 只要階段仍在處理中，內部迴圈就會執行。 它也會接聽訂單的可能變更。  
  
### <a name="outer-loop"></a>外部迴圈  
 協調流程會藉由指派所接收的訊息開始外部迴圈 (**NewOrderMgrMsg**) 給變數， **OrderMgrMsg**。 接著它會將階段和狀態複製到訊息的路由部分。 協調流程也會傳回位址設定位址的訊息中**StageCompletionPort**:  
  
```  
OrderMgrMsg.RoutingPart.OrderMgrReturnAddress =   
       StageCompletionPort(Microsoft.XLANGs.BaseTypes.Address);  
```  
  
 然後協調流程傳送的順序**StagePort**，請求-回應連接埠。 然後協調流程會等候來自已開始訂單處理之階段的通知。 階段傳送**OrderAck**時就會開始處理訂單訊息。  
  
> [!NOTE]
>  **OrderAck**訊息是一種.NET 類別，而不是結構描述所定義的方案中。 如需有關使用.NET 類別來定義訊息的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
 當協調流程收到通知時，它會將指派到階段**currentStage**變數並進入內部迴圈。  
  
### <a name="inner-loop"></a>內部迴圈  
 只要在內部迴圈執行**currentStage**變數等於**階段**變數; 也就是說，只要目前階段正在處理。 迴圈的主體是**接聽**圖形使用三個**接收**圖形。 在協調流程中，最左邊圖形**訂單要求**，是訂單更新機制下, 一節中所述的一部分。  
  
 當訂單處理階段完成時，它會傳送訊息至**StageCompletion**連接埠**OrderManager**協調流程。 如果因錯誤而突然終止階段，它會傳送**TerminatedMessage**。 在此情況下， **OrderManager**擲回例外狀況。 最外層的例外狀況處理常式攔截例外狀況，並傳送錯誤訊息， **OperatorPort**。  
  
 若階段傳送**OrderMgrMsg**、 **OrderManager**遞增**階段**變數。 如果有多個階段 （階段少於或等於 numstages），則協調流程會將訂單狀態**OrderMgrMsg**設為 STAGE_n_COMPLETED，其中 n 是目前階段的數目。 如果沒有更多的階段，它會將訂單狀態設為 COMPLETED 並結束這兩個迴圈。  
  
## <a name="order-updates"></a>訂單更新  
 **OrderManager**協調流程會接聽內部處理迴圈內部的訂單更新。 請注意，**接收**圖形它會使用為此， **OrderRequest**，也會使用**FromBrokerPort**。 在迴圈內部的相同連接埠上使用第二個接收圖形，來結合相互關聯集，會形成通用 BizTalk Server 模式，也就是群組模式。 您可以使用群組模式，來確保協調流程的相同執行個體會處理第一個及後續與特定作業連接的訊息。  
  
 當訂單管理員接收到第一個與訂單連接的訊息時，它會初始化兩個相互關聯集。 首先， **OrderCorrelation**，會使用客戶識別碼 (**CustID**) 以及訂單識別碼 (**OrderID**)。 訂單管理員會與訂單處理階段共用這個相互關聯。 第二個相互關聯是群組相互關聯， **OrderConvoyCorrelation**，它會使用訂單狀態 (**狀態**) 除了客戶識別碼與訂單識別碼。 **OrderRequestReceive**圖形會使用**OrderConvoyCorrelation**為沿用相互關聯集。 使用這個方式來設定相互關聯集，可以確保負責特定訂單的訂單管理員執行個體能夠接收到任何的變更。  
  
> [!NOTE]
>  請記住，相互關聯集是一個訊息屬性的群組，可用於判斷訊息是否屬於協調流程的特定執行個體。 如需詳細資訊，請參閱[使用協調流程中的相互關聯](../core/using-correlations-in-orchestrations.md)。  
  
 當**OrderManager**收到後續訊息的訂單，它會先測試要求的類型。 若要求類型是 TERMINATE，「決策」圖形就會執行終止分支。 否則，協調流程會測試新的訊息，以查看它是否為更新。 更新訊息具有更高的序號 (**SeqNum**) 比原始要求。 若新訊息的序號更高，協調流程會以新訊息重新啟動訂單處理。 若原始和更新訊息具有相同或更低的序號，就會發生順序錯誤。 若序號相等，則其為重複的訂單，並標示為重複的錯誤。  
  
 如需有關**SeqNum**，請參閱[金鑰訊息和欄位](../core/key-messages-and-fields.md)。  
  
## <a name="final-steps"></a>最後步驟  
 之後結束迴圈，訂單管理員將回覆位址指派給動態連接埠**CSRCompletionPort**。 接著管理員會建構完成狀態訊息、傳送它，然後測試是否有錯誤。 若有錯誤，協調流程會執行「終止」圖形，否則它就會停止。  
  
## <a name="coordinating-with-the-stages"></a>與階段進行協調  
 這兩個**OrderBroker**協調流程與第二個處理階段協調流程 (**CableOrder2**) 歷程記錄資料庫中建立項目。 CableOrder2 協調流程會更新所輸入的歷程記錄資訊**OrderBroker**協調流程。 為了確保在更新之後，資料庫中沒有項目**OrderBroker**會使用傳遞通知，它會使用資料庫的連接埠上。  
  
 組態對應**OrderBroker**將歷程記錄資料庫的連接埠傳送至包含兩個連接埠的傳送埠群組，有一個測試組態的連接埠 (**HISTORYINSERT-SP-測試**)，另一個用於一般組態 (**HISTORYINSERT-SP**)。 若您讓群組中的兩個連接埠皆為作用中，那麼解決方案會在這兩個連接埠上傳送訊息。 因此它會要求兩個傳遞通知，但只會處理其中一個。  
  
 若要避免這種情況下，取消登錄測試連接埠 (**測試-HISTORYINSERT-SP**)，或停止應用程式測試版本。 如需傳遞通知的詳細資訊，請參閱[使用通知](../core/using-acknowledgments.md)。  
  
## <a name="errors-and-routing-repaired-messagesdesign-choices"></a>錯誤與路由修復訊息—設計選擇  
 例外狀況處理常式協調流程和訂單處理階段所使用的協調流程使用錯誤處理協調流程 (**ErrorHandlerOrch**) 來路由損壞修復的訂單。 此設計會假設有一個部門或群組將需要在表單中修復訂單。 修復的訂單不重新送出訂單仲介協調流程透過 (**OrderBroker**)。 當然，標準化訂單會在其標準化表單中修復。 解決方案的目前設計會讓處理常式協調流程將錯誤訊息路由回到原始訂單的來源。 不過，修復的訂單必須路由到錯誤處理常式協調流程上的 MSMQ 連接埠。 (解決方案測試版本會使用檔案資料夾。)接著錯誤處理常式會將已修復的訊息傳回呼叫協調流程。  
  
 這個解決方案使用這個設計，是因為訂單仲介會對訂單訊息進行重要的驗證和標準化。 接著，要求修復的訂單訊息也會在標準化表單中。 維護訊息的標準化表單，可避免必須處理訊息之已提交表單與標準化表單之間的差異性。  
  
## <a name="see-also"></a>另請參閱  
 [程序管理員邏輯](../core/process-manager-logic.md)   
 [關鍵訊息和欄位](../core/key-messages-and-fields.md)