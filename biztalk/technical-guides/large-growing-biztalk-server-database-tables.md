---
title: "大型成長 BizTalk Server 資料庫資料表 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30372f7-ab90-4ebb-9022-ac3ae3309459
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f427862d90c119c831bffc59e1a6e55a25700a68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="large-growing-biztalk-server-database-tables"></a>大型成長的情況的 BizTalk Server 資料庫資料表
下表列出[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]通常成長的最大的資料表。 您可以使用這項資料來判斷可能有潛在的問題。  
  
|Table|Description|註解|  
|-----------|-----------------|--------------|  
|*HostNameQ*_Suspended 資料表|此資料表包含多工緩衝處理資料表中特定的主控件擱置的執行個體相關聯的訊息的參考。 此資料表是 BizTalkMsgBoxDb 資料庫中。|如果*HostNameQ*_Suspended 資料表有多筆記錄，資料表可以包含有效擱置的執行個體中出現的**群組中樞**頁面。 您可以終止這些執行個體。 如果這些執行個體不會出現在**群組中樞**，執行個體可能會快取執行個體或被遺棄路由失敗報告。 當您終止擱置的執行個體時，您清除這個資料表中的項目和其相關聯的資料列中的多工緩衝處理和執行個體的資料表。|  
|*HostNameQ*資料表|此資料表包含多工緩衝處理資料表中特定的主控件相關聯，且不會暫停訊息的參考。 此資料表是 BizTalkMsgBoxDb 資料庫中。|如果*HostNameQ*資料表有多筆記錄，可能存在下列種類的執行個體：<br /><br /> 已備妥的執行執行個體<br />-使用中的執行個體<br />-已凍結執行個體<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]需要 「 趕上 」，並處理執行個體的時間。 這個資料表可以增長時處理內送速率 outpaces 處理外寄速率。 此案例中也可能是因為大型 BizTalkDTADb 資料庫或 SQL Server 磁碟延遲。|  
|多工緩衝處理、 組件和片段的資料表|這些資料表儲存在 BizTalkMsgBoxDb 資料庫的實際訊息資料。|已凍結，或已暫停，且目前正在使用的是，具有許多記錄表示大量訊息的多工緩衝處理、 組件和片段的資料表。 根據大小、 組件的數目和片段設定，這些資料表中的，單一訊息可能會產生所有這些資料表。 每個訊息都有多工緩衝處理資料表中的一個資料列和 Parts 資料表中的至少一個資料列。|  
|執行個體資料表|此資料表會儲存在 BizTalkMsgBoxDb 資料庫中的所有執行個體和其目前的狀態。|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]許多暫停的執行個體保留在執行個體資料表不應該允許系統管理員。 如果商務邏輯需要長時間執行的協調流程，應只會保留許多凍結的執行個體。 請記住一個服務執行個體可以與多工緩衝處理資料表中的許多訊息相關聯。|  
|TrackingData*_x_x*資料表|此資料表會儲存在 BizTalkMsgBoxDb 資料庫的追蹤資料解碼 Service (TDDS) 將事件移至 BizTalkDTADb 資料庫中追蹤的事件。|如果 TrackingData_*x_x*資料表很大，可能是 TDDS 未執行或未成功執行。 如果 TDDS 正在執行，請檢閱事件記錄檔和 TDDS_FailedTrackingData 資料表取得的錯誤資訊，BizTalkDTADb 資料庫中。|  
|Tracking_Fragments*x*，Tracking_Parts*x*，Tracking_Spool*x*資料表|這些資料表的兩個是 BizTalkMsgBoxDb 和 BizTalkDTADb 資料庫中。 其中一個已上線，而且其他離線。|**TrackedMessages_Copy_BizTalkMsgBoxDb** SQL Server Agent 作業追蹤的訊息內文會直接移至 BizTalkDTADb 資料庫中的這些資料表。|  
|dta_ServiceInstances 資料表|此資料表會儲存在 BizTalkDTADb 資料庫中的服務執行個體的追蹤的事件。|如果此資料表很大，BizTalkDTADb 資料庫。 可能是大|  
|dta_DebugTrace 資料表|此資料表會儲存在 BizTalkDTADb 資料庫中的協調流程偵錯工具事件。|如果 dta_DebugTrace 資料表有多筆記錄，協調流程圖形追蹤正在使用或所使用。 如果協調流程偵錯不例行作業需要，停用追蹤的所有協調流程的協調流程圖形。 如果已停用追蹤的協調流程圖形 BizTalkMsgBoxDb 資料庫中的待處理項目，可能會繼續成長，因為 TDDS 會繼續將此資料移入 dta_DebugTrace 資料表 dta_DebugTrace 資料表。<br /><br /> 若要控制 BizTalkDTADb 追蹤資料庫的大小，您可以選擇停用全域追蹤。 如需詳細資訊，請參閱[如何關閉全域追蹤](http://go.microsoft.com/fwlink/p/?LinkId=153687)(http://go.microsoft.com/fwlink/p/?LinkId=153687)。 如需追蹤資料庫大小調整指導方針的詳細資訊，請參閱[追蹤資料庫大小的指導方針](http://go.microsoft.com/fwlink/p/?LinkId=153688)(http://go.microsoft.com/fwlink/p/?LinkId=153688)。|  
|dta_MessageInOutEvents 資料表|此資料表會儲存在 BizTalkDTADb 資料庫中的追蹤的事件訊息。 這些追蹤的事件訊息包含訊息內容資訊。|如果 dta_DebugTrace 資料表和 dta_MessageInOutEvents 資料庫中的資料表 BizTalkTrackingDb 太大，您可以截斷資料表手動後停止追蹤主控件。 指示如何截斷資料表，如下所示的 Microsoft 知識庫文章 952555，「 dta_DebugTrace 資料表 」 一節底下的程序的[如何維護和疑難排解 BizTalk Server 資料庫](http://go.microsoft.com/fwlink/p/?LinkId=158847)(http://go.microsoft.com/fwlink/p/ 嗎？LinkId = 158847)。|  
|dta_ServiceInstanceExceptions 資料表|此資料表會在 BizTalkDTADb 資料庫中儲存任何已擱置的服務執行個體資訊時發生錯誤。|Dta_ServiceInstanceExceptions 資料表通常會變為大型定期已擱置的執行個體的環境中。|