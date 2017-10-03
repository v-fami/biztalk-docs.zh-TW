---
title: "交易集詳細資料狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d81367c7-c74e-42cb-b856-748962b727ec
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6da167ea995fa05d8e35807d8cf26f23b5444a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-details-status-report"></a>交易集詳細資料狀態報告
這個報告會針對選自「交換/通知狀態」報告其中之特定 EDI 交換的交易集，顯示詳細資料。 若要顯示此狀態報告，以滑鼠右鍵按一下 [交換/通知狀態] 報告中，查詢結果] 窗格中所列的交換，然後按一下 [**交易集詳細資料**。  
  
 此報表是您已選取時，才可以使用**儲存交易集/內容 reporting**相關合作對象 [EDI 屬性] 對話方塊的 [一般] 頁面中的屬性。  
  
## <a name="fields-in-the-status-report"></a>狀態報告中的欄位  
 「交易集詳細資料狀態報告」會針對已接收或已傳送交換的交易集顯示下列資訊：  
  
-   交易集識別碼  
  
-   文件類型  
  
-   傳送者合作對象別名  
  
-   應用程式傳送者  
  
-   接收者合作對象別名  
  
-   應用程式接收者  
  
-   方向  
  
-   交換控制編號  
  
-   群組控制編號  
  
-   交易集合控制編號  
  
-   交易集合狀態  
  
-   交換日期時間 （依預設不顯示）  
  
    > [!NOTE]
    >  接收文件，如果交換中所指定的日期是 YYMMDD 格式和 YY 是大於或等於 75，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將年份顯示 19YY。 如果日期為少於 75 台，它會顯示為 20YY。  
    >   
    >  例如，如果您收到包含值 991113 中 isa09-交換，交換日期時間會列入報表中為 11/13/1999年。  
  
-   處理日期/時間 （依預設不顯示）  
  
-   群組日期/時間 （依預設不顯示）  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a>狀態報告之查詢運算式中的欄位  
 您可以自訂 [EDI 交換和相互關聯的 ACK 狀態] 報告，方法是變更查詢運算式中負責決定所顯示之資料的欄位。 可用的欄位如下：  
  
|||||  
|-|-|-|-|  
|查詢運算式欄位|可能的運算子|可能的值|預設已包含？|  
|搜尋|等於|交易集詳細資料|是 (必要)|  
|交換日期時間|小於或等於<br /><br /> 大於或等於|特定日期時間<br /><br /> 今天<br /><br /> 今日 - 1|是<br /><br /> 附註： 可以包含超過一次在查詢運算式中。|  
|接收者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱|是|  
|傳送者合作對象名稱|等於|全部 (預設)<br /><br /> 特定合作對象名稱|是|  
|方向|等於|全部 (預設)<br /><br /> Receive<br /><br /> Send|是|  
|控制項 ID|等於|交換控制識別碼|是|  
|交易集合相互關聯識別碼|等於|相互關聯識別碼|是|  
|相符記錄上限|等於|整數 (預設為 50)|是|  
|狀態|等於<br /><br /> 不等於|已接受<br /><br /> 已接受，發生錯誤<br /><br /> 已傳送<br /><br /> 全部<br /><br /> 預期通知<br /><br /> 未預期通知<br /><br /> 已拒絕|否|  
|交易集識別碼|等於|交易集識別碼|否|  
  
## <a name="additional-reports-displayed-from-this-report"></a>根據這份報告顯示的其他報告  
 您可針對 [交易集詳細資料] 報告所顯示的交易集，顯示下列其他狀態報告：  
  
-   訊息內容狀態報告： 您可以用滑鼠右鍵按一下詳細資料報告中的交易集，然後按一下 [檢視交易集內容] 來顯示報告。 如需詳細資訊，請參閱[EDI 訊息內容狀態報告](../core/edi-message-content-status-report.md)。  
  
-   交換/通知狀態報告： 此報表會使用相同的使用者介面[EDI 交換和相互關聯的 ACK 狀態報告](../core/edi-interchange-and-correlated-ack-status-report.md)顯示多個交換。 兩者間的差異，在於這份報告資料只涵蓋包含這個交易集的交換。  
  
