---
title: "設定寄件者訊息追蹤 (NRR) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6ca2709-ac4b-48c0-82f8-8a43971a86cb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1785a5502bc1adb9cc8b9aa7f85b6a4473d21c5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-sender-message-tracking-nrr"></a>設定寄件者訊息追蹤 (NRR)
在此頁面的設定中，您可以指定是否將輸出訊息和其通知 (MDN) 儲存在不可否認性的資料庫中。 如需詳細資訊，請參閱[BizTalk Server 中的 AS2 處理](../core/as2-processing-in-biztalk-server.md)。  
  
 若要將訊息儲存在不可否認性的資料庫中，合作對象必須在 AS2 協議屬性中啟用 NRR (Non-repudiation of receipt，接收不可否認性)。 NRR 可確保寄件方已確認訊息收件者已簽署回條。 概念上而言，NRR 對於訊息寄件者是一個不可否認的證明，代表訊息已完整無缺地送達目的地。 只有當原始訊息和回條都完成數位簽署時，才會建立 NRR。  
  
> [!IMPORTANT]
>  所有屬性會停都用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-message-tracking-for-outbound-as2-messages-and-inbound-mdn"></a>若要為輸出 AS2 訊息和輸入 MDN 設定訊息追蹤  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**本機主機設定**區段中，按一下**寄件者訊息追蹤 (NRR)**。  
  
    > [!NOTE]
    >  為了確保接收不可否認性，您必須建立訊息的真實性和完整性。 建議做法是對訊息使用數位簽章。 如此一來，如果您選取任何要將訊息儲存在不可否認性資料庫的屬性，您應該簽署訊息以選取**訊息應該簽署**屬性**驗證**頁面。  
  
3.  選取**為輸出的編碼 AS2 訊息啟用 NRR**輸出的編碼的 AS2 訊息儲存在不可否認性資料庫中。  
  
4.  選取**為輸出的解碼 AS2 訊息啟用 NRR**輸出的解碼的 AS2 訊息儲存在不可否認性資料庫中。  
  
5.  選取**為輸入的 MDN 啟用 NRR** ，將輸入的 MDN 儲存在不可否認性資料庫中。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定本機主機設定 (AS2)](../core/configuring-local-host-settings-as2.md)