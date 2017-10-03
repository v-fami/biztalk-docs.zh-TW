---
title: "顯示 EDI 或 AS2 狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60968c3d-6329-411f-9f10-1dd4a6cc9d79
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0564a5c5d904a217ac406befebd3d7c742dc00c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="displaying-an-edi-or-as2-status-report"></a>顯示 EDI 或 AS2 狀態報告
啟用 EDI 和 AS2 狀態報告時，您可以存取下列狀態報告：  
  
|報告類型|上層狀態報告|下層狀態報告|  
|--------------------|---------------------------------|--------------------------------|  
|EDI|EDI 交換和相互關聯的 ACK 狀態|-交換狀態和通知詳細資料<br /><br /> 交易集詳細資料<br /><br /> EDI 訊息內容|  
|EDI|批次狀態|-|  
|EDI|交換彙總報告|-|  
|EDI|交易集彙總報告|-|  
|AS2|AS2 訊息和相互關聯的 MDN 狀態|AS2 訊息內容|  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
-   您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員群組的成員身分登入，才能自訂任何狀態報告。  
  
-   如果以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組的成員身分登入，則只能顯示唯讀狀態報告。  
  
## <a name="display-an-edi-or-as2-status-report"></a>顯示 EDI 或 AS2 狀態報告  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下  **BizTalk 群組**節點。  
  
2.  在**群組中樞** 索引標籤**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，移至頁面底部。  
  
3.  若要顯示**EDI 交換和相互關聯的 ACK 狀態**報告，請執行，如下所示：  
  
    1.  按一下**EDI 交換和相互關聯的 ACK 狀態**中**EDI 狀態報告**區域**群組中樞** 索引標籤。  
  
    2.  若要顯示某個交換及其相互關聯之通知的詳細資訊，請以滑鼠右鍵按一下查詢結果中的項目**EDI 交換和相互關聯的 ACK 狀態**報表，然後再按一下**交換狀態和通知詳細資料**。  
  
    3.  若要顯示交易集的詳細資訊，請關閉 交換狀態和通知詳細資料報告，回到**EDI 交換和相互關聯的 ACK 狀態**詳細資料報表。 以滑鼠右鍵按一下查詢結果中的項目，然後按一下 **交易集詳細資料**。  
  
    4.  若要顯示的標頭及裝載交易集的詳細資訊，請以滑鼠右鍵按一下中的項目**交易集詳細資料**報表，然後再按一下**檢視交易集內容**。  
  
    5.  若要顯示包含交易集之交換的資料，以滑鼠右鍵按一下中的項目**交易集詳細資料**報表，然後再按一下**交換/通知狀態**。 包含交易集的交換將會反白顯示在 [交換/通知狀態] 報告中。  
  
4.  若要顯示**批次狀態**報告，請執行，如下所示：  
  
    1.  按一下**批次狀態**中**EDI 狀態報告**區域**群組中樞** 索引標籤。  
  
    2.  若要顯示完成的批次中的批次項目相關聯**批次狀態**報告，以滑鼠右鍵按一下項目，然後按一下**已完成批次**。  
  
    3.  若要顯示已完成的批次交換的資料，以滑鼠右鍵按一下中的交換**已完成批次**報表，然後再按一下**交換/通知狀態**。 批次交換的項目將會反白顯示在 [交換/通知狀態] 報告中。  
  
5.  若要顯示**交換彙總報告**，繼續進行，如下所示：  
  
    -   按一下**交換彙總報告**中**EDI 狀態報告**區域**群組中樞** 索引標籤。  
  
6.  若要顯示**交易集彙總報告**，繼續進行，如下所示：  
  
    -   按一下**交易集彙總報告**中**EDI 狀態報告**區域**群組中樞** 索引標籤。  
  
7.  若要顯示**AS2 訊息和相互關聯的 MDN 狀態**報告，請執行，如下所示：  
  
    1.  按一下**AS2 訊息和相互關聯的 MDN 狀態**中**EDIINT 狀態報告**區域**群組中樞** 索引標籤。  
  
    2.  若要顯示 AS2 訊息中的 EDI 交換的狀態，以滑鼠右鍵按一下中的項目**AS2 訊息和相互關聯的 MDN 狀態**報表，然後再按一下**交換/通知狀態**。  
  
        > [!NOTE]
        >  如需有關 EDI 和 AS2 狀態如何相關的詳細資訊，請參閱 「 相互關聯的 AS2 訊息與其 EDI 內容 」 一節[AS2 訊息和相互關聯的 MDN 狀態報告](../core/as2-message-and-correlated-mdn-status-report.md)。  
  
    3.  若要以電傳格式顯示 AS2 訊息，以滑鼠右鍵按一下 AS2/MDN 狀態 報告中中的項目，然後按一下 **訊息電傳格式**。  
  
    4.  若要以解碼格式顯示 AS2 訊息，以滑鼠右鍵按一下 AS2/MDN 狀態 報告中中的項目，然後按一下 **訊息解碼格式**。  
  
    5.  若要顯示 MDN 訊息，以滑鼠右鍵按一下 AS2/MDN 狀態 報告中中的項目，然後按一下  **Mdn 訊息**。  
  
## <a name="see-also"></a>另請參閱  
 [監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md)   
 [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)   
 [啟用 EDI 和 AS2 狀態報告](../core/enabling-edi-and-as2-status-reports.md)   
 [設定 EDI 和 AS2 狀態報告](../core/configuring-an-edi-and-as2-status-report.md)