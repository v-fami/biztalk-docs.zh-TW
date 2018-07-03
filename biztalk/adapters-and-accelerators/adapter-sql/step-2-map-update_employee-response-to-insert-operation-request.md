---
title: 步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應插入作業要求訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d12014a-0147-4227-88fa-0b290eff4cce
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d158e0f7eed50a40d2696712bacee65a8de946a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009015"
---
# <a name="step-2-map-the-updateemployee-response-message-to-insert-operation-request-message"></a>步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應插入作業要求訊息
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  

 **若要完成的時間：** 10 分鐘  

 **目標：** 在此步驟中，您可以建立要在執行插入作業的要求訊息**為 Purchase_Order**資料表，然後將對應的回應訊息**UPDATE_EMPLOYEE**儲存要插入作業的要求訊息的程序。 如此一來，您傳遞要插入的回應訊息中的值**為 Purchase_Order**資料表。  

## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 1： 為 Purchase_Order 資料表上的插入作業建立要求訊息](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)。  

### <a name="to-map-the-messages"></a>若要將訊息對應  

1. 到現有的協調流程，在**插入**區塊**決定**圖形，下方**ReceiveUpdateResponse**圖形中新增**訊息指派**圖形。 從 [工具箱] 拖曳**訊息指派**空間的圖形表示。  

   > [!NOTE]
   >  當您卸除**訊息指派**圖形拖曳至設計介面，而協調流程設計師 」 可讓您建立封閉式**建構訊息**為您的圖形。  

2. 在設計介面中，以滑鼠右鍵按一下**constructmessage_1**圖形，，然後按一下**屬性 視窗**。  

3. 在 [**屬性**] 窗格 **[constructmessage_1]** 圖形中，指定下列值。  


   |    將此屬性設定     |     此值      |
   |--------------------------|------------------------|
   | **建構的訊息** |        InsertPO        |
   |         **名稱**         | ConstructInsertMessage |


4. 按兩下**MessageAssignment**圖形以開啟**BizTalk 運算式編輯器**。  

5. 在  **BizTalk 運算式編輯器**，新增下列：  

   ```  
   InsertPO = UpdatePOMessageCreator.UpdatePOMessageCreator.XMLMessageCreator();  
   InsertPO(WCF.Action) = "TableOp/Insert/dbo/Purchase_Order";  
   ```  

    在這裡， **InsertPO**是您在中建立的訊息[步驟 2： 建立 BizTalk 協調流程的訊息](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)傳送要求訊息的插入作業**為 Purchase_Order**資料表。 在  **MessageAssignment**圖形，您可以叫用**UpdatePOMessageCreator**類別來建立要求訊息。 此外，您可以設定要求訊息的 WCF 動作。  

6. 內**建構的訊息**圖形和 after**訊息指派**圖形中新增**轉換**圖形。  

7. 在 **轉換組態**對話方塊中，從左窗格中，在**轉換**標籤，按一下 **來源**。  

8. 從**來源轉換**右邊的方塊中，按一下下的空間**變數名稱**，然後選取**UpdateEmployeeResponse**。  

    ![選擇對應的來源結構描述](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-source-map.gif "sql_adap_tut_05_source_map")  

9. 在 **轉換組態**對話方塊中，從左窗格中，在**轉換**標籤，按一下 **目的地**。  

10. 從**目的轉換**右邊的方塊中，按一下下的空間**變數名稱**，然後選取**InsertPO**。  

     ![選擇對應的目的地結構描述](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-dest-map.gif "sql_adap_tut_05_dest_map")  

11. 按一下 [確定] 。 對應檔案隨即開啟。  

12. 展開來源和目的地結構描述中的節點。  

13. 對應 Employee_ID 並命名為這兩個結構描述中的欄位。  

    - 地圖**Employee_ID**來源結構描述中的節點 (UPDATE_EMPLOYEEResponse) **Employee_ID**節點與目的結構描述 (Insert)。  

    - 地圖**名稱**來源結構描述中的節點**Employee_Name**目的結構描述中。  

      下圖顯示對應的結構描述。  

      ![對應來源和目的地結構描述](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-07-dest-map.gif "sql_adap_tut_07_dest_map")  

      儲存並關閉對應。  

14. 下圖顯示進行中協調流程。  

     ![使用 [轉換] 圖形的協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-08-map-orch.gif "sql_adap_tut_08_map_orch")  

## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已建立要插入至記錄訊息**為 Purchase_Order**資料表，並接著對應的回應訊息**UPDATE_EMPLOYEE**預存程序的要求訊息，插入作業。  

## <a name="next-steps"></a>後續步驟  
 傳送要求訊息上執行插入作業**為 Purchase_Order**資料表，並接收回應，如中所述[步驟 3： 傳送要求訊息插入記錄並接收回應](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)。  

## <a name="see-also"></a>另請參閱  
 [步驟 1： 為 Purchase_Order 資料表上的 [插入] 作業建立要求訊息](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)   
 [第 4 課：在訂單資料表上執行插入作業](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)