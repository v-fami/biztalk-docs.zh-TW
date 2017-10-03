---
title: "考量和已知的問題的 TPE |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, known issues
- planning, Tracking Profile Editor
- Tracking Profile Editor, planning
ms.assetid: e96d85e0-e9ae-434a-b54e-5950f4a2b9c6
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d630b2cfa5cca1d7a441796ef8c555d02bb04910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-and-known-issues-for-tpe"></a>TPE 的考量和已知問題
當您使用追蹤設定檔和 TPE 時，應該考量下列問題。  
  
## <a name="naming-folders-in-the-tpe"></a>在 TPE 中命名資料夾  
 在追蹤設定檔編輯器中命名資料夾時，請注意下列命名需求：  
  
-   資料夾名稱和資料項目執行個體值的組合長度不能超過 128 個字元。  
  
-   就 Continuation 和 ContinuationID 資料夾而言，資料夾的命名是讓兩個協調流程相互關聯的關鍵。 例如，如果協調流程 A 是協調流程 B 的父系，則協調流程 A 包含的接續資料夾名稱，會直接對應至協調流程 B 中的 ContinuationID 資料夾。  
  
## <a name="developing-orchestrations-for-the-tpe"></a>開發 TPE 的協調流程  
 如果協調流程的開頭或結尾是無效圖形，您便無法將協調流程對應至商務活動。 協調流程引擎不允許追蹤某些圖形。 其中包括：  
  
-   訊息指派  
  
-   轉換  
  
-   群組 (工作)  
  
-   暫止  
  
-   迴圈 (While)  
  
-   分支  
  
-   Terminate  
  
-   擲回  
  
-   Catch  
  
-   While 圖形  
  
 當對應至商務活動時，請使用下列指導方針，以便讓追蹤設定檔編輯器和其他 BAM 工具能夠使用那些活動：  
  
-   對於「群組」圖形，請使用非交易式「範圍」圖形。  
  
-   對於 While 圖形，請將圖形包裝在非交易式「範圍」圖形中。  
  
-   「終止」圖形則沒有解決方法，因為此圖形的結束事件絕不會發生在正常實例中。  
  
-   請勿使用任何不允許拖放作業的圖形來啟動或結束排程。  
  
## <a name="applying-tracking-profiles-that-monitor-running-processes"></a>套用可監控正在執行之處理程序的追蹤設定檔  
 如果活動包含 BAM 接續，更新追蹤設定檔可能會影響進行中的活動執行個體。 特別是，如果更新追蹤設定檔時指定由下游攔截的活動項目資料已有記錄，就可能覆寫原始值。 基本上，任何的單一事件資料流都不會受到套用追蹤設定檔更新所影響，因為每個資料流物件均與活動/資料流開始時即已備妥的設定檔特定版本緊密繫結。 但是，由於接續是將多個事件資料流相互關聯的方法，在設定檔更新時還未開始的資料流將會接受更新所指定的變更，以致可能發生上述的資料覆寫情況。 如需有關接續的詳細資訊，請參閱[活動接續](../core/activity-continuation.md)和[如何建立接續](../core/how-to-create-a-continuation.md)。  
  
## <a name="tracking-profiles-without-a-send-or-receive-shape-from-which-to-draw-message-properties"></a>追蹤沒有用來繪製訊息屬性之「傳送」或「接收」圖形的設定檔  
 接續會透過活動之間相同的內容屬性或內容資料追蹤活動。 諸如「訊息識別碼」、「服務識別碼」和「執行個體識別碼」等屬性會變更活動之間的值。  
  
 您可以使用下列方法建立追蹤設定檔以處理這種實例：  
  
-   如果協調流程透過動態繫結傳送訊息至其他協調流程，則接續可以使用全域唯一內容資料值。  
  
-   如果訊息中沒有唯一的內容資料，可以使用訊息的交換識別碼。 若要使用交換識別碼，您必須在相同的「接收」圖形上追蹤該識別碼。 如果您建立新的訊息，在交換識別碼變更建立新的訊息時，您無法使用的交換識別碼。 從「傳送」或「接收」圖形以外的任何圖形追蹤交換識別碼，並不可靠。  
  
-   只要在協調流程中使用從管線接收的完全相同訊息，您也可以使用訊息識別碼，也就是說，協調流程連接埠會繫結至管線，並且從該位置追蹤「接收」圖形和訊息識別碼。 如果您從不同的圖形追蹤訊息識別碼，追蹤到的訊息識別碼將會無效而無法用於接續。  
  
-   如果協調流程呼叫另一個協調流程和未傳遞訊息，或協調流程呼叫另一個協調流程，但是被呼叫端沒有任何 「 建構 」、 接收或傳送圖形，可以擷取內容資料值，使用者可以使用執行個體識別碼。 呼叫的協調流程的執行個體識別碼不會變更。  
  
