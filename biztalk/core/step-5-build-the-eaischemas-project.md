---
title: "步驟 5： 建置 EAISchemas 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c20cd368-7446-4861-8d71-5bc25ce408a2
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394d9df78f7064df8501ed43149bd26793533c47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-build-the-eaischemas-project"></a>步驟 5：建置 EAISchema 專案
![步驟 5 之 5](../core/media/step-5of5.gif "Step_5of5")  
  
 **若要完成的時間：** 6 分鐘  
  
 **目標：**在此步驟中，您會編譯 EAISchemas 專案。  
  
 **用途：** Microsoft BizTalk Server 與.NET Framework 的最重要的部分是所有 BizTalk Server 成品、 對應、 結構描述、 協調流程和管線都會編譯為.NET 組件。 此設計的兩個最重要含意是這些組件必須具有強式名稱，因此它們也遵循 .NET 版本管理規則。 其主要含意為，一旦針對另一個 .NET 專案或組件 (包括 BizTalk 專案) 的特定版本建置 BizTalk 專案，該專案會繼續使用此版本，直到再針對較新的版本重新建置它為止。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前，您必須先完成下列步驟：  
  
    -   [步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)  
  
    -   [步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md) 
  
    -   [步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md)  
  
    -   [步驟 4： 建立地圖](../core/step-4-create-the-map.md)  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-build-the-eaischemas-project"></a>若要建置 EAISchemas 專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**，然後按一下 **建置**。  
  
     畫面底部應會顯示：  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ```  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已經建置 EAISchemas 專案來產生組件檔案 (DLL)。  
  
## <a name="next-steps"></a>後續步驟  
 建立評估庫存補充要求訊息，依據核准準則中的內容的商務程序[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)   
 [步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)   
 [步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md)   
 [步驟 4： 建立地圖](../core/step-4-create-the-map.md)