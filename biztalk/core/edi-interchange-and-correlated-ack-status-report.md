---
title: "EDI 交換和相互關聯的 ACK 狀態報表 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a112cc3d-d34c-4652-a8ee-3355a31d4a03
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5f4268badf9907eb90b090abe34a8355b3ab8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-interchange-and-correlated-ack-status-report"></a>EDI 交換和相互關聯的 ACK 狀態報告
此報告會顯示 EDI 傳送和接收管線處理的所有 EDI 交換，以及與這些交換相互關聯的通知。  
  
## <a name="fields-in-the-status-report"></a>狀態報告中的欄位  
 [EDI 交換和相互關聯的 ACK 狀態] 報告會針對接收或傳送交換以及其相互關聯的通知，顯示下列資訊：  
  
-   傳送者合作對象  
  
    > [!NOTE]
    >  傳送者合作對象將會依照以下方式決定：  
    >   
    >  -   如果交換中的合作對象名稱符合合作對象之 EDI 屬性中所設定的名稱，則會顯示設定的名稱。  
    > -   如果交換中的合作對象名稱不符合任何已設定 EDI 屬性的現有合作對象，則會顯示指定交換中的合作對象名稱。  
  
-   接收者合作對象  
  
    > [!NOTE]
    >  接收者合作對象名稱將會依照以下方式決定：  
    >   
    >  -   如果交換中的合作對象名稱符合合作對象之 EDI 屬性中所設定的名稱，則會顯示設定的名稱。  
    > -   如果交換中的合作對象名稱不符合任何已設定 EDI 屬性的現有合作對象，則會顯示指定交換中的合作對象名稱。  
  
-   控制項 ID  
  
-   方向  
  
-   交換日期時間  
  
-   EDI 編碼類型  
  
-   交換狀態  
  
-   群組計數  
  
-   連接埠識別碼  
  
-   傳送者合作對象別名  
  
-   接收者合作對象別名  
  
-   交易集合相互關聯識別碼  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>狀態報告之查詢運算式中的欄位  
 您可以自訂 [EDI 交換和相互關聯的 ACK 狀態] 報告，方法是變更查詢運算式中負責決定所顯示之資料的欄位。 可用的欄位如下：  
  
|||||  
|-|-|-|-|  
|查詢運算式欄位|可能的運算子|可能的值|預設已包含？|  
|搜尋|等於|交換/通知狀態|是 (必要)|  
|狀態|等於<br /><br /> 不等於|已接受<br /><br /> 已接受，發生錯誤<br /><br /> 已傳送<br /><br /> 全部<br /><br /> 預期通知<br /><br /> 未預期通知<br /><br /> 已拒絕<br /><br /> (這些值定義如下)。|是|  
|交換日期時間|小於或等於<br /><br /> 大於或等於|特定日期時間<br /><br /> 今天<br /><br /> 今日 - 1|是<br /><br /> 附註： 可以包含超過一次在查詢運算式中。|  
|相符記錄上限|等於|整數 (預設為 50)|是|  
|控制項 ID|等於|交換控制識別碼|否|  
|方向|等於|全部 (預設)<br /><br /> Receive<br /><br /> Send|否|  
|接收者合作對象|等於|全部 (預設)<br /><br /> 特定合作對象名稱|否|  
|傳送者合作對象|等於|全部 (預設)<br /><br /> 特定合作對象名稱|否|  
  
## <a name="status-definitions"></a>狀態定義  
 EDI 狀態報告中所用的狀態值定義如下：  
  
-   已接受：有效的交換  
  
-   已接受，發生錯誤：區段中已註明錯誤  
  
-   已傳送：已成功傳送交換  
  
-   All： 顯示與任何其他值的訊息  
  
-   預期通知  
  
    > [!NOTE]
    >  如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 預期會有技術通知，則當傳送輸出訊息時，[交換狀態和通知詳細資料] 狀態報告中的 [交換狀態] 欄位將會針對此訊息設定為 [預期通知]。 會發生這個錯誤**預期 TA1**屬性設定**通知**頁面的單向協議索引標籤。已接收及驗證技術通知時，狀態就會變更為 已接受。 請注意，只有技術通知會發生這個情況，功能通知則不會。  
  
-   未預期通知  
  
-   已拒絕：交換無效，因為發生錯誤。  
  
## <a name="additional-reports-displayed-from-this-report"></a>根據這份報告顯示的其他報告  
 您可針對 [交易集詳細資料] 報告中所顯示的交易集，顯示下列其他狀態報告。 以滑鼠右鍵按一下 [EDI 交換和相互關聯的 ACK 狀態] 報告中所列的交換或通知，然後按一下適當的命令，即可存取報告：  
  
-   [交換狀態和通知詳細資料狀態報告](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [交易集詳細資料狀態報告](../core/transaction-set-details-status-report.md)  
  
## <a name="next-steps"></a>後續的步驟
  
-   [交換狀態和通知詳細資料狀態報告](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [交易集詳細資料狀態報告](../core/transaction-set-details-status-report.md)  
  
-   [EDI 訊息內容狀態報告](../core/edi-message-content-status-report.md)  
  
