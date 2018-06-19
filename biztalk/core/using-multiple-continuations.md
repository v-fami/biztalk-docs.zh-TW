---
title: 使用多個接續 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01a38087-71ee-40b3-a957-6a2653bd6435
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e27a73fae39a55f05650c08397616f3cbe4fa80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288934"
---
# <a name="using-multiple-continuations"></a>使用多個接續
在有多個活動的環境中使用「追蹤設定檔編輯器」(TPE) 時，您必須瞭解追蹤活動所在的實例，才能以正確順序對應接收埠、協調流程和傳送埠。  
  
 在追蹤設定檔中，TPE 會自動評估活動的開始和結束。 當收集到第一個資料片段時，此活動會開始，而當收集到最後一個片段時，此活動會結束。  
  
 在大部分情況下，對開發人員而言，建立單一接續 (例如，兩個協調流程之間的接續) 是很簡單的程序。 TPE 呈現的複雜度是多個接續的案例。 有多個接續的實例即代表「商務活動監控」(BAM) 活動會跨越多個接收埠、協調流程和傳送埠。 若要收集一筆記錄中的 BAM 資料，您必須在所有 BizTalk Server 排程之間建立接續。 如果是透過 TPE 使用者介面 (UI) 來完成，這個處理程序可能會很複雜。  
  
 本主題描述如何在不同的實例中建立單一和多個接續。  
  
#### <a name="base-scenario-description---multiple-receive-ports-orchestrations-and-send-ports"></a>基本實例描述 - 多個接收埠、協調流程和傳送埠  
 這個實例是由含有多個接收埠 (R)、協調流程 (O) 和傳送埠 (S) 的 BizTalk Server 所組成。 其中包含用來連結接續的一般 interchangeID 內容屬性。 您可以使用任何內容屬性，例如 activityID 或其他唯一識別碼。 特定內容的選擇與實例的探討並無密切關聯。  
  
 基於此實例的目的，暫不詳述從這些連接埠及協調流程中追蹤資料項目/里程碑/內容屬性值的相關議題， 而有關對應的部分則特別限定在商務邏輯的範圍。 我們的目標是使用完成的活動資料表中的單一資料列，從所有連接埠和協調流程中擷取所有 BAM 資料。 可供協調流程用於接收和處理訊息的各種方式，帶來了一些有趣的問題和解決方案。  
  
> [!NOTE]
>  含有一個連接埠或一個協調流程的實例可以視為含有許多連接埠和許多協調流程之實例的特殊案例。  
  
#### <a name="scenario-solution-1---one-receive-port-and-one-orchestration"></a>實例解決方案 1 - 一個接收埠和一個協調流程  
 在這個實例中，訊息只會抵達其中一個接收埠 (R1)，而且只由其中一個協調流程 (O1) 來處理。  
  
 建立接續的程序如下：  
  
1.  在追蹤設定檔的資料夾活動樹狀檢視中建立接續。  
  
2.  按一下以選擇內容屬性結構描述**選取事件來源** 按鈕，然後按一下**選取內容屬性**功能表項目。  
  
3.  找出**interchangeId 屬性**中**內容屬性名稱**清單，然後加以選取。  
  
4.  從屬性結構描述中，將 interchangeID 對應至您剛才建立的接續資料夾。  
  
5.  在活動樹狀結構中新建立的 interchangeID 節點上按一下滑鼠右鍵，然後選取要做為對應起點的連接埠。  
  
6.  在**選取連接埠**對話方塊顯示時，會選取所有**N**接收埠。  
  
7.  在資料夾活動樹狀結構中建立 [continuationID] 資料夾。  
  
8.  按一下以開啟每個協調流程**選取事件來源** 按鈕，然後按一下**選取協調流程排程**功能表項目。 在每個協調流程中的圖形上按一下滑鼠右鍵，然後將 interchangeID 內容屬性對應至新建立的 continuationID。  
  
 在包含三個協調流程的部署中，追蹤設定檔看起來會像這樣：  
  
 ![TPE 多重接續案例 1](../core/media/4761d680-7218-4404-a636-06739f70f344.gif "4761d680-7218-4404-a636-06739f70f344")  
  
#### <a name="scenario-solution-2---one-receive-port-and-multiple-orchestrations"></a>實例解決方案 2 - 一個接收埠和多個協調流程  
 在這個實例中，訊息只會抵達其中一個接收埠 (R1)，而且會由每一個協調流程處理。 這會在同時傳送訊息給每一個協調流程時發生。  
  
 在這種情況下，每個協調流程都必須有接續和 continuationID。 建立接續的程序會類似於實例解決方案 1 所述的步驟。 針對三個協調流程部署，產生的追蹤設定檔看起來像這樣：  
  
 ![TPE Multiple 接續案例 2](../core/media/3cebd82f-9192-4d52-84c7-584f24e8ecca.gif "3cebd82f-9192-4d52-84c7-584f24e8ecca")  
  
#### <a name="scenario-solution-3---content-based-routing"></a>實例解決方案 3 - 以內容為基礎的路由  
 這個實例定義以內容為基礎的路由 (CBR) 解決方案。 訊息只會抵達其中一個接收埠，而且只傳送至其中一個傳送埠。 這種路由會依據訊息中的內容屬性值產生。 在這種情況下，需要一個接續。 對應看起來會像這樣：  
  
 ![接續 CBR 案例。] (../core/media/4459a73d-515f-4d6d-a68f-b18eee072df8.gif "4459a73d-515f-4d6d-a68f-b18eee072df8")  
  
> [!NOTE]
>  上述對應也適用於只抵達其中一個接收埠、但會傳送給所有傳送埠的訊息。  
  
#### <a name="scenario-solution-4---one-orchestration-multiple-send-ports"></a>實例解決方案 4 - 一個協調流程和多個傳送埠  
 在此案例中，有多個傳送。 連接埠。 只由其中一個協調流程，這取決於處理規則的宣告，並且會傳送至所有傳送埠會處理訊息。 在這種情況下，需要一個接續。 對應看起來會像這樣：  
  
 ![接續案例 4](../core/media/3ab10b51-d306-4ad1-acb6-6731e23394ac.gif "3ab10b51-d306-4ad1-acb6-6731e23394ac")  
  
#### <a name="scenario-solution-5---sequential-orchestrations"></a>實例解決方案 5 - 循序協調流程  
 在這個實例中，訊息會依序由每個協調流程逐一處理，然後透過接續傳遞給下一個協調流程。 對應看起來會像這樣：  
  
 ![接續案例 5](../core/media/563cacee-104c-4f8a-9836-da90aecb7487.gif "563cacee-104c-4f8a-9836-da90aecb7487")  
  
### <a name="collecting-data-in-an-asynchronous-environment"></a>收集非同步環境中的資料  
 當您設定接續時，BAM 就會預期有資料抵達。 在非同步環境中，您可能接收不到後端程序的回應。  
  
 如果收不到回應資料，活動執行個體便會一直等候。 活動將永遠無法完成，因此記錄就一直保留在 BAM 主要匯入資料庫的資料表中。 試想有一個長時間執行的交易，在這種情況下，無法得知剩餘的資料何時會抵達。 也沒有所謂的逾時，因為資料是否抵達取決於商務邏輯或程序，而資料抵達之後，就將活動標示為完成。 資料可能同一天抵達，或者誇張一點，來年才到。  
  
 解決方案是使用相關的活動。  
  
 請將您的活動分割成兩個活動。 讓這兩個活動產生關聯，再將該回應關聯到原始的活動。  
  
 如需相關活動的詳細資訊，請參閱[活動關係](../core/activity-relationships.md)。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)