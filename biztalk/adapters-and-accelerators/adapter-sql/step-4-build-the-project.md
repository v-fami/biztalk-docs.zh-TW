---
title: "步驟 4： 建置專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d88b1407-ecdd-4dbf-90da-02dc4781568c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f1d6fa03b4a686537ef04f0121c1ae168e525ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-build-the-project"></a>步驟 4： 建置專案
![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：**在此步驟中，您編譯 BizTalk 協調流程專案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[步驟 3： 將要求訊息傳送至插入記錄，並接收回應](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)。  
  
### <a name="to-build-the-biztalk-orchestration-project"></a>若要建置 BizTalk 協調流程專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，然後**屬性**。  
  
2.  在 [屬性頁] 對話方塊中，在樹狀目錄窗格中，展開**通用屬性**，按一下 **組件**，然後在 [屬性] 清單中，按一下 **組件金鑰檔案**省略符號**[…]**.  
  
3.  指定的路徑中所述，您建立的組件金鑰檔案[來建立使用 SQL 配接器的 SQL 應用程式的必要條件](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md)，然後按一下**開啟**。  
  
4.  在 屬性頁 對話方塊中，在樹狀目錄窗格中，展開**組態屬性**，按一下 **部署**，然後執行下列步驟：  
  
    1.  如**應用程式名稱**屬性中，輸入`SampleApplication`。  
  
    2.  如**重新部署**屬性選取**True**。  
  
     按一下 **[確定]**。  
  
5.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
6.  在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**建置方案**。  
  
     應該會在畫面底部的 [輸出] 窗格：**建置： 3 的成功或最新狀態、 0 失敗、 0 略過。**  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您可以編譯包含 BizTalk 專案和兩個類別庫專案的方案。  
  
## <a name="next-steps"></a>後續步驟  
 中所述，部署方案時，[第 5 課： 部署方案](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 傳送要插入的記錄，並接收回應的要求訊息](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)   
 [第 4 課： 執行插入作業的採購訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)