-   如果協調流程透過執行呼叫 (而不是直接呼叫) 以載入其他協調流程，就無法使用任何靜態訊息屬性追蹤活動。 使用者無法啟用接續。 在此執行個體中執行追蹤的唯一方式，是透過包含要執行追蹤之唯一內容資料的管線傳送訊息。  
  
## <a name="you-cannot-use-a-session-id-as-a-continuation-token-for-pass-through-pipelines"></a>您無法使用工作階段識別碼當做通過管線的接續 Token  
 在追蹤設定檔中，當您從訊息內容選取項目時，追蹤設定檔會繫結至該訊息的結構描述。 在通過管線中，結構描述的名稱值是空值。 當 BAM 嘗試根據連接埠名稱和結構描述名稱載入組態時，無法對應至工作階段識別碼結構描述，並且引擎不會追蹤任何資料。  
  
 對於通過管線，如果真的需要追蹤內容資料，您可以從追蹤設定檔移除所有內容追蹤或使用 XML 管線。  
  
## <a name="using-unique-port-names"></a>使用唯一的連接埠名稱  
 列舉雙向連接埠時，TPE 會將雙向連接埠顯示為兩個邏輯連接埠 (傳送和接收埠)。 每個邏輯連接埠會顯示為相同的名稱。 BizTalk Server 可以讓您使用相同的名稱建立單向和雙向連接埠。 例如，您可以建立名為 "Port1" 的雙向連接埠，然後使用相同的名稱建立接收埠。 在這些情況中，TPE 會顯示一次接收埠並顯示兩次雙向連接埠，其中一次是當做接收埠，另一次是當做傳送埠。  
  
 在這個情況中，TPE 會將追蹤設定檔套用至兩個接收埠。 我們建議為連接埠提供唯一的名稱以協助正確識別。  
  
## <a name="using-tpe-orchestrations-with-a-parallel-shape-as-the-first-shape"></a>搭配平行圖形使用 TPE 協調流程當做第一個圖形  
 如果您使用「分叉」、「平行」或「待命」圖形開始協調流程，則無法對應其中一個分支的活動識別碼。 在平行處理的情況中，您可以對應「分叉」圖形上的 ActivityID。 您也可以讓 BAM 產生活動識別碼，以避免協調流程的最上層發生平行圖形問題。  
  
> [!IMPORTANT]
>  將活動對應至一個以上的路徑，並將 ActivityID 對應至「分叉」圖形的一個路徑，會在依照未對應 ActivityID 的路徑進行處理時造成錯誤。  
  
## <a name="availability-of-message-properties-at-design-time"></a>設計階段的訊息屬性可用性  
 建立追蹤設定檔時，並非所有的訊息屬性都可以使用。 當訊息屬性所對應的圖形位於協調流程最上層時，這是最可能發生的情況。 在這些執行個體中，訊息屬性的值為空值。  
  
 舉例來說，「待命」圖形便是協調流程中的第一個圖形。 當訊息屬性從這個圖形對應，只有下列屬性有值： InstanceID、 ServiceID 和 ServiceClassID。 (此時 MessageID 不在範圍中，並且具有空值)。  
  
## <a name="you-cannot-map-shapes-inside-a-loop-shape-to-report-a-milestone"></a>您無法在「迴圈」圖形內對應圖形以報告里程碑  
 TPE 區塊會將「迴圈」圖形內的來源對應至活動，而那些活動是對應至迴圈以外的項目。  
  
 迴圈活動是指，在協調流程中迴圈或重複的動作。 您也許可以從協調流程內迴圈的動作擷取事件。 若要執行這項操作，請建立其他活動，並對應迴圈內所有的新活動里程碑和資料。 請務必這麼做，因為迴圈中的資料處理將會在每個排程執行發生一次以上。  
  
 例如，如果您有多個明細項目在迴圈中處理採購單，如等問題 「 哪個訂單的項目價格為 $100？ 」 模稜兩可。 明確的問題如下：  
  
 哪個訂單的明細項目價格為 $100?  
  
 哪個訂單的總計/最小/最大項目價格為 $100?  
  
 建立明確的問題必須將明細項目與訂單當做兩回事來思考。 在追蹤設定檔編輯器中，根活動 (例如訂單) 會對應至迴圈外的所有動作。 子活動 (例如明細項目) 會對應至迴圈內的動作。  
  
 一般使用這些建構類型的方式是，根據與外部活動相關的內部活動，分解重複的迴圈並具有相關的活動。  
  
 您需要使用內容項目當做根活動的 ActivityID，並讓這個內容項目可以用在迴圈內部的某些訊息中。 請將活動對應至子活動底下顯示的關係節點，並將該活動命名為根活動。  
  
