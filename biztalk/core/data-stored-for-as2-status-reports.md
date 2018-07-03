---
title: AS2 狀態報告的儲存的資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6aa4077-3768-436b-99b9-d203a86a7e69
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f14fc95dfba5e29089653ef02dddd1b0b366ff8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012513"
---
# <a name="data-stored-for-as2-status-reports"></a>AS2 狀態報告的儲存資料
AS2 狀態報告中有兩個層級的報告： 第一個 if**開啟報告**協議中選取屬性 (從**一般屬性**頁面**一般**索引標籤中**協議屬性**對話方塊)，而第二個如果針對協議選取不可否認性資料庫儲存體屬性。  
  
## <a name="data-stored-if-as2-reporting-is-activated"></a>啟動 AS2 報告時所儲存的資料  
 如果**開啟報告**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會保留記錄的所有已傳送或接收 AS2 訊息和 Mdn。  
  
 對於已接收的 AS2 訊息，BizTalk Server 會儲存下列資訊：  
  
- AS2 訊息的記錄。  
  
  對於已接收或傳送的 MDN 訊息 (同步或非同步)，BizTalk Server 會儲存下列資訊：  
  
- MDN 的記錄。  
  
  狀態報告 UI 會啟用 AS2 訊息記錄與適當 MDN 記錄的相互關聯。  
  
## <a name="data-stored-if-resend-as2-message-if-mdn-not-received-is-enabled"></a>已啟用若未收到 MDN 則重新傳送 AS2 訊息時所儲存的資料  
 如果**重新傳送 AS2 訊息，若未收到 MDN**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會記錄下列資訊：  
  
-   每一次嘗試重新傳送的時間  
  
-   每一次嘗試重新傳送的狀態  
  
-   每一次嘗試重新傳送的索引  
  
## <a name="data-stored-if-non-repudiation-database-storage-is-enabled"></a>啟用不可否認性的資料庫儲存時所儲存的資料  
 不可否認性的資料庫儲存是透過選取下列協議屬性加以啟用：  
  
- 為輸出的編碼 AS2 訊息啟用 NRR  
  
- 為輸出的解碼 AS2 訊息啟用 NRR  
  
- 為輸入的 MDN 啟用 NRR  
  
- 為輸入的編碼 AS2 訊息啟用 NRR  
  
- 為輸入的解碼 AS2 訊息啟用 NRR  
  
- 為輸出的 MDN 啟用 NRR  
  
  如果選取一個或多個上述屬性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會儲存下列資訊：  
  
- 任何 AS2 訊息的內容和任何 MDN (無論是否具有 AS2 標頭) 的內容。  
  
## <a name="data-stored-for-edi-over-as2"></a>透過 AS2 傳送或接收 EDI 時所儲存的資料  
 如果**開啟報告**針對 EDI 協議，以及 AS2 協議中，選取屬性，則您可以將 AS2 訊息記錄 （包含 EDI 內容） 與 EDI 訊息記錄相互關聯。  
  
 如果有啟用交易集儲存區，您就可以在狀態報告 UI 中顯示交易集詳細資料和 AS2 訊息內容詳細資料。  
  
> [!NOTE]
>  您必須使用 AS2EdiReceive 或 AS2EdiSend 管線，才能存取這些報告。  
  
## <a name="see-also"></a>另請參閱  
 [儲存 EDI 和 AS2 狀態報告的資料](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [EDI 狀態報告的儲存資料](../core/data-stored-for-edi-status-reports.md)   
 [批次狀態報告的儲存資料](../core/data-stored-for-batching-status-reports.md)