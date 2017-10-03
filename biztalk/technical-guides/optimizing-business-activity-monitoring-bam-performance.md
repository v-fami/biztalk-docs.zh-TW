---
title: "最佳化商務活動監控 (BAM) 效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9ed29b2-0be6-4a37-be68-9476832fd49f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83801a4e147b3e1eaf34c5e264d6adecfbdf8f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-business-activity-monitoring-bam-performance"></a>最佳化商務活動監控 (BAM) 效能
本主題說明商務活動監控 (BAM) 效能的因素。  
  
## <a name="bam-disk-usage-configuration"></a>磁碟使用量的 BAM 組態  
 BizTalk 系統負載下因為大量保存至 BAM 資料庫的資料時，BAM 會帶來大量負擔。 因此，審慎使用 BAM 資料庫的磁碟 I/O 技術是非常重要。  
  
## <a name="bam-eventstream-apis"></a>BAM 的 EventStream Api  
 可在 BizTalk BAM 實例中使用四種類型的 EventStreams︰  
  
-   DirectEventStream (DES)  
  
-   BufferedEventStream (BES)  
  
-   OrchestrationEventStream (OES)  
  
-   MessageEventStream (MES)  
  
 您應該選擇其中一個這些應用程式開發介面，根據下列因素：  
  
-   如果您擔心延遲，請選擇 DES，此時會使用與 BAM 主要匯入資料庫同步的方式來保存資料。  
  
-   如果您擔心事件插入的效能和輸送量，請選擇非同步 API （BES、 OES 或 MES）。  
  
-   如果您要撰寫沒有的電腦執行的應用程式安裝 BizTalk Server，請使用 DES 和 BES;這些 Api 可用於非 BizTalk 應用程式。  
  
    > [!NOTE]  
    >  您可能會在一些情況下想要混合 EventStream 類型。 比方說，管線處理，您可能想要擷取 BAM 中的特定資料不論是否在管線正在回復交易。 特別是，您可能想要擷取資料的相關失敗的訊息數目或管線處理期間發生多少重試次數。 若要在這種情況下擷取資料，您應該使用 BES。  
  
-   如果您的應用程式要在已安裝 BizTalk Server 的電腦上執行，請使用 MES 和 OES (這些 API 只能從 BizTalk 應用程式使用)。  
  
    > [!NOTE]  
    >  OES 相當於 MES，但它適用於 BizTalk 協調流程。  
  
-   如果您想要與管線交易同步的 BAM 事件持續性，您應該使用訊息事件資料流 (MES)。  
  
 所有非同步 EventStreams （BES、 MES 和 OES） 先將資料保存到 BizTalk MessageBox 資料庫。 然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。  
  
 如需有關 BAM 的 EventStream Api 的詳細資訊，請參閱[EventStream 類別](http://go.microsoft.com/fwlink/?LinkId=158046)(http://go.microsoft.com/fwlink/?LinkId=158046) 中的 BizTalk Server 文件。  
  
## <a name="bam-performance-counters"></a>BAM 效能計數器  
 如需 BAM 的效能計數器的詳細清單，請參閱[BAM 效能計數器](http://go.microsoft.com/fwlink/?LinkId=158048)(http://go.microsoft.com/fwlink/?LinkId=158048) 中的 BizTalk Server 文件。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 效能最佳化](../technical-guides/optimizing-biztalk-server-performance.md)