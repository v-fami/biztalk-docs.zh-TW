---
title: 步驟 2： 建立訊息的 BizTalk 協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47a4fb98-6085-4aeb-ab39-2f2c3858d4e0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bad2f052efa561020ba04060a8290137a08f542
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995359"
---
# <a name="step-2-create-messages-for-biztalk-orchestrations"></a>步驟 2： 建立訊息的 BizTalk 協調流程
![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，方法，您可以將協調流程新增至 BizTalk 專案，並建立您在中產生的結構描述的訊息[步驟 1： 作業產生結構描述](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 1： 作業產生結構描述](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)。  
  
### <a name="to-create-messages-in-an-orchestration"></a>若要建立協調流程中的訊息  
  
1. 將 BizTalk 協調流程新增至 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]:  
  
   1.  從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。  
  
   2.  在 [**加入新項目**] 對話方塊中，從**分類**方塊中，按一下**協調流程檔案**。 從**範本**方塊中，按一下**BizTalk 協調流程**。  
  
   3.  輸入 BizTalk 協調流程的名稱，然後按一下**新增**。 本教學課程中，輸入 名稱`EmployeeOrch.odx`。  
  
2. 開啟**協調流程檢視**的 BizTalk 專案中，如果它尚未開啟的視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3. 將訊息加入至協調流程。  
  
   1.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
   2.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
   3.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
       |使用|以進行此動作|  
       |--------------|----------------|  
       |識別碼|輸入 `NotifyReceive`。|  
       |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取**Employee_PurchaseOrder.Notification**Employee_PurchaseOrder 所在的 BizTalk 專案的名稱。 通知是針對產生的結構描述**通知**作業。|  
  
   4.  重複上述步驟來新增四個新的訊息，要求-回應訊息設定叫用 UPDATE_EMPLOYEE 預存程序，並執行為另一個要求-回應訊息**插入**上的作業**為 Purchase_Order**資料表。  
  
       |若要設定識別項|若要設定訊息類型|  
       |-----------------------|-------------------------|  
       |UpdateEmployee|*Employee_PurchaseOrder.TypedProcedure_dbo。UPDATE_EMPLOYEE*，其中 TypedProcedure_dbo。UPDATE_EMPLOYEE 是結構描述為 UPDATE_EMPLOYEE 預存程序。|  
       |UpdateEmployeeResponse|*Employee_PurchaseOrder.TypedProcedure_dbo。UPDATE_EMPLOYEEResponse*|  
       |InsertPO|*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.Insert*TableOperation_dbo_Purchase_Order.Insert 所在的結構描述為 Purchase_Order 資料表上的插入作業。|  
       |InsertPOResponse|*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.InsertResponse*|  
  
   5.  儲存協調流程檔案和 BizTalk 專案。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您會建立訊息來叫用執行的輸入和輸出作業上使用 SQL Server [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="next-steps"></a>後續步驟  
 中所述，新增至插入作業的 SQL Server 和篩選器通知中收到通知的協調流程圖形[第 2 課： 接收和篩選器通知](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)。  
  
## <a name="see-also"></a>另請參閱  
 [第 1 課： 產生結構描述，並建立訊息](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)   
 [步驟 1：產生作業的結構描述](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)