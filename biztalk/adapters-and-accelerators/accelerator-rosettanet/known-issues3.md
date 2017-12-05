---
title: "在 BizTalk Server RosettaNet 加速器的已知問題 |Microsoft 文件"
description: "請參閱 < 已知的問題與失敗、 BAM、 安裝及設定，並在 BizTalk Server 中的 BTARN 更 0A1 通知的解決方式"
caps.latest.revision: "11"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 335eb3c9-b565-470f-b69c-2a771ef8b476
ms.author: mandia
ms.openlocfilehash: bbb7ddc2028383f8ac346e7876459f322d2dd96b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues"></a>已知問題
本節包含的有用資訊，可幫助您避免 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 的錯誤。 已知的問題可分為以下各類：  
  
-   0A1 失敗通知  
  
-   商務活動監控 (BAM)  
  
-   安裝與組態  
  
-   其他  
  
## <a name="0a1-notification-of-failure"></a>0A1 失敗通知  
  
### <a name="btarn-does-not-perform-cross-field-validation-for-the-cidx-process-configuration-property-and-the-0a1-agreement-property"></a>BTARN 不會對 CIDX 程序組態屬性與 0A1 協議屬性執行跨欄位驗證。  
 當您使用程序組態設定檔，將協議的「0A1 協議」屬性設為 0A1 時，即使 CIDX 不支援 0A1 協議，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 仍舊不會防止您將程序組態設定檔的「標準」屬性設為 "CIDX"。  
  
## <a name="business-activity-monitoring"></a>商務活動監控  
  
### <a name="duplicate-column-data-appears-in-the-business-activity-monitoring-reports"></a>商務活動監控報告中出現重複的欄位資料  
 在 BAM 活動 Web 報告中的 ActivityID 與 PIPInstanceID 資料欄位，包含相同的內容。 此資料正確地反映交易夥伴介面程序 (PIP) 執行個體識別碼。 ActivityID 用這個值進行內部相互關聯。 您可以忽略此訊息。  
  
### <a name="empty-data-columns-in-the-business-activity-monitoring-web-reports"></a>商務活動監控 Web 報告中出現空白資料欄位  
 商務活動監控 (BAM) Web 報告內沒有 0A1 訊息程序的任何資料。 Web 報告中的 0A1 訊息欄都是以「初始化的 0A1」進行硬式編碼。  
  
## <a name="installation-and-configuration"></a>安裝與組態  
  
### <a name="groups-and-users-in-either-the-biztalk-application-users-group-and-the-biztalk-server-administrators-group-must-be-in-the-same-domain"></a>BizTalk 應用程式使用者群組以及 BizTalk Server  Administrator 群組中的群組與使用者，必須位於同一個網域中  
 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 支援將群組加入至「BizTalk 應用程式使用者」群組或「BizTalk Server 系統管理員」群組， 但隸屬於「BizTalk 應用程式使用者」群組或「BizTalk Server 系統管理員」群組的個別使用者帳戶與群組，都必須位於同一個網域中才行。  
  
