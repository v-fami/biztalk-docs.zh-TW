---
title: "步驟 3： 新增至協調流程連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 245df16e-d327-4c79-be85-004134d5ea6f
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13af336b2162e0f784195bf7c789c0dff984cb04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-ports-to-the-orchestration"></a>步驟 3：將連接埠加入協調流程
![步驟 4 之 3](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：**在此步驟中，新增三個連接埠到 EAIProcess 協調流程，並設定它們。  
  
 **用途：**連接埠指定您的協調流程的傳送訊息及接收來自其他商務程序的訊息。 每個連接埠都具有類型、方向和繫結，由這些決定通訊的方向、通訊的模式、傳送和接受訊息的位置，以及通訊進行的方式。 您在此步驟中建立和設定的 3 個連接埠會執行下列角色：  
  
-   **ReceiveRequestPort**接收倉儲的庫存補充要求訊息。  
  
-   **SendToERP**要求將訊息轉寄至 ERP 系統。  
  
-   **SendDeclinePort**傳送要求拒絕訊息傳回至倉儲。  
  
 如需詳細資訊，請參閱[協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前必須先完成[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-and-configure-receiverequestport"></a>建立和設定 ReceiveRequestPort  
  
1.  在 [方案總管] 中，按兩下**EAIProcess.odx**。  
  
2.  在協調流程設計師中，從協調流程工具箱拖曳**連接埠**圖形到左側的**連接埠介面**、 平行**ReceiveRequest**圖形。 [連接埠組態精靈] 隨即自動啟動。  
  
3.  在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
4.  在**連接埠內容**頁面上，執行下列工作，，然後按一下**下一步**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**ReceiveRequestPort**。|  
  
5.  在**選取連接埠類型**頁面上，執行下列工作，，然後按一下**下一步**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**選取要用於此連接埠的連接埠類型**|選取**建立新的連接埠類型**選項。|  
    |**連接埠類型名稱：**|型別**ReceiveRequestPortType**。|  
    |**通訊模式**|選取**單向**。|  
    |**存取限制**|選取**內部-限制於此專案**。|  
  
6.  在**連接埠繫結**頁面上，執行下列工作，，然後按一下**下一步**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連接埠通訊方向**|選取**我將一律接收訊息，在此連接埠**。|  
    |**連接埠繫結**|從選取**稍後指定**。|  
  
7.  在**完成連接埠精靈**頁面上，按一下**完成**。  
  
#### <a name="to-create-and-configure-senddeclineport"></a>若要建立和設定 SendDeclinePort  
  
1.  從協調流程 [工具箱] 中，拖曳**連接埠**圖形到左側的**連接埠介面**、 平行**SendRequestDecline**圖形。  
  
2.  使用下表中的資訊，來建立**SendDeclinePort**傳送埠。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|型別**SendDeclinePort**。|  
    |**選取要用於此連接埠的連接埠類型**|選取**建立新的連接埠類型**。|  
    |**連接埠類型名稱**|型別**SendDeclinePortType**。|  
    |**通訊模式**|選取**單向**。|  
    |**存取限制**|選取**內部-限制於此專案**。|  
    |**連接埠通訊方向**|從下拉式清單選取**我將總是傳送訊息在此連接埠**。|  
    |**連接埠繫結**|從下拉式清單選取**稍後指定**。|  
  
#### <a name="to-create-and-configure-sendtoerpport"></a>若要建立和設定 SendToERPPort  
  
1.  從協調流程 [工具箱] 中，拖曳**連接埠**圖形到右側**連接埠介面**、 平行**SendToERP**圖形。  
  
2.  使用下表中的資訊，來完成連接埠組態精靈**SendToERP**傳送埠。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|型別**SendToERPPort**。|  
    |**選取要用於此連接埠的連接埠類型**|選取**建立新的連接埠類型**。|  
    |**連接埠類型名稱**|型別**SendToERPPortType**。|  
    |**通訊模式**|選取**單向**選項。|  
    |**存取限制**|選取**內部-限制於此專案**選項。|  
    |**連接埠通訊方向**|從下拉式清單選取**我將總是傳送訊息在此連接埠**。|  
    |**連接埠繫結**|從下拉式清單選取**稍後指定**。|  
  
#### <a name="to-connect-the-ports-to-the-action-shapes"></a>將連接埠連接到動作圖形  
  
-   在協調流程設計師的設計介面中，將每個連接埠的綠色箭頭圖形控點拖曳至動作圖形的對應綠色控點：  
  
    |連接此連接埠|至此動作圖形|  
    |-----------------------|--------------------------|  
    |**ReceiveReqPort**|**Receive_Request**|  
    |**SendDeclinePort**|**Send_ReqDenied**|  
    |**SendToERP**|**Send_ReqToERP**|  
  
     下圖顯示 EAIProcess 協調流程與所有連接的連接埠。  
  
     ![具有連接的連接埠的 EAIProcess 協調流程。] (../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您新增了三個連接埠到 EAIProcess 協調流程，並且加以設定。  
  
## <a name="next-steps"></a>後續步驟  
 您建置專案[步驟 4： 建置 EAIOrchestration 專案](../core/step-4-build-the-eaiorchestration-project.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md)   
 [步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)   
 [步驟 4： 建置 EAIOrchestration 專案](../core/step-4-build-the-eaiorchestration-project.md)