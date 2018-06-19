---
title: 步驟 2： 將要求訊息傳送至 SQL Server，並接收回應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 864d2174-d54b-4383-92bf-f6808a2a904b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce820ab6a1914e44239313588eaaefeb696e61d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224798"
---
# <a name="step-2-send-the-request-message-to-sql-server-and-receive-response"></a>步驟 2： 將要求訊息傳送至 SQL Server，並接收回應
![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以傳送要執行的要求訊息**UPDATE_EMPLOYEE**預存程序，並接收回應。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)。  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a>以傳送要求訊息並接收回應  
  
1.  到現有的協調流程，在**插入**區塊**決定**圖形中新增**訊息指派**圖形。 從 [工具箱] 拖曳**訊息指派**空間的圖形表示。  
  
    > [!NOTE]
    >  當您卸除**訊息指派**圖形拖曳至設計介面，協調流程設計師 」 可讓您建立封閉式**建構訊息**圖形。  
  
2.  設計介面上，以滑鼠右鍵按一下**constructmessage_1**圖形，，然後按一下**屬性 視窗**。  
  
3.  在**屬性**窗格 **[constructmessage_1]** 圖形中，指定下列值。  
  
    |將此屬性設定|此值|  
    |-----------------------|-------------------|  
    |**建構的訊息**|UpdateEmployee|  
    |**名稱**|ConstructRequestMessage|  
  
4.  按兩下**MessageAssignment**圖形以開啟**BizTalk 運算式編輯器**。  
  
5.  在**BizTalk 運算式編輯器**，加入下列：  
  
    ```  
    UpdateEmployee = UpdateEmployeeMessageCreator.UpdateEmployeeMessageCreator.XMLMessageCreator();  
    UpdateEmployee(WCF.Action) = "TypedProcedure/dbo/UPDATE_EMPLOYEE";  
    ```  
  
     在這裡， **UpdateEmployee**是您在建立的訊息[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)傳送要求訊息**UPDATE_EMPLOYEE**儲存程序。 在**MessageAssignment**圖形，您可以叫用**UpdateEmployeeMessageCreator**類別來建立要求訊息。 此外，您可以設定要求訊息的 WCF 動作。  
  
6.  在協調流程中加入下列圖形**訊息指派**圖形。  
  
    |形狀圖|圖形類型|屬性|  
    |-----------|----------------|----------------|  
    |SendUpdateMessage|Send|-設定**訊息**至*UpdateEmployee*<br />-設定**名稱**至*SendUpdateMessage*|  
    |ReceiveUpdateResponse|Receive|-設定**啟動**至*False*<br />-設定**訊息**至*UpdateEmployeeResponse*<br />-設定**名稱**至*ReceiveUpdateResponse*|  
  
7.  新增要求-回應傳送埠至協調流程。 您將使用此連接埠以將要求訊息傳送到 SQL Server，並接收回應。 設定下列屬性的連接埠。  
  
    |將此屬性設定|此值|  
    |-----------------------|-------------------|  
    |**通訊方向**|傳送-接收|  
    |**通訊模式**|要求-回應|  
    |**識別碼**|SQLOutboundPort|  
  
     此外，從 Operation_1，若要變更的作業名稱**UpdateEmp**。  
  
8.  連接到動作圖形的連接埠。 在 協調流程設計工具的設計介面上，拖曳動作圖形的連接埠對應綠色控點的綠色箭頭圖形控。  
  
    > [!NOTE]
    >  在此步驟中，您使用拖放方法將連接埠連接到動作圖形。 代替使用動作圖形的作業屬性將動作圖形連接到連接埠。  
  
     連接埠和動作圖形連接，如下所示：  
  
    -   連接**SendUpdateMessage**至動作圖形**要求**控點**SQLOutboundPort**。  
  
    -   連接**ReceiveUpdateResponse**至動作圖形**回應**控點**SQLOutboundPort**。  
  
9. 下圖顯示進行中協調流程。  
  
     ![更新協調流程傳送更新訊息](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您必須更新協調流程藉由新增**MessageAssignment**圖形，**傳送**和**接收**圖形和連接埠。 連接圖形和連接埠來傳送要求訊息給執行 UDPATE_EMPLOYEE 要求訊息並接收回應。  
  
## <a name="next-steps"></a>後續步驟  
 在下一個步驟中，您會加入至插入作業上叫用的協調流程圖形**Purchase_Order**資料表中所述[第 4 課： 執行插入作業的採購訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)   
 [第 3 課： 執行預存程序選取 加入新的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)