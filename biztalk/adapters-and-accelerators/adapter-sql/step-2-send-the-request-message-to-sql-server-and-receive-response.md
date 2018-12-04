---
title: 步驟 2： 將要求訊息傳送到 SQL Server，並接收回應 |Microsoft Docs
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
ms.openlocfilehash: 55c2c6095c9e0c7bf88ec22a296ccc6483c62472
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826310"
---
# <a name="step-2-send-the-request-message-to-sql-server-and-receive-response"></a>步驟 2： 將要求訊息傳送到 SQL Server，並接收回應
![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您可以傳送要執行的要求訊息**UPDATE_EMPLOYEE**預存程序，並接收回應。  
  
## <a name="prerequisites"></a>先決條件  
 您必須先完成[步驟 1： 為 UPDATE_EMPLOYEE 預存程序建立要求訊息](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)。  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a>若要傳送的要求訊息並接收回應  
  
1.  在現有的協調流程，底下**插入**區塊**決定**圖形中新增**訊息指派**圖形。 從 [工具箱] 拖曳**訊息指派**空間的圖形表示。  
  
    > [!NOTE]
    >  當您卸除**訊息指派**圖形拖曳至設計介面，而協調流程設計師 」 可讓您建立封閉式**建構訊息**為您的圖形。  
  
2.  在設計介面中，以滑鼠右鍵按一下**constructmessage_1**圖形，，然後按一下**屬性 視窗**。  
  
3.  在 [**屬性**] 窗格 **[constructmessage_1]** 圖形中，指定下列值。  
  
    |將此屬性設定|此值|  
    |-----------------------|-------------------|  
    |**建構的訊息**|UpdateEmployee|  
    |**名稱**|ConstructRequestMessage|  
  
4.  按兩下**MessageAssignment**圖形以開啟**BizTalk 運算式編輯器**。  
  
5.  在  **BizTalk 運算式編輯器**，新增下列：  
  
    ```  
    UpdateEmployee = UpdateEmployeeMessageCreator.UpdateEmployeeMessageCreator.XMLMessageCreator();  
    UpdateEmployee(WCF.Action) = "TypedProcedure/dbo/UPDATE_EMPLOYEE";  
    ```  
  
     在這裡， **UpdateEmployee**是您在中建立的訊息[步驟 2： 建立 BizTalk 協調流程的訊息](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)傳送要求訊息**UPDATE_EMPLOYEE**儲存程序。 在  **MessageAssignment**圖形，您可以叫用**UpdateEmployeeMessageCreator**類別來建立要求訊息。 此外，您可以設定要求訊息的 WCF 動作。  
  
6.  在協調流程中加入下列圖形**訊息指派**圖形。  
  
    |形狀圖|圖形類型|屬性|  
    |-----------|----------------|----------------|  
    |SendUpdateMessage|Send|-設定**訊息**到*UpdateEmployee*<br />-設定**名稱**到*SendUpdateMessage*|  
    |ReceiveUpdateResponse|Receive|-設定**啟用**到*False*<br />-設定**訊息**到*UpdateEmployeeResponse*<br />-設定**名稱**到*ReceiveUpdateResponse*|  
  
7.  新增要求-回應傳送埠至協調流程。 您將使用此連接埠，以將要求訊息傳送到 SQL Server，並接收回應。 設定連接埠的下列屬性。  
  
    |將此屬性設定|此值|  
    |-----------------------|-------------------|  
    |**通訊方向**|傳送-接收|  
    |**通訊模式**|要求-回應|  
    |**識別碼**|SQLOutboundPort|  
  
     此外，變更 Operation_1，若要從 作業名稱**UpdateEmp**。  
  
8.  連接到動作圖形的連接埠。 在協調流程設計師 」 設計介面上，拖曳的綠色箭頭圖形控點的 「 動作 」 圖形的連接埠的對應綠色控點。  
  
    > [!NOTE]
    >  在此步驟中，您使用拖放方法將連接埠連接到動作圖形。 代替使用動作圖形的作業屬性將動作圖形連接到連接埠。  
  
     請連線的連接埠和動作圖形，如下所示：  
  
    -   連接**SendUpdateMessage**到動作圖形**要求**控點**SQLOutboundPort**。  
  
    -   連接**ReceiveUpdateResponse**到動作圖形**回應**控點**SQLOutboundPort**。  
  
9. 下圖顯示進行中協調流程。  
  
     ![更新協調流程傳送更新訊息](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您必須更新協調流程藉由新增**MessageAssignment**圖形**傳送**並**接收**圖形和連接埠。 連接圖形和連接埠來傳送要求訊息給執行 UPDATE_EMPLOYEE 要求訊息，並接收回應。  
  
## <a name="next-steps"></a>後續步驟  
 在下一個步驟中，您可以新增上叫用插入作業的協調流程圖形**為 Purchase_Order**資料表中所述[第 4 課： 執行插入作業在訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 建立要求訊息為 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)   
 [第 3 課：執行預存程序以選取新增的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)
