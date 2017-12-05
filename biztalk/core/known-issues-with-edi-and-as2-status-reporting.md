---
title: "已知問題與 EDI 和 AS2 狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d755dca-a4b6-44be-bc45-88c0b17685a0
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 691a10671c4c8ff5f2ff77065455c100784ddd0e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-with-edi-and-as2-status-reporting"></a>EDI 和 AS2 狀態報告的已知問題
本主題說明使用 BizTalk Server 中 EDI 狀態報告的已知的問題。  
  
## <a name="batch-status-reporting-data-may-not-be-updated-if-the-batch-orchestration-is-stopped-outside-of-the-partner-agreement-manager"></a>如果在夥伴協議管理員外部停止了批次協調流程，批次狀態報告資料可能不會更新。  
 批次協調流程執行個體可以透過 [批次] 頁面的 [EDI 屬性] 對話方塊停用的合作對象。 如果您以這種方式停用批次協調流程執行個體，BizTalk Server 將會更新該批次的狀態報告資料。 不過，如果您以其他方式停止批次協調流程，例如，協調流程的其中一個查詢頁面停止 [群組概觀] 頁面上的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，報告可能不會更新資料，以及可能的狀態與批次狀態報告的已過期。 例如，即使批次協調流程已經停用了，狀態報告可能還是會指出批次仍在作用中。  
  
## <a name="the-biztalk-service-needs-to-be-restarted-after-edi-status-reporting-has-been-enabled"></a>啟用 EDI 狀態報告之後必須重新啟動 BizTalk 服務  
 **徵兆**  
  
 EDI 狀態報告已經啟用，但卻無法產生 EDI 狀態報告。  
  
 **可能的原因**  
  
 BizTalk 服務在 EDI 狀態報告啟動或停用之後必須重新啟動，讓變更生效。 如果解決方案中使用的是 AS2EdiReceive 或 AS2EdiSend 管線，則 BizTalk 服務和 IIS 服務都必須重新啟動，變更才會生效。  
  
 **解決方式**  
  
 重新啟動 BizTalk 服務 (在 [電腦管理] 對話方塊中)。 如果正在方案中使用 AS2EdiReceive 管線或 AS2EdiSend 管線，重新啟動 IIS Admin service (使用*iisreset*命令)，以及。  
  
> [!NOTE]
>  啟用 AS2 狀態報告時並不需要重新啟動 BizTalk 服務或 IIS 管理服務。  
  
## <a name="the-status-report-will-display-9999-for-the-year-when-the-as2-message-date-time-in-the-message-is-a-null-value"></a>當訊息中的 AS2 訊息日期時間是空值時，狀態報告將會顯示 "9999" 的年份  
 如果內送 AS2 訊息中的 [AS2 訊息日期時間] 欄位設定為空值，則在 AS2 狀態報告中，該訊息之 [AS2 訊息日期時間] 欄位中的年份將會顯示 “9999” 的值。  
  
 如果內送 AS2 訊息中的 [AS2 訊息日期時間] 欄位無法剖析 (例如 Mon, 21 May 2007 10:08:28 NZST)，則在 AS2 狀態報告中，該訊息之 [AS2 訊息日期時間] 欄位將會設定成目前的時間。  
  
## <a name="status-reporting-is-still-configured-after-bam-tools-have-been-uninstalled"></a>解除安裝 BAM 工具之後狀態報告仍然保持已設定狀態  
 若要安裝 EDI 狀態報告，您必須安裝 BAM 工具。 不過，如果您解除安裝 BAM 工具，狀態報告仍會保持已設定的狀態。 這是原廠設定。  
  
 移除 BAM 工具之後，您將無法再透過使用者介面搜尋狀態報告資料表。 不過，如果已啟用狀態報告，BizTalk Server 還是會在狀態報告資料表中建立記錄。  
  
