---
title: "AS2 訊息和相互關聯的 MDN 狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48ed0ee3-c844-4cb9-a84d-32b719ab8fab
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ce4aed138f4e32e87cb1d428050999cc2b764a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-message-and-correlated-mdn-status-report"></a>AS2 訊息和相互關聯的 MDN 狀態報告
此報告會顯示 AS2 傳送和接收管線處理的所有 AS2 訊息，以及與這些交換相互關聯的 MDN。  
  
## <a name="fields-in-the-status-report"></a>狀態報告中的欄位  
 「AS2 訊息和相互關聯的通知狀態報告」會針對已接收或已傳送的交換及其相互關聯的通知，顯示下列資訊：  
  
-   傳送者合作對象名稱  
  
-   接收者合作對象名稱  
  
-   AS2 來源  
  
-   AS2 目標  
  
-   AS2 訊息識別碼  
  
-   AS2 訊息日期時間  
  
-   接收日期時間  
  
-   合作對象角色  
  
-   MDN 狀態  
  
-   加密狀態  
  
-   簽章狀態  
  
-   Edi 交換狀態  
  
-   是重複的 AS2 訊息嗎  
  
-   若要檢查有重複的天數  
  
-   檔名  
  
-   啟用可信賴傳訊  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>狀態報告之查詢運算式中的欄位  
 您可以自訂「AS2 訊息和相互關聯的通知狀態報告」，藉由變更查詢運算式中的欄位，決定要顯示的資料。 可用的欄位如下：  
  
|||||  
|-|-|-|-|  
|查詢運算式欄位|可能的運算子|可能的值|預設已包含？|  
|搜尋|等於|AS2/MDN 狀態|是 (必要)|  
|訊息狀態|等於<br /><br /> 不等於|全部<br /><br /> 認可-處理<br /><br /> 認可-失敗<br /><br /> 已處理-暫止的 MDN<br /><br /> 已處理-未預期 MDN<br /><br /> 尚未認可 – 重新傳送嘗試超過<br /><br /> 尚未認可 – 重新傳送的時間長度超過|是|  
|AS2 訊息日期時間|小於或等於<br /><br /> 大於或等於|特定日期時間<br /><br /> 今天<br /><br /> 今日 - 1|是<br /><br /> 附註： 可以包含超過一次在查詢運算式中。|  
|相符記錄上限|等於|整數 (預設為 50)|是|  
|AS2 訊息識別碼|等於|全部<br /><br /> 特定 AS2 訊息識別碼|否|  
|方向|等於|全部 (預設)<br /><br /> Receive<br /><br /> Send|否|  
|接收者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱|否|  
|傳送者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱|否|  
  
## <a name="additional-as2-message-and-correlated-mdn-status-reports"></a>其他 AS2 訊息和相互關聯的 MDN 狀態報告  
 如果您以滑鼠右鍵按一下 [AS2 訊息和相互關聯的 MDN 狀態] 報告中所列的 AS2 訊息，可以顯示下列其中一個詳細狀態報告：  
  
|狀態報告|顯示的狀態|  
|-------------------|----------------------|  
|交換/通知狀態|AS2 訊息之 EDI 內容的狀態|  
|重新傳送狀態詳細資料|重新傳送訊息的狀態|  
|訊息電傳格式|AS2 訊息的電傳格式|  
|訊息解碼|AS2 訊息的解碼格式|  
|MDN 訊息|AS2 訊息相互關聯的 MDN 訊息|  
  
 每個最後三個訊息的格式是相同的。 如需詳細資訊，請參閱[AS2 訊息內容狀態報告](../core/as2-message-content-status-reports.md)。  
  
## <a name="correlate-an-as2-message-with-its-edi-payload"></a>AS2 訊息與其 EDI 內容相互關聯  
 AS2 和 EDI 狀態報告，可讓您將相互關聯的 AS2 訊息與其 EDI 內容的狀態項目。 如果您同時啟用 AS2 和 EDI 狀態報告，會在 AS2 狀態報告中建立 AS2 訊息的狀態項目，並在 EDI 狀態報告中建立該 AS2 訊息之 EDI 內容的狀態項目。 如果您有顯示 AS2 狀態報告，您可以以滑鼠右鍵按一下 AS2 訊息狀態項目，然後按一下 顯示 AS2 訊息的 EDI 內容狀態**交換/通知狀態**。 如果 AS2 訊息中只有一個 EDI 交換，此動作將會顯示該 EDI 交換的狀態項目。  
  
 如果 AS2 訊息包含多個 EDI 交換，而您嘗試顯示 AS2 訊息中多個 EDI 交換的狀態，則只有最後一個 EDI 交換會在 [交換/通知狀態] 報告中顯示。 此外， **EDI 交易控制編號**欄位在 [AS2/MDN 狀態] 報告中的只會顯示最後一個交換控制編號。 (交換控制編號可使 AS2 訊息與其 EDI 交換內容相互關聯)。  
  
 AS2 訊息中所有 EDI 交換的資料都會儲存在狀態報告資料庫中。 如果，您可以在 [交換/通知狀態] 報告中的 AS2 訊息中顯示的所有交換**Control ID Equals All**子句會在狀態報告查詢。 這也可能會顯示出其他不在 AS2 訊息中的交換，不過，您可以查看其他欄位 (如 [傳送者合作對象]、[接收者合作對象] 和 [交換日期時間]) 判斷哪些 EDI 交換是在某個單一的 AS2 訊息中。  
  
 **合作對象角色**欄位在 AS2 狀態報告和**方向**EDI 狀態報告中的欄位在意義上的是相反。 針對內送 AS2 訊息含有 EDI 內容，**合作對象角色**欄位 AS2 訊息會是**寄件者**，雖然**方向**欄位會是 EDI 交換**接收**。 這是因為對於從合作對象收到的內送訊息來說，該合作對象的角色就是傳送者。 與所傳送 AS2 訊息相關之合作對象的屬性，就是做為 AS2 訊息傳送者之合作對象的屬性，即如 [夥伴協議管理] 的 [AS2 屬性] 對話方塊中所定義。 因此，AS2 合作對象角色與 EDI 方向相反。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [AS2 訊息內容狀態報告](../core/as2-message-content-status-reports.md)  
  
-   [重新傳送狀態詳細資料報表](../core/resend-status-details-report.md)  
  
## <a name="see-also"></a>另請參閱  
 [AS2 訊息和相互關聯的 MDN 狀態報告](../core/as2-message-and-correlated-mdn-status-report.md)   
