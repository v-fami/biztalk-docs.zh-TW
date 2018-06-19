---
title: 步驟 2： 擷取通知訊息的通知類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72f3e805-0f5f-42fa-8fe3-78ccbb375f74
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a4fd5e96c3593d3f47ed3c7dfc1875efca7c52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224158"
---
# <a name="step-2-extract-notification-type-from-notification-message"></a>步驟 2： 擷取通知訊息的通知類型
![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您可以新增 「 運算式 」 圖形，以擷取從 SQL Server 資料庫接收的通知類型。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 1： 新增至接收通知的協調流程圖形](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)。  
  
### <a name="to-extract-the-notification-type-from-the-notification-message"></a>擷取通知訊息的通知類型  
  
1.  將變數加入至您在建立 BizTalk 協調流程[步驟 1： 新增至接收通知的協調流程圖形](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)。  
  
    1.  從協調流程] 檢視中，以滑鼠右鍵按一下**變數**，然後按一下 [**新變數**。  
  
    2.  以滑鼠右鍵按一下新的變數， **Variable_1**，然後按一下**屬性 視窗**。 設定變數的下列屬性。  
  
        |將此屬性設定|此值|  
        |-----------------------|-------------------|  
        |**識別碼**|Notificationtype 而|  
        |**型別**|System.String|  
  
2.  新增**運算式**BizTalk 協調流程的圖形。 從協調流程 [工具箱] 中，拖曳**運算式**圖形至協調流程設計介面，和卸除它後**接收**圖形  
  
     內**運算式**圖形，將 xpath 查詢來擷取從 SQL Server 所接收的通知訊息類型。 在之前建立 xpath 查詢，讓我們看看通知訊息的格式。 典型的通知訊息如下所示：  
  
    ```  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
3.  您看到的通知類型的相關資訊可內`<info>`標記，在父系`<Notification>`標記。 因此，加入下列 xpath 查詢內**運算式**圖形：  
  
    ```  
    NotificationType = xpath(NotifyReceive,"string(/*[local-name()='Notification']/*[local-name()='Info']/text())");  
    ```  
  
     在這裡， **notificationtype 而**是您建立來儲存值的 xpath 查詢所擷取的變數。 **NotifyReceive**是您在建立的訊息[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)來接收通知訊息。  
  
4.  下圖顯示進行中協調流程**運算式**包含圖形。  
  
     ![新增 「 運算式 」 圖形至協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-02-add-expression-orch.gif "sql_adap_tut_02_add_expression_orch")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已新增**運算式**圖形以解壓縮 SQL Server 資料庫從收到的通知類型。  
  
## <a name="next-steps"></a>後續步驟  
 中所述，新增決定圖形插入通知篩選[步驟 3： 將篩選加入插入通知](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 加入以接收通知的協調流程圖形](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)   
 [步驟 3： 將篩選加入 Insert 通知](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)   
 [第 2 課： 接收和篩選器通知](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)