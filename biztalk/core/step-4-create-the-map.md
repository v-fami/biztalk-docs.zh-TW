---
title: 步驟 4： 建立對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f7f1f6d-0e57-4a65-b91d-c81fcc832961
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fcbce54a488cb687ad0fb2c7a1931243c8cd882
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973980"
---
# <a name="step-4-create-the-map"></a>步驟 4：建立對應
![步驟 4，5 個](../core/media/step-4of5.gif "Step_4of5")  
  
 **若要完成的時間：** 6 分鐘  
  
 **目標：** 在此步驟中，您會建立要求拒絕訊息的要求訊息轉換的對應。  
  
 **用途：** 此對應會確定要求識別碼編號與總計包含在傳回給倉儲庫存系統的要求拒絕訊息。 您將使用 [BizTalk 對應工具] 將內送訊息中的欄位連結至為外寄訊息定義的欄位。 由於這兩個訊息沒有相同的結構，因此這是必要的。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前必須先完成[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)和[步驟 3： 建立要求拒絕結構描述](../core/step-3-create-the-request-decline-schema.md)。  
  
## <a name="procedures"></a>程序  
 此對應會仰賴要求結構描述與要求拒絕結構描述。  您必須先使用結構描述來編譯專案，然後才能在對應上使用它們。  
  
#### <a name="to-compile-the-eaischemas-project"></a>若要編譯 EAISchemas 專案  
  
-   在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**，然後按一下 **建置**。  
  
#### <a name="to-create-the-map"></a>若要建立對應  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**專案，指向**新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目-EAISchemas**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**已安裝的範本**|按一下**對應檔**，然後按一下 **對應**。|  
    |**名稱**|型別**MapToReqDecline.btm**。|  
  
3.  按一下 **[加入]**。  
  
     下圖顯示 [來源結構描述]、[目的結構描述] 和 [對應工具格線]。  
  
     ![MapToReqDenied 對應](../core/media/tut1-maptoreqden1.jpg "Tut1_MapToReqDen1")  
  
4.  在**來源結構描述**] 窗格中，按一下 [**開啟來源結構描述**。  
  
5.  在**BizTalk 型別選擇器**對話方塊方塊中，展開  **EAISchemas**，依序展開**結構描述**，按一下  **eaischemas.request**，然後按一下  **確定**。  
  
6.  在**來源結構描述**] 窗格中，以滑鼠右鍵按一下**\<結構描述\>**，然後按一下 [**展開樹狀結構節點**。  
  
7.  在**目的結構描述**] 窗格中，按一下 [**開啟目的結構描述**。  
  
8.  在**BizTalk 型別選擇器**對話方塊方塊中，展開  **EAISchemas**，展開**結構描述**，按一下**EAISchemas.RequestDecline**，然後按一下按一下**確定**。  
  
9. 在**目的結構描述**] 窗格中，以滑鼠右鍵按一下**\<結構描述\>**，然後按一下 [**展開樹狀結構節點**。  
  
10. 在**來源結構描述**窗格拖曳**ReqID**欄位設為**ReqID**中**目的結構描述**窗格。 會顯示連接兩個項目的直線。  
  
11. 在**來源結構描述**窗格拖曳**GrandTotal**欄位設為**GrandTotal**欄位**目的結構描述** 窗格來對應資料從另一個結構描述。  
  
12. 在**檔案**功能表上，按一下 **全部儲存**，儲存工作。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已建立將要求訊息轉換成要求拒絕訊息的對應。  
  
## <a name="next-steps"></a>後續步驟  
 您會建置 EAISchemas 專案。  
  
## <a name="see-also"></a>請參閱  
 [步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)   
 [步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)   
 [步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md)   
 [步驟 4： 建立地圖](../core/step-4-create-the-map.md)   
 [步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)