### <a name="uninstallation-of-btarn-fails-if-biztalk-server-is-removed-first"></a>如果 BizTalk Server 會先移除，就會失敗，解除安裝 BTARN  
 如果您移除 BizTalk Server，然後再移除[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]、[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]移除程序失敗，而且未發生錯誤。 若要解決此問題，重新安裝並重新設定 BizTalk Server，然後再移除[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。  
  
### <a name="distributed-deployment-requires-a-domain-controller"></a>分散式部署需要有網域控制站  
 在多伺服器環境中部署 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] (例如將 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝在某一台伺服器上，並將設定組態所需的 [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫安裝在另一台伺服器上) 時，就需要有網域控制站。  
  
### <a name="custom-pip-configurations-are-not-supported"></a>不支援自訂 PIP 組態  
 目前的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 版本不支援使用自訂項目或其他非 RosettaNet 標準資訊設定 PIP。  
  
### <a name="btarn-automatically-starts-the-single-sign-on-service"></a>BTARN 自動啟動單一登入服務  
 當 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 需要「單一登入」(SSO) 服務，但 SSO 服務並未執行時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 就會自動啟動 SSO 服務。  
  
### <a name="the-configuration-program-will-not-remove-btarn-virtual-directories-from-the-excluded-paths-list-when-webapps-is-not-configured-for-the-default-web-site"></a>未對預設網站設定 WebApps 時，組態程式不會從排除的路徑清單移除 BTARN 虛擬目錄  
 如果您取消設定 Web 應用程式虛擬資料夾設定為 [SharePoint Server] 而非 [預設的網站] 的 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 安裝，則在取消設定之後，您必須在 SharePoint 管理中心網站，以手動方式從排除的路徑清單中移除 btarnapp 和 btarnhttpreceive 虛擬目錄。 發生這種情況是因為在設定 Web 應用程式虛擬資料夾為 [SharePoint Server] 時，您必須將 btarnapp 和 btarnhttpreceive 以手動方式加入到排除的路徑清單。 組態程式不會從排除的路徑清單自動移除它們。  
  
## <a name="miscellaneous"></a>其他  
  
### <a name="btarn-will-receive-messages-encrypted-in-either-encryption-algorithm"></a>BTARN 可接收用任何一種加密演算法加密的訊息  
 即使用於加密訊息的通訊協定與此欄位的「編碼」設定不符，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 接收管線仍然會接收並解密訊息。 因此，不論是以 RC2-40 或 3DES 加密的訊息，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 都會接收。  
  
### <a name="btarn-requires-a-signal-in-a-single-action-synchronous-scenario"></a>在單向動作同步實例中，BTARN 需要收到信號  
 在單向動作同步實例中，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 都會等待接收信號，也會產生信號。 此行為與 RosettaNet 規格的定義不同。根據 RosettaNet 規格，在單向動作同步實例中，信號可以為必要或非必要。 若 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 為回應者，當 BTARN 收到來自啟動者的訊息後，一定會產生信號做為回應。 如果 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 是啟動者，則 BTARN 會一直等待回應者傳回信號。 如果 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 在程序組態設定的 `Time To Perform` 屬性中指定的時間內都沒有收到信號，就會視為逾期，並產生 0A1 訊息。  
  
### <a name="btarn-supports-utf-16-in-received-messages"></a>BTARN 可以接收 UTF-16 的訊息  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]接收和處理 utf-16 字元集的訊息。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]傳送訊息的 utf-8 的字元集。  
  
### <a name="namespaces-must-be-stripped-from-response-messages-mapped-from-request-messages"></a>從要求訊息對應的回應訊息中，其命名空間必須加以刪除  
 若您在雙向動作實例的私用程序中使用 BizTalk 對應工具，BizTalk 對應工具將會在對應要求訊息的回應訊息執行個體中，新增命名空間至部分項目標記。 這些命名空間會導致傳送管線的失敗。 您必須移除這些命名空間。 請用 HeaderHelper 範例進行這項作業。 如需詳細資訊，請參閱[雙向動作 PIPAutomation 協調流程 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)和[步驟 4： 建立 HeaderHelper 專案 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md).  
  
### <a name="changing-uri-settings-requires-iisreset"></a>變更 URI 設定需要使用 IISRESET  
 執行安裝程式時，您會設定接收與傳送 .aspx 頁面要使用的 URI 設定，以及接收配接器與傳送配接器的 URI 設定。 如果您變更了 .aspx 頁面或配接器所在電腦的電腦名稱，就必須變更這些設定。 您可以重新執行組態程序以變更這些設定，但是這麼做將需要重設所有的組態設定。 您也可以變更關聯的登錄機碼 (`AsyncReceivePortURI`、`RNIFSenderURI` 和 `SyncReceivePortURI`)，這樣就只會變更 URI 設定而已。 變更上述任何一項登錄機碼設定之後，您必須執行 IISRESET，變更才會生效。 這是因為 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會快取設定以供本身使用。 執行 IISRESET 後，還必須重新啟動 BizTalk 服務。  
  
### <a name="btarn-does-not-enforce-restrictions-on-rnif-v11-enumerations"></a>BTARN 不會對 RNIF v1.1 列舉強制執行限制條件  
 RosettaNet 實作架構 (RNIF) 規格 v1.1 某些 RNIF 結構描述列舉型別上指定的限制。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]不會強制這些限制，並不會驗證符合這些限制。 這些限制不適用於 RNIF v2.01。  
  
 上述原則適用於下列服務標頭項目：  
  