## <a name="tracking-profiles-spanning-multiple-applications"></a>跨越多個應用程式的追蹤設定檔  
 如果追蹤設定檔跨越多個應用程式，則必須在部署解決方案的所有應用程式之後，才能部署追蹤設定檔。 如果追蹤設定檔不是部署的最後一個項目，您會收到下列訊息，「**找不到對應來源。**「 部署精靈呼叫 BTTDeploy.exe 時。  
  
## <a name="mapping-multiple-biztalk-server-artifacts-to-a-document-reference-url-or-messageid-nodes"></a>將多個 BizTalk Server 成品對應至文件參考 URL 或 MessageID 節點  
 TPE 可以讓您從多個 BizTalk Server 成品拖放至相同的文件參考 URL 或 MessageID 節點。  
  
 在其中的多個來源會對應到相同的項目中的 BAM 活動的情況下，最後一個成品，是 BAM 期間發生處理是指保存在追蹤資料，而且可以檢視 BAM 入口網站中。  
  
## <a name="updating-btt-versions-to-match-biztalk-solution-versions"></a>更新 BTT 版本以符合 BizTalk 解決方案版本  
 BAM 開發人員和系統管理員可以藉由自動化 BTT 檔案的更新，以維護追蹤設定檔和 BizTalk 解決方案之間的版本同步。 若要這樣做，請修改**版本**屬性**DataLevel** BTT 檔案項目。 在下列範例項目中，您可以修改 TargetAssemblyName 和 SchemaName 屬性中的版本資訊。  
  
```  
<DataLevel Name="City" SourceTypeSelected="Messaging Payload" TargetAssemblyName="TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SchemaName="TheImplementationOfOrderMgmt.PurchaseOrder,TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SomXPath="/*[local-name()='<Schema>' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" XPath="/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" IsBeginActivity="true" IsEndActivity="false">  
```  
  
## <a name="some-orchestration-shapes-cannot-be-tracked-in-the-tpe"></a>無法追蹤 TPE 中的某些協調流程圖形  
 協調流程引擎不會針對下列圖形產生事件，因此在 TPE 中無法追蹤或對應這些圖形：  
  
-   工作  
  
-   所有分支  
  
-   暫止  
  
-   Terminate  
  
-   擲回  
  
-   Catch  
  
-   MessageAssignment (因為這是「建構」圖形的一部分)  
  
-   轉換 (因為這是「建構」圖形的一部分)  
  
-   迴圈  
  
## <a name="tpe-not-retrieving-deployed-tracking-profiles"></a>TPE 未擷取已部署的追蹤設定檔  
 在升級或重新部署之後，您可能會在擷取已部署的追蹤設定檔時遭遇困難。 這可能是由於 BizTalkMgmtDb 資料庫儲存於登錄中時所使用的伺服器名稱不相符。  
  
 BizTalkMgmtDb 會在群組組態期間寫入至登錄。 TPE 會使用此項目來尋找主要匯入資料庫，並篩選追蹤設定檔。  
  
 在組態期間可以用數種格式輸入伺服器名稱。 例如：  
  
-   mgmtsvr1316267,15001\inst  
  
-   MGMTSVR1316267\inst,15001  
  
 TPE 會在使用登錄項目時執行基本的字串比較。 若要擷取部署的追蹤設定檔是為了檢查預存的伺服器和資料庫名稱，並在 TPE 中輸入**設定管理資料庫** 對話方塊。  
  
#### <a name="to-determine-the-syntax-for-server-and-database-names-and-enter-it-in-the-biztalk-management-database"></a>判斷伺服器和資料庫名稱的語法，並將其輸入至 BizTalk 管理資料庫  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**自訂組態管理員**。 如需使用**自訂組態管理員**，請參閱[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。  
  
2.  瀏覽窗格中，選取**群組**以開啟群組組態頁面。  
  
3.  在**資料存放區**方格中，觀察**伺服器名稱**和**資料庫名稱**。  
  
4.  開啟 TPE，然後選取**工具**功能表項目。  
  
5.  選取**設定管理資料庫**功能表項目，以開啟**設定管理資料庫** 對話方塊。  
  
6.  在**SQL Server**文字方塊中，輸入伺服器名稱用於**伺服器名稱**欄位**資料存放區**gridon**自訂組態管理員**群組頁面。  
  
7.  在**資料庫名稱**文字方塊中，輸入資料庫名稱用於**資料庫名稱**欄位**資料存放區**gridon**自訂組態管理員**群組頁面。  
  
8.  按一下**確定**按鈕以儲存項目。  
  
## <a name="see-also"></a>另請參閱  
 [使用 TPE](../core/using-the-tpe.md)   
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)