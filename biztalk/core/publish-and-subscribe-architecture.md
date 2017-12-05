---
title: "發佈和訂閱架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publish/subscribe architecture, publishers
- architecture, publish/subscribe
- publishing, publish/subscribe architecture
- publish/subscribe architecture, about publish/subscribe architecture
- creating, subscriptions
- publish/subscribe architecture, Messaging Engine
- routing, publishing
- Messaging Engine, publishing
- publish/subscribe architecture, subscribers
- publish/subscribe architecture
- subscriptions, publish/subscribe architecture
- publish/subscribe architecture, creating subscriptions
- subscriptions, creating
- Messaging Engine, subscribing
- publishing, routing
- Messaging Engine, publish/subscribe architecture
- publish/subscribe architecture, events
ms.assetid: 5ed36c1f-077d-468f-a99e-60f97377cef6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b11ed175fc047eee59761547d8d13ab798ac860c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="publish-and-subscribe-architecture"></a>發佈和訂閱架構
在發佈/訂閱設計中，有三個元件：  
  
-   發行者  
  
-   訂閱者  
  
-   事件  
  
 發佈者包括發佈可到達其接收位置之訊息的接收埠、在非同步傳送訊息或啟動另一個協調流程時發佈訊息的協調流程，以及從目標應用程式或傳輸收到回應時發佈訊息的請求/回應傳送埠。  
  
 在 BizTalk Server 中，兩種主要的訂閱類型：啟動和執行個體。 *啟動訂閱*是指定履行訂閱的訊息應該啟動，或建立時，「 訂閱者 」 時收到的新執行個體。 建立啟動訂閱的項目範例包含具有篩選條件的傳送埠，或是與協調流程繫結的傳送埠，以及將其 [啟動] 屬性設定為 [True] 的協調流程接收圖形。 *訂用帳戶的執行個體*指出履行訂閱的訊息，應該路由傳送到 「 訂閱者 」 已在執行執行個體。 建立執行個體訂閱的項目範例為具有相互關聯之接收埠與要求/回應樣式接收埠的協調流程，這些連接埠會等待 BizTalk Server 的回應。  
  
 這兩種類型的訂閱在資訊層次的差異，在於執行個體訂閱會包含唯一的執行個體識別碼，這個識別碼是儲存在主要 MessageBox 資料庫的訂閱資料表中。 當協調流程執行個體或接收埠完成處理時，會從 MessageBox 移除執行個體訂閱，而啟動訂閱只要有登錄協調流程或傳送埠就會維持作用中。  
  
## <a name="creating-subscriptions"></a>建立訂閱  
 訂閱是由 BizTalk Server 中的服務類別所建立，它會列在 BizTalk Server 管理資料庫的 adm_ServiceClass 資料表中。 這些服務包含快取服務；由「結束點管理員」所裝載的內含式與外掛式傳訊；XLANG 子服務裝載的協調流程/XLANG。 這些服務類別的每一個都可以建立訂閱，並接收已發佈的訊息。  
  
 訂閱是比較陳述式的集合，又稱為述詞，它包含訊息內容屬性及訂閱專用的值。 例如，「訊息類型」是訊息的內容屬性，而且許多訂閱會在其訂閱中指定訊息類型。 「訊息代理程式」會在訂閱資料表中插入訂閱的一般資訊，而特定述詞會根據為訂閱所指定的作業類型而定，插入至下列其中一個述詞資料表中：  
  
-   BitwiseANDPredicates  
  
-   EqualsPredicates  
  
-   EqualsPredicates2ndPass  
  
-   ExistsPredicates  
  
-   FirstPassPredicates  
  
-   GreaterThanOrEqualsPredicates  
  
-   GreaterThanPredicates  
  
-   LessThenOrEqualsPredicates  
  
-   LessThenPredicates  
  
-   NotEqualsPredicates  
  
 這些全部都透過呼叫 bts_createsubscription_<\<應用程式名稱\>與 bts_insertpredicate_<\<應用程式名稱\>預存程序，在 MessageBox 資料庫 where \<應用程式名稱\>是建立訂閱之 BizTalk 主控件名稱。  
  
 在登錄傳送埠時，連接埠至少會為任何內容中具有該傳送埠傳輸識別碼的訊息建立訂閱。 這允許傳送埠永遠接收專門給它的訊息。 當協調流程連接埠與特定傳送埠繫結時，繫結的相關資訊會儲存在 BizTalk 管理資料庫中。 當訊息從協調流程透過繫結至實體傳送埠的連接埠傳送時，會在內容中包含「傳送識別碼」，讓訊息可路由至該傳送埠。 不過，請務必注意，此傳送埠並不是唯一可接收從協調流程傳送之訊息的傳送埠。 當協調流程傳送訊息時，會將該訊息伴隨著所有相關的升級屬性發佈到 MessageBox。 繫結的傳送埠保證會接收訊息的複本，因為傳輸識別碼在內容中，不過任何其他傳送埠或協調流程，都可以有同樣符合訊息屬性的訂閱。 瞭解不論在何時都會將訊息直接發佈到 MessageBox 是非常重要的，所有具有符合訂閱的訂閱者都會收到訊息的複本。  
  
