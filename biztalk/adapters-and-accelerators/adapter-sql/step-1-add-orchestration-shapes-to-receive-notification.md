---
title: 步驟 1： 加入以接收通知的協調流程圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e4c6fa5-81b7-4928-84d5-39533535f862
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a33693a09d89acc5d1ad9e4514c7907b789cc75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223126"
---
# <a name="step-1-add-orchestration-shapes-to-receive-notification"></a>步驟 1： 加入以接收通知的協調流程圖形
![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您將收到變更通知的協調流程圖形**員工**資料表。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成中的步驟[第 1 課： 產生的結構描述和建立訊息](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)。  
  
### <a name="to-receive-notification-messages"></a>若要接收通知訊息  
  
1.  開啟 BizTalk 協調流程**EmployeeOrch.odx**，您在加入[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)。  
  
2.  新增**接收**圖形至協調流程。 從協調流程 [工具箱] 中，拖曳**接收**圖形至協調流程設計介面，並將它放置到指示之間的空間**開始**（綠色圓形） 和**結束**（紅色八角形） 圖形。  
  
    |將此屬性設定|此值|  
    |-----------------------|-------------------|  
    |**Activate**|True|  
    |**訊息**|NotifyReceive|  
    |**名稱**|ReceiveNotification|  
  
3.  新增單向接收埠到協調流程。 您將使用此連接埠來接收通知訊息從 SQL Server 資料庫。 設定下列屬性的連接埠。  
  
    |將此屬性設定|此值|  
    |-----------------------|-------------------|  
    |**通訊方向**|Receive|  
    |**通訊模式**|單向|  
    |**識別碼**|ReceiveNotification|  
  
     此外，從 Operation_1，若要變更的作業名稱**通知**。  
  
4.  連接**ReceiveNotification**埠連接到**ReceiveNotification**動作圖形。 在 協調流程設計工具的設計介面上，拖曳動作圖形的連接埠對應綠色控點的綠色箭頭圖形控。  
  
    > [!NOTE]
    >  在此步驟中，您使用拖放方法將連接埠連接到動作圖形。 代替使用動作圖形的作業屬性將動作圖形連接到連接埠。  
  
5.  下圖顯示進行中協調流程。  
  
     ![若要接收通知訊息的協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-01-receive-notification-orch.gif "sql_adap_tut_01_receive_notification_orch")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您可以加入協調流程圖形，並接收埠以接收通知，從 SQL Server 資料庫。  
  
## <a name="next-steps"></a>後續步驟  
 您新增 「 運算式 」 圖形至協調流程以擷取從 SQL Server 資料庫中，接收通知的類型中所述[步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 擷取通知訊息的通知類型](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)   
 [第 2 課： 接收和篩選器通知](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)