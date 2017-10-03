---
title: "步驟 3： 傳送要插入的記錄，並接收回應的要求訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a8a8906-7c7d-437c-9f04-345ad4ac460e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db97afa0de19e15e5005e5647279365ea6ba023b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-send-the-request-message-to-insert-records-and-receive-a-response"></a>步驟 3： 傳送要插入的記錄，並接收回應的要求訊息
![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：**在此步驟中，您可以傳送要插入至記錄的要求訊息**Purchase_Order**資料表，並接收回應。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)。  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a>以傳送要求訊息並接收回應  
  
1.  在協調流程中加入下列圖形**建構訊息**圖形。  
  
    |形狀圖|圖形類型|屬性|  
    |-----------|----------------|----------------|  
    |SendInsertMessage|Send|-設定**訊息**至*InsertPO*<br />-設定**名稱**至*SendInsertMessage*|  
    |ReceiveInsertResponse|Receive|-設定**啟動**至*False*<br />-設定**訊息**至*InsertPOResponse*<br />-設定**名稱**至*ReceiveInsertResponse*|  
    |SaveInsertResponse|Send|-設定**訊息**至*InsertPOResponse*<br />-設定**名稱**至*SaveInsertResponse*|  
  
2.  修改**SQLOutboundPort**您在建立[步驟 2： 將要求訊息傳送至 SQL Server 和接收回應](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)。  
  
    1.  以滑鼠右鍵按一下協調流程設計師 」 中的連接埠，然後按一下**新作業**。 若要加入新的作業，連接埠圖形變更**Operation_1**。  
  
    2.  按一下**Operation_1** 屬性 視窗中變更 識別項的值**InsertPO**。  
  
3.  新增單向傳送埠至協調流程。 您將使用此連接埠來傳送插入作業的回應訊息。 設定下列屬性的連接埠。  
  
    |將此屬性設定|此值|  
    |-----------------------|-------------------|  
    |**通訊方向**|Send|  
    |**通訊模式**|單向|  
    |**識別碼**|SaveResponsePort|  
  
     此外，從 Operation_1，若要變更的作業名稱**InsertPO**。  
  
4.  連接到動作圖形的連接埠。 在 協調流程設計工具的設計介面上，拖曳動作圖形的連接埠對應綠色控點的綠色箭頭圖形控。  
  
    > [!NOTE]
    >  在此步驟中，您使用拖放方法將連接埠連接到動作圖形。 代替使用動作圖形的作業屬性將動作圖形連接到連接埠。  
  
     連接埠和動作圖形連接，如下所示：  
  
    -   連接**SendInsertMessage**至動作圖形**要求**控點**InsertPO**作業**SQLOutboundPort**。  
  
    -   連接**ReceiveInsertResponse**至動作圖形**回應**控點**InsertPO**作業**SQLOutboundPort**。  
  
    -   連接**SaveInsertResponse**至動作圖形**要求**控點**SaveResponsePort**。  
  
5.  下圖顯示進行中協調流程。  
  
     ![完成協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-09-comp-orch.gif "sql_adap_tut_09_comp_orch")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 傳送要求來插入記錄，到**Purchase_Order**資料表，並接收回應。  
  
## <a name="next-steps"></a>後續步驟  
 中所述，建置專案時，[步驟 4： 建置專案](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)   
 [步驟 4： 建置專案](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)   
 [第 4 課： 執行插入作業的採購訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)