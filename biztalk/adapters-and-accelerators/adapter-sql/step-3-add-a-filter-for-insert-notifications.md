---
title: "步驟 3： 將篩選加入 Insert 通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a1e9ef-a179-42a7-b4ae-b1170181053b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97fc32fe7dd657bb45edca91fda0eddaa537b32a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-a-filter-for-insert-notifications"></a>步驟 3： 將篩選加入 Insert 通知
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：**此步驟中，在您加入至篩選的插入作業的通知訊息的協調流程 「 決定 」 圖形。 協調流程中的後續作業會執行才收到通知的插入類型。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)。  
  
### <a name="to-filter-for-notification-messages"></a>若要篩選的通知訊息  
  
1.  新增**決定**圖形至協調流程之後,**運算式**圖形。 從 [工具箱] 拖曳**決定**圖形正下方的連接線到**運算式**圖形。  
  
     **決定**圖形展開會顯示分支**如果**陳述式**([rule_1])**和分支**Else**陳述式。  
  
2.  設計介面上，以滑鼠右鍵按一下**決定**圖形，，然後按一下**屬性 視窗**。  
  
3.  在**屬性**窗格**決定**圖形，在**名稱**屬性中，輸入`CheckNotification`。  
  
4.  設計介面上，以滑鼠右鍵按一下**Rule_1**圖形 (內**決定**圖形)，然後按一下**屬性 視窗**。  
  
5.  在**屬性**窗格**Rule_1**，請在**名稱**屬性中，輸入**插入**。  
  
6.  以滑鼠右鍵按一下**插入**圖形，，然後按一下**編輯布林值運算式**。  
  
7.  在 BizTalk 運算式編輯器 」 中，輸入下列命令：  
  
    ```  
    NotificationType.Equals("Insert")  
    ```  
  
     這種狀況會告訴執行後續的作業，只有當協調流程中的值**notificationtype 而**變數是**插入**。  
  
    > [!NOTE]
    >  加入這個變數中的[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)擷取 SQL Server 資料庫從收到的通知訊息的通知類型。  
  
8.  下圖顯示進行中協調流程**決定**包含圖形。  
  
     ![新增 「 決定 」 圖形至協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-03-add-filter-orch.gif "sql_adap_tut_03_add_filter_orch")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已新增**決定**圖形以篩選來通知收到是用於插入作業時，才執行後續作業的通知訊息。  
  
## <a name="next-steps"></a>後續步驟  
 在下一個步驟中，您將協調流程圖形來叫用 UPDATE_EMPLOYE 在員工資料表、 預存程序中所述[第 3 課： 執行預存程序來選取新加入的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)   
 [第 2 課： 接收和篩選器通知](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)