## <a name="only-one-edi-interchange-will-be-correlated-to-an-as2-message-in-the-status-report-ui"></a>狀態報告 UI 中只有一個 EDI 交換與 AS2 訊息相互關聯  
 如果 AS2 訊息包含多個 EDI 交換，而您嘗試顯示 AS2 訊息中多個 EDI 交換的狀態，則只有最後一個 EDI 交換會在 [交換/通知狀態] 報告中顯示。 此外， **EDI 交易控制編號**欄位在 [AS2/MDN 狀態] 報告中的只會顯示最後一個交換控制編號。 (交換控制編號可使 AS2 訊息與其 EDI 交換內容相互關聯)。  
  
 AS2 訊息中所有 EDI 交換的資料都會儲存在狀態報告資料庫中。 如果，您可以在 [交換/通知狀態] 報告中的 AS2 訊息中顯示的所有交換**Control ID Equals All**子句是狀態報告查詢。 這也可能會顯示出其他不在 AS2 訊息中的交換，不過，您可以查看其他欄位 (如 [傳送者合作對象]、[接收者合作對象] 和 [交換日期時間]) 判斷哪些 EDI 交換是在某個單一的 AS2 訊息中。  
  
## <a name="removing-the-bam-tools-from-a-group-will-prevent-you-from-viewing-edi-or-as2-status-reports"></a>從群組中移除 BAM 工具會讓您無法檢視 EDI 或 AS2 狀態報告  
 如果您從群組中移除了 BAM 工具，嘗試檢視 EDI 或 AS2 狀態報告時將會發生錯誤。 發生這種錯誤表示系統找不到預存程序 bts_GetBatchStatusRecords。 如果您在嘗試檢視 EDI 或 AS2 狀態報告時發生錯誤，請確認是否已正確設定 EDI 和 AS2 的群組、執行階段和 BAM 工具。  
  
 您可以取消設定 BAM 工具 (而不只是移除這些工具) 來避免這個問題。 取消設定 BAM 工具時，系統將會提示您取消設定相依的 EDI/AS2 功能。 如果移除 BAM 工具，就不會收到這種提示。  
  
## <a name="status-reporting-will-not-work-after-an-upgrade-if-the-bam-tools-are-not-configured"></a>如果沒有設定 BAM 工具，則在升級之後，狀態報告將無法運作  
 您必須設定 BAM 工具，EDI 和 AS2 狀態報告才能運作。 如果您將 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 的安裝升級到後續版本，而且沒有在升級程序中設定 BAM 工具，則已升級的安裝的上 EDI/AS2 狀態報告功能將無法正常運作。  
  
 如果您想要使用的狀態報告在您升級至 BizTalk Server 之後，，請確定您在執行升級之前，會設定 BAM 工具。  
  
 如果狀態報告在您執行升級之後無法運作，請在升級記錄中判斷 BAM 工具是否在升級之前設定。 如果您沒有，您可以設定 BAM 工具，並接著將部署 EdiStatusReportingActivityDefs.xml 檔案中包含的 BusinessMessageJournal BAM 活動*\<磁碟機\>*: \Program Files\MicrosoftBizTalk Server。  
  
## <a name="disabling-transaction-set-storage-affects-an-activated-batch-but-enabling-storage-does-not"></a>停用交易集儲存區會影響已啟動的批次，但是啟用儲存區不會  
 如果您在啟動批次處理協調流程的執行個體時停用了交易集的儲存區，這項變更將會立即生效。 BizTalk Server 會在啟用儲存區時儲存批次的交易集，但是在停用儲存區之後就不會儲存交易集。 您停用交易集的儲存的體，藉由清除 [儲存交易集/內容報告] 屬性 [EDI 屬性] 對話方塊的 [一般] 窗格中。  
  
 不過，如果您在交易集的儲存區停用時啟動了批次處理協調流程的執行個體，然後再啟用該儲存區，則正在建立的批次將不會儲存任何交易集。  
  
