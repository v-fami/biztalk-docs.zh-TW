---
title: 設定 EDI 和 AS2 狀態報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c7fa76d-0d03-4b74-9a3a-60f4bd0534ff
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051a03b735f3714910b415d5418ff84089c57940
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233614"
---
# <a name="configuration-of-edi-and-as2-status-reporting"></a>EDI 和 AS2 狀態報告的組態
本主題說明如何啟用 EDI 和 AS2 狀態報告，以及 EDI、批次處理和 AS2 狀態報告之狀態報告篩選器和顯示資料行的組態。  
  
## <a name="enabling-status-reporting"></a>啟用狀態報告  
 EDI 狀態報告才會提供在伺服器上如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 BAM 子系統與安裝該伺服器上。 如果未安裝 BAM 基礎結構，無法啟用 EDI/AS2 狀態報告。 伺服器也必須是成員的 EDI 處理[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]分組，讓它擁有存取權 EDI 狀態報告資料存放區。  
  
 會為狀態報告 UI 中的合作對象的交換輸入 EDI 訊息項目，如果**開啟報告**中選取屬性**一般屬性**頁面**一般**索引標籤中**協議屬性** 對話方塊。 如果合作對象傳送或接收的交換不會決定，EDI 訊息項目將會輸入這些交換才**啟動 EDI 報告**X12 和 EDIFACT 的後援協議中選取屬性。 這個條件適用於 EDI 交換和相互關聯的 ACK 狀態報告。 批次狀態報告才會啟用在判斷協議和**開啟報告**中選取屬性**一般屬性**頁面**一般**索引標籤中**協議屬性** 對話方塊。  
  
 將追蹤資料庫中儲存的交易集，如果**儲存報告的訊息內容**中選取屬性**一般屬性**頁面**一般**索引標籤中**協議屬性**對話方塊或**儲存交易集/內容 reporting**後援協議屬性中設定屬性。 您必須選取這個屬性，才能使用交易集詳細資料與訊息內容狀態報告。  
  
 會在狀態報告 UI 中輸入 AS2 訊息項目，如果**開啟報告**中選取屬性**一般屬性**頁面**一般**中的索引標籤**協議屬性** 對話方塊。 若要將 AS2 訊息或 mdn 儲存在不可否認性資料庫中，您必須選取適當的屬性中**寄件者不可否認性**或**接收者不可否認性**頁面的單向 AS2 協議索引標籤中**協議屬性** 對話方塊。 這些屬性會啟用 AS2 訊息和相互關聯的 MDN 狀態報告。  
  
 將可使用 可靠傳訊狀態 報告如果**重新傳送 AS2 訊息，若未收到 MDN**上已啟用屬性**傳送者 MDN 設定**的單向AS2協議索引標籤頁面**協議屬性** 對話方塊。  
  
 如需有關如何啟用狀態報告的詳細資訊，請參閱[啟用 EDI 和 AS2 狀態報告](../core/enabling-edi-and-as2-status-reports.md)。  
  
## <a name="status-report-filters-and-display-columns"></a>狀態報告篩選器和顯示資料行  
 EDI 和 AS2 狀態報告可讓您自訂狀態報告所儲存的資料範圍。 請在**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 在顯示任何狀態報告的狀態報告窗格之後，您就可以選取想要在報告中呈現的資料範圍。 如果要這樣做，請選取要包含在狀態報告查詢運算式中的篩選值。  
  
 您也可以自訂狀態報告中顯示的資料型別。  
  
> [!NOTE]
>  一旦啟用狀態報告後，所有的狀態都會儲存在儲存區中。 透過自訂查詢運算式或狀態資料行，您就可以定義顯示的已儲存資料。  
  
 如需詳細資訊，請參閱[設定 EDI 和 AS2 狀態報告](../core/configuring-an-edi-and-as2-status-report.md)。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)   
 [EDI 交換和相互關聯的 ACK 狀態報表](../core/edi-interchange-and-correlated-ack-status-report.md)   
 [批次狀態報告](../core/batch-status-report.md)   
 [交換彙總報告](../core/interchange-aggregation-report.md)   
 [交易集彙總報告](../core/transaction-set-aggregation-report.md)   
 [AS2 訊息和相互關聯的 MDN 狀態報告](../core/as2-message-and-correlated-mdn-status-report.md)