-   `GlobalBusinessActionCode`  
  
-   `GlobalPartnerClassificationCode`  
  
-   `GlobalBusinessServiceCode`  
  
-   `GlobalProcessCode`  
  
-   `GlobalProcessIndicatorCode`  
  
-   `VersionIdentifier`  
  
### <a name="performancecontrolrequest-parameters-will-not-override-default-process-configuration-settings"></a>PerformanceControlRequest 參數不會覆寫預設的程序組態設定  
 內送訊息的服務標頭中可以含有 `PerformanceControlRequest` 參數。 這些參數包括在進行中的程序組態設定中所設定的通知 （接收） 和執行，時間的時間延遲參數值[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]不會以動態方式設定為基礎的時間延遲`PerformanceControlRequest`內送訊息中的參數。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]一律會在程序組態設定中設定之預設 PIP 值中的時間延遲。 這符合 RosettaNet 實作架構 (RNIF) 規格 v1.1。  
  
### <a name="the-pip-name-and-pip-version-of-double-action-messages-are-case-sensitive"></a>雙向動作訊息的 PIP 名稱與 PIP 版本有區分大小寫  
 若回應訊息的 PIP 名稱與 PIP 版本的大小寫，與原始雙向動作要求訊息中對應值的大小寫不同，則啟動者 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將回應訊息視為無效而拒絕，並產生例外狀況傳回給回應者。  
  
### <a name="btarn-does-not-support-changing-agreement-settings-while-there-are-active-processes"></a>當有作用中的程序時，BTARN 不支援變更協議設定。  
 協議屬性變更會套用，當您按一下**套用**或**確定**接受條款。 在您更改了協議之後，只要牽涉到該協議的執行中程序或新程序，其中的所有新活動都會使用變更過的協議屬性。 在您變更協議的同時，如果有正在執行的程序，此程序可能已經對訊息使用了先前的協議屬性。 然而，這個程序的新訊息會使用新的協議設定，這樣將導致無法預測的後果。 建議您最好在沒有執行任何程序時，才對協議設定進行變更。  
  
### <a name="btarn-will-not-perform-cross-field-validation-after-changes-to-a-process-configuration-profile"></a>變更了程序組態設定檔之後，BTARN 並不會執行跨欄位驗證  
 當您建立程序組態設定檔，然後建立協議時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會執行跨欄位驗證，以確保協議屬性與設定檔相容。 例如，若設定檔的「標準」屬性設為「CIDX」，BTARN 就會檢查協議的「0A1」協議屬性是否設為「No 0A1」。 不過，若您在建立協議之後才變更程序組態設定檔，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 就不會執行跨欄位驗證。 若將「標準」屬性從「RosettaNet」變更為「CIDX」，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 並不會驗證協議的「0A1」協議屬性是否設為「No 0A1」。  
  
### <a name="errors-will-result-if-all-orchestrations-are-not-started"></a>如果協調流程並未全部啟動，就會發生錯誤  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式安裝了九項協調流程。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 若要能成功地處理訊息，您必須在啟動處理作業之前，繫結、登錄與啟動這九項協調流程。 如需詳細資訊，請參閱在 BizTalk Server 說明中的 「 協調流程管理在 BizTalk 總管 」 或 「 管理協調流程 」 主題。  
  