## <a name="unicode-as2-messages-will-not-be-displayed-completely-in-text-wire-format"></a>UNICODE AS2 訊息不會完全以文字電傳格式顯示  
 如果 BizTalk Server 處理採用 UNICODE 格式編碼的 AS2 訊息或 MDN，當您嘗試以文字電傳格式檢視該訊息時，BizTalk Server 將無法完整顯示訊息。 這是因為 UNICODE 格式的 "00" 位元組會解譯為資料流結尾。 不過，如果您嘗試以二進位電傳格式檢視訊息，BizTalk Server 將會完整顯示該訊息。  
  
 在啟動了 AS2 訊息的狀態報告 (在 [AS2 屬性] 對話方塊的 [一般] 窗格中)，以及啟用內送或外寄 AS2 或 MDN 訊息的儲存區 (在 [AS2 屬性] 對話方塊的 [做為 AS2 訊息接收者的合作對象] 窗格或 [做為 AS2 訊息傳送者的合作對象] 窗格中) 時，就會發生這種情況。  
  
## <a name="enabling-as2-status-reporting-and-send-port-body-tracking-simultaneously-may-cause-an-error"></a>同時啟用 AS2 狀態報告和傳送埠內文追蹤可能會造成錯誤  
 如果您啟用 AS2 狀態報告，並將傳送埠內文追蹤的同時，下列錯誤可能會顯示事件檢視器中: 「 傳訊引擎時發生錯誤刪除一或多個訊息。 」 當傳送埠是具有 AS2Send 和 AS2Receive 管線的靜態請求-回應 AS2 傳送埠時，就會發生這種情況。 發生的時機則包括啟用下列屬性時：  
  
-   中的 [AS2 屬性] 對話方塊的 [一般] 窗格的 [啟動 AS2 報告] 屬性。  
  
-   合作對象當做 AS2 訊息接收者] 窗格的 [AS2 屬性] 對話方塊中的 [將輸出編碼的 AS2 訊息儲存在不可否認性資料庫 」 的屬性。  
  
-   [傳送埠屬性] 對話方塊之 [追蹤] 窗格中的 [連接埠處理後要求訊息] 屬性。  
  
 這個問題的解決方法是清除 [將編碼的輸出 AS2 訊息儲存在不可否認性的資料庫中] 或 [連接埠處理後要求訊息] 屬性。 建議您停用 [連接埠處理後要求訊息] 屬性，讓 AS2 追蹤可以擷取內文資訊以及 AS2 狀態報告的其他資訊。  
  
## <a name="edi-and-as2-message-context-properties-are-not-available-after-upgrading-to-biztalk-2009"></a>EDI 和 AS2 訊息內容屬性都未升級至 BizTalk 2009 之後  
 升級到 BizTalk Server 之後，任何內容屬性會不顯示在狀態報告任何 EDI 或 AS2 接收的訊息升級發生之前。  升級會正確顯示的內容屬性之後，接收的訊息。  
  
 EDI 和 AS2 內容屬性集合並未儲存在舊版的 BizTalk Server 訊息的一部分，並在升級後就無法使用。 升級到 BizTalk Server 中，AS2 內容屬性會儲存為訊息的一部分之後不過 EDI 內容屬性不會。  
  
## <a name="interchange-date-for-received-documents-may-display-the-wrong-year-in-status-reports"></a>接收文件的交換日期可能會顯示在狀態報告中錯誤的年度  
 如果接收的文件以 YYMMDD 格式指定日期，BizTalk Server 會使用下列邏輯來決定的年份值：  
  
-   如果大於或等於 75 YY，年份將會顯示為 19YY。  
  
-   如果少於 75 台 YY，年份將會顯示為 20YY。  
  
 例如，如果 isa09-內送訊息的值包含 991113，[狀態] 報表會顯示日期為 11/13/1999年。  
  
## <a name="error-message-may-be-displayed-as-a-string-of-question-marks"></a>錯誤訊息可能顯示為由問號組成的字串。  
 在 BizTalk Server 當地語系化組建中，如果錯誤訊息是顯示為由問號組成的字串，您需要根據作業系統語言來變更系統地區設定，才能取得預期的錯誤訊息。 如需變更系統地區設定的詳細資訊，請參閱[變更系統地區設定](http://windows.microsoft.com/en-IN/windows-vista/Change-the-system-locale)。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md)   
 [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)