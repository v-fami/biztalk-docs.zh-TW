---
title: "儲存的批次狀態報告資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d55aa0e1-095f-434e-8530-f1a946ad4430
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db9831aafce56845fe7b75e91f5369a8860d8996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-stored-for-batching-status-reports"></a>批次狀態報告的儲存資料
當**開啟報告**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會儲存每個批次的執行個體的狀態。 這個屬性是在用於**一般屬性**頁面**一般**索引標籤中**協議屬性** 對話方塊。 這個狀態可以是下列任何一項：  
  
-   **定義**： 批次的執行個體的設定。 批次啟動開始日期時間大於目前日期時間。 所有批次參數都已定義，但是批次未執行 (不接受文件)。  
  
-   **Active**： 批次的執行個體已啟動且正在彙總交易集。 您可以檢視已接受/已拒絕的交易集數目。  
  
-   **釋放**： 批次符合釋放準則和已釋放至 MessageBox，但尚未由傳送管線，釋出或處理任何訊息之前，先停止批次。  
  
-   **完成**: 批次已由 EdiSend 管線傳送。  
  
 如果批次已由 EdiSend 管線傳送，您可以將 UI 中的批次記錄與所傳送 Edi 交換的記錄相互關聯，然後檢視交易集詳細資料。  
  
> [!NOTE]
>  批次組態可能有多個「已完成」狀態的批次執行個體。  
  
 **與批次的交換相互關聯**  
  
 BusinessMessageJournal BAM 活動可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將包含交易集的已接收 EDI 交換，與包含同一個交易集的外寄批次交換產生相互關聯。 如需如何實作及使用此相互關聯資訊，請參閱[相互關聯的內送交易集與外寄批次](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md)。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 和 AS2 狀態報告的儲存資料](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [EDI 狀態報告的儲存資料](../core/data-stored-for-edi-status-reports.md)   
 [AS2 狀態報告的儲存資料](../core/data-stored-for-as2-status-reports.md)