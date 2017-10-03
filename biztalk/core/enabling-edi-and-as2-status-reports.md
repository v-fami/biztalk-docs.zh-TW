---
title: "啟用 EDI 和 AS2 狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa40fbad-51ad-40e0-9fe3-68e54beb11a5
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cef3d25040c253badd0f517326cc7830b6962df8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-edi-and-as2-status-reports"></a>啟用 EDI 和 AS2 狀態報告
本主題描述如何設定 EDI 和 AS2 狀態報告中的**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 狀態報告追蹤資料會根據以下程序所選的儲存區屬性，儲存於 BizTalk 追蹤資料庫 (BizTalkDTADb)。 您可以設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來啟用每個協議的狀態報告。 您應該根據儲存的資料量，例行地封存使用中存放區的資料，最後如果適用要從封存存放區清除這些資料。 如需管理 BizTalkDTADb 資料庫的詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。  
  
 您可以用三種方式啟用狀態報告：  
  
-   針對解析為協議的輸入或輸出 EDI 交換，啟用狀態報告。  
  
-   針對 EDI 後援協議屬性啟用狀態報告，以便針對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷其適用協議的 EDI 交換啟動狀態報告。  
  
-   啟用 AS2 訊息的狀態報告  
  
## <a name="prerequisites"></a>必要條件  
 您必須以成員的登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組或 BizTalk Server B2B 操作員 」 群組。  
  
### <a name="to-enable-edi-status-reports-for-an-agreement"></a>若要啟用協議的 EDI 狀態報告  
  
1.  在**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理**主控台中，按一下 **合作對象**節點下的[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和**BizTalk 群組**節點。  
  
2.  在**合作對象與商務設定檔** 窗格中，按一下您要啟用狀態報告的 X12 或 EDIFACT 協議的合作對象。  
  
3.  在**協議**區段中，以滑鼠右鍵按一下您要啟用狀態報告，然後按一下協的議**屬性**。  
  
4.  在**一般**索引標籤的**一般主控件設定**區段中，按一下**開啟報告**。  
  
    > [!NOTE]
    >  這個步驟會讓訊息項目輸入到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中的狀態報告 UI。  
  
5.  選取**儲存交易集/內容 reporting** ，將交易集儲存在追蹤 (BizTalkDTADb) 資料庫的 EDI 資料表中。  
  
    > [!NOTE]
    >  如果您在啟動批次處理協調流程的執行個體時啟用交易集的儲存區，就不會為所建立的批次儲存交易集。 然而，如果您在啟動批次處理協調流程的執行個體時停用交易集的儲存區，則批次處理過程中便會停用該儲存區。  
  
6.  按一下 **[確定]**。  
  
7.  重新啟動 BizTalk 服務 (在 [電腦管理] 對話方塊中)。 如果正在方案中使用 AS2EdiReceive 管線或 AS2EdiSend 管線，重新啟動 IIS Admin service (使用*iisreset*命令)，以及。  
  
    > [!NOTE]
    >  BizTalk 服務在 EDI 狀態報告啟動或停用之後必須重新啟動，讓變更生效。 如果解決方案中使用的是 AS2EdiReceive 或 AS2EdiSend 管線，則 BizTalk 服務和 IIS 服務都必須重新啟動，變更才會生效。 請注意，啟用 AS2 狀態報告時則不需要。  
  
### <a name="to-enable-edi-status-reports-for-fallback-agreements"></a>若要啟用後援協議的 EDI 狀態報告  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**節點，以滑鼠右鍵按一下**合作對象**，然後選取**X12 後援設定**或**EDIFACT 後援設定**。  
  
    > [!NOTE]
    >  在後援協議中設定狀態報告時，只有在尚未決定訊息的協議時組態才適用。  
  
2.  在**後援設定一般頁面**索引標籤上，按一下 **啟動 EDI 報告**。  
  
    > [!NOTE]
    >  這個步驟會讓訊息項目輸入到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中的狀態報告 UI。  
  
3.  選取**儲存交易集/內容 reporting** ，將交易集儲存在追蹤 (BizTalkDTADb) 資料庫的 EDI 資料表中。  
  
    > [!NOTE]
    >  **對於 EDIFACT 編碼訊息**： 如果您選取這個屬性，則您也必須在 [EDI 全域屬性] 對話方塊的 [UNB 區段定義] 頁面中選取 UNB3.2 欄位 （辨識符號） 的值。 根據預設，並未設定此屬性，以及交換將遭擱置，如果**儲存交易集/內容 reporting**已選取，但並未為 UNB3.2 選取值。  
  
4.  按一下 **[確定]**。  
  
### <a name="to-enable-as2-status-reports"></a>若要啟用 AS2 狀態報告  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和**BizTalk 群組**節點，按一下**合作對象**節點。  
  
2.  在**合作對象與商務設定檔** 窗格中，按一下您要啟用狀態報告的 X12 或 EDIFACT 協議的合作對象。  
  
3.  在**協議**區段中，以滑鼠右鍵按一下您要啟用狀態報告，然後按一下協的議**屬性**。  
  
4.  在**一般主控件設定**區段中，按一下**開啟報告**。  
  
    > [!NOTE]
    >  這個步驟會讓訊息項目輸入到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中的狀態報告 UI。  
  
5.  在單向協議索引標籤的**協議屬性**對話方塊中，按一下 **接收者訊息追蹤 (NRR)**頁面。  
  
6.  在**接收者訊息追蹤 (NRR)**頁面上，按一下**為輸入的編碼 AS2 訊息啟用 NRR**以啟用內送訊息的電傳格式顯示。  
  
    > [!NOTE]
    >  當您以滑鼠右鍵按一下 [AS2 訊息和相互關聯的 MDN 狀態] 頁面中的訊息，然後按一下時，將會顯示訊息的電傳格式**訊息電傳格式**。  
  
    > [!NOTE]
    >  **開啟報告**必須選取屬性，您才能啟用不可否認性資料庫中的任何資料的儲存體。 如果您選取這個屬性或其他啟用不可否認性資料庫中之儲存區的屬性，就會顯示快顯提示您啟動 AS2 報告。 如果您按一下**是**，將會為您啟動 AS2 報告。  
  
7.  在**接收者訊息追蹤 (NRR)**頁面上，按一下**為輸入的解碼 AS2 訊息啟用 NRR**以啟用內送訊息的解碼格式顯示。  
  
8.  在**接收者訊息追蹤 (NRR)**頁面上，按一下**為輸出的 MDN 啟用 NRR**以啟用內送訊息 MDN 回應的顯示。  
  
9. 在單向協議索引標籤的**協議屬性**對話方塊中，按一下 **寄件者訊息追蹤 (NRR)**頁面。  
  
10. 在**寄件者訊息追蹤 (NRR)**頁面上，按一下**為輸出的編碼 AS2 訊息啟用 NRR**以啟用外寄訊息的電傳格式顯示。  
  
11. 在**寄件者訊息追蹤 (NRR)**頁面上，按一下**為輸出的解碼 AS2 訊息啟用 NRR**以啟用外寄訊息的解碼格式顯示。  
  
12. 在**寄件者訊息追蹤 (NRR)**頁面上，按一下**為輸入的 MDN 啟用 NRR**以啟用外寄訊息 MDN 回應的顯示。  
  
13. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md)   
 [設定 EDI 和 AS2 狀態報告](../core/configuring-an-edi-and-as2-status-report.md)   
 [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)   