### <a name="rnifreceiveaspx-does-not-remove-the-mime-bottom-boundary-from-a-message"></a>RNIFReceive.aspx 並未刪除訊息的 MIME 下界限  
 當 RNIFReceive.aspx 頁面從夥伴的 RNIFSend.aspx 頁面接收訊息時，該訊息中會含有 MIME 標頭與以及 MIME 上下界限 (base 64 數字)。 RNIFSend.aspx 會為 RNIF 傳輸，新增標頭與界限至訊息。 RNIFReceive.aspx 提交訊息至公開程序前，應移除訊息中的 MIME 標頭與界限。 RNIFReceive.aspx 會移除 MIME 標頭與上界限，但不會移除下界限。 遺留的下界限，並不會影響在公開程序中的訊息處理。  
  
### <a name="btarn-does-not-support-a-case-sensitive-configuration-of-sql-server-databases"></a>BTARN 不支援要區分大小寫的 SQL Server 資料庫組態  
 如果您進行[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫與資料庫物件區分大小寫，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台中找不到資料庫資源，而擲回例外狀況。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫與資料庫物件必須是不區分大小寫。  
  
### <a name="all-queries-in-database-maintenance-scripts-should-be-written-for-utc-time"></a>資料庫維護指令碼中的所有查詢都必須使用 UTC 時間  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫使用 UTC (世界標準時間) 時間，因此為維護這些資料庫的其中一個資料庫而建立的任何查詢，也都必須使用 UTC 時間。 例如，如果您的維護指令碼要使用 `GetDate()` 命令，應將其變更為 `GetUTCDate()`。  
  
### <a name="a-publicresponder-orchestration-will-reject-a-duplicate-request-action-message"></a>PublicResponder 協調流程會拒絕重複的要求動作訊息  
 當 `PublicResponder` 協調流程 (PublicResponderV11.odx) 收到重複的要求動作訊息時，會在事件日誌中記錄警告，然後拒絕該訊息。 在回應者協調流程完成後，若收到重複的訊息，由於已經沒有任何訂閱，因此 BizTalk Server 會停止該訊息。  
  
### <a name="transmission-errors-will-not-be-shown-in-bam-if-the-public-process-has-stopped"></a>公開程序停止後，傳輸錯誤不會顯示在 BAM 中  
 當公開程序協調流程處理其最終訊息時，若發生傳輸錯誤，事件日誌與 HAT 會顯示錯誤，但 BAM 不會顯示該項錯誤。 這是因為協調流程已停止，因此 BAM 無法顯示訊息。  
  
### <a name="the-pipelineexe-tool-cannot-be-used-to-debug-a-btarn-receive-pipeline"></a>pipeline.exe 工具不能用來對 BTARN 接收管線進行偵錯  
 要對接收管線進行偵錯，則必須建立裝載該管線的連接埠， 您無法使用 BizTalk Server 提供的 pipeline.exe 工具偵錯。  
  
### <a name="an-error-may-be-generated-for-a-retried-message-that-is-successfully-processed-after-the-orchestration-finishes"></a>可能因為重試訊息在協調流程完成後才成功處理完畢而產生錯誤  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 使用協調流程代表處理流程。 在某些情況下，在其中幾個重試的訊息時重試，之前的重試的訊息抵達 BizTalk MessageBox 中,，可能會成功地完成協調流程。 這種狀況發生時，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 會產生對應的「完成但捨棄」錯誤訊息。 此時應該查看商務營運系統 (LOB) 應用程式，才能判斷該程序是否已經完成。 如果 LOB 應用程式表示程序已成功完成，您就可以忽略「完成但捨棄」訊息。  
  
### <a name="an-xml-file-exported-from-trackingxls-may-have-incorrect-fields"></a>從 tracking.xls 匯出的 XML 檔案可能含有不正確的欄位  
 當您在追蹤 XLS 檔案內定義新的追蹤檢視，並從這個追蹤 XLS 檔案匯出 XML 檔案時，某些欄位的名稱可能會被稍微修改。 請把您自訂的追蹤 XML 檔案中的這些欄位，和 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式安裝的標準 tracking.xml 欄位比對，就可以找出並予以更正。  
  
### <a name="rnif-11-service-header-schema-for-signals-and-responses-may-need-modification"></a>信號和回應的 RNIF 1.1 服務標頭結構描述可能需要修改  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 提供所有現成的 RosettaNet 標頭結構描述。 某些實作使用 [信號控制] 和 [動作控制] 節點的方式較為不同，如下所述。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 提供現成的「信號控制」項目，如下所示。 請注意，以下也可能適用於「動作控制」項目。  
  
```  
<!ELEMENT SignalControl (  
          InstanceIdentifier,  
          PartnerRoute,  
          SignalIdentity,  
          inResponseTo)>  
```  
  
 如果您的解決方案需要的是上述序列，您就不需要作任何動作。  
  
 但是某些實作是使用下列程式碼：  
  
```  
<!ELEMENT SignalControl (  
          inResponseTo,  
          InstanceIdentifier,  
          PartnerRoute,  
          SignalIdentity)>  
```  
  
 如果您的解決方案需要這個序列，請參閱 KB 889523。 此軟體更新將會變更對應的 XML 結構描述。 請注意，這個更新只會影響 RNIF 1.1 程序。  
  
### <a name="pipautomationgetaction-sql-stored-procedure-needs-update"></a>PipAutomationGetAction SQL 預存程序需要更新  
 您必須更新 PipAutomationGetAction SQL 預存程序，才能鎖定單一記錄。 請刪除以下程式碼行：  
  
```  
IF @@ERROR <> 0  
    UPDATE MessagesToLOB SET Delivered = -1 WHERE MessageID = @tempGUID  
```  
  
 以下才是正確的 PipAutomationGetAction 預存程序：  
  
```  
CREATE PROCEDURE PipAutomationGetAction  
AS  
 SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
BEGIN TRANSACTION  
DECLARE @tempGUID nvarchar(36)  
SELECT TOP 1 @tempGUID = MessageID FROM MessagesToLOB WITH (READPAST,UPDLOCK,ROWLOCK)  
   WHERE Delivered = 0 AND MessageCategory = 10  
  ORDER BY TimeCreated  
  SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion, ServiceContent FROM MessagesToLOB  
   WHERE MessageID = @tempGUID  
For xml auto  
UPDATE MessagesToLOB SET Delivered = 1 WHERE MessageID = @tempGUID  
 COMMIT TRANSACTION  
GO  
```  
  
### <a name="you-can-customize-aspx-code-to-return-the-error-description"></a>您可以自訂 aspx 程式碼以傳回錯誤描述  
 如果您需要記錄或傳送錯誤描述，可以自訂 aspx 程式碼，將實際的文字放在回應中傳回， 方法是使用 HttpResponse.Status (此為內建 asp 要求的回應物件) 或 HttpWebResponse.StatusDescription (由 [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 呼叫 HttpWebRequest 物件的 GetResponse 方法傳回)。 若要將其中一個適用回應物件的傳回值傳回，請以 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 所附的 aspx 程式碼中 Response.StatusCode 的設定方式，對 Response.Status 的值作類似的設定。  
  
### <a name="rnif-11-messages-cannot-be-read-in-plain-text-from-non-repudiation-tables-if-the-encoding-method-is-set-to-base64"></a>如果編碼方式設定為 Base64，就無法從不可否認性資料表中讀出純文字的 RNIF 1.1 訊息  
 這種狀況只有在編碼方式設定為 Base64 時才會發生。 當編碼方式設定為 quoted-printable 或 8-bit 時，可以從不可否認性資料表中讀出純文字的訊息。 您必須將訊息檔案存成 *.eml 副檔名，然後使用 Outlook Express 開啟檔案讀取訊息，這樣 Outlook Express 就會幫您把這個訊息解碼。 您也可以利用以下的程式碼，從不可否認性資料表中讀取以 Base64 方式編碼的訊息。  
  
```  
byte[] textBytes = Convert.FromBase64String(txtEncodedText.Text);  
string plainText = Encoding.UTF8.GetString(textBytes);  
txtOutput.Text = plainText;  
```  
  
## <a name="see-also"></a>請參閱  
[疑難排解和已知問題](troubleshooting-and-known-issues-in-rosettanet.md)