## <a name="publishing-and-routing"></a>發佈和路由  
 在建立和啟用訂閱後，必須先發佈訊息才會執行任何處理。 當 BizTalk Server 從前面所提及的其中一個服務收到訊息時，就會發佈它們。 在本路由討論中，我們將著重於 BizTalk Server 透過配接器收到的訊息。  
  
 當訊息進入接收管線處理時，會將屬性升級至訊息內容。 在接收配接器與管線處理過訊息後並準備將它發佈至 MessageBox 時，第一個執行的動作是「訊息代理程式」會將升級屬性的屬性值與訊息內容的述詞值插入至主要 MessageBox SQL Server 資料庫。 在資料庫中包含這些值可讓「訊息代理程式」進行路由決策。  
  
 「訊息代理程式」的下一步驟是要求主要 MessageBox 資料庫尋找已發佈之目前批次訊息的訂閱。 請記住，訊息並未寫入至資料庫，而是只寫入內容的屬性。 MessageBox 查詢中的 bts_FindSubscriptions 預存程序會查詢上述所識別的訂閱與述詞資料表，將它們連結到針對目前的訊息批次所儲存的訊息屬性。  
  
 透過此訊息，「訊息代理程式」會呼叫 bts_InsertMessage 預存程序，將訊息插入至具有訂閱的每個 MessageBox 資料庫一次。 訂用帳戶 id。 第一次呼叫 bts_InsertMessage 預存程序 此第一階段中，預存程序呼叫 int_EvaluateSubscriptions 預存程序會負責查閱訂用帳戶的詳細資訊，確認訊息符合安全性需求的應用程式，藉由檢查，述詞符合應用程式內容主機，以及應用程式特定擱置的佇列根據狀態的應用程式特定佇列中插入訊息的參考訊息。 針對為此應用程式所找到的每個訂閱，在應用程式特定的佇列資料表中，插入訊息識別碼、訂閱識別碼、服務識別碼，以及其他訂閱資訊。 插入訊息之後，即會清除訊息屬性與訊息述詞資料表的批次相關值。  
  
 接著會為訊息中的每個部分呼叫 bts_InsertMessage 預存程序。 在第一次呼叫時，訊息內容會傳遞，然後會插入多工緩衝處理資料表，例如組件、 內文部分名稱和識別碼的多訊息相關的中繼資料 除了訊息內文部分會插入至 PARTS 資料表使用 int_InsertPart 預存程序。 接著為每個其餘的訊息部分呼叫 bts_InsertMessage 預存程序，在此會將這些訊息部分直接傳遞至 int_InsertPart預存程序，以便將它們保存在 PARTS 資料表中。  
  
 路由訊息時，會在下列資料表中插入記錄，以便為每個收到訊息特定執行個體及其部分的每個服務新增參考：  
  
-   MessageRefCountLog1  
  
-   MessageRefCountLog2  
  
-   PartRefCountLog1  
  
-   PartRefCountLog2  
  
 透過清除定期執行的工作，讓 MessageBox 不會被系統中不再存在的訊息資料所佔滿，這些參考可以避免訊息和部分遭到刪除。 有兩個資料表可用來降低爭用和鎖定的問題。  
  
 既然已將訊息路由至正確的佇列、儲存在 Spool 與 Parts 資料表，以及在應用程式特定佇列中參考它，應用程式執行個體就必須將訊息從佇列提取出來。 每個主控件執行個體都有一些取消佇列的執行緒，它們會不斷地每隔一段時間即輪詢資料庫，而此間隔時間是設定在 BizTalk 管理資料庫的 e adm_ServiceClass 資料表中。 此相同資料表有一個資料行指出要使用之取消佇列執行緒的數目。 每個執行緒呼叫 MessageBox 資料庫，並呼叫 bts_dequeuemessages_<\<應用程式名稱\>預存程序適用於執行中的主應用程式。 這個預存程序會使用鎖定語意，以確定只有一個執行個體，一個清除佇列執行緒可以在指定的時間在佇列中的訊息上運作。 取得鎖定的主控件執行個體可取得訊息，且需負責將訊息交給它所需的子服務。  
  
 若接收訊息的服務是「結束點管理員」，會叫用傳送埠 (或是要求/回應接收埠的回應部分)，但若它是 XLANG/s 子服務，則會根據訂閱中是否有執行個體識別碼來決定，要建立協調流程，或定位為服務訂閱。 接著服務會釋放對訊息及其部分的參考，以便在其他服務沒有參考時，就可以刪除訊息資料。  
  
## <a name="see-also"></a>請參閱  
 [傳訊引擎](../core/the-messaging-engine.md)