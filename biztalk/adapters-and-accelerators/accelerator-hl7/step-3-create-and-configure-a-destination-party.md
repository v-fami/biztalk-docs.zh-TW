---
title: "步驟 3： 建立及設定目的合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8746f115-9f69-4593-9943-9ccda45cd900
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d955aeaabe4d7207a07827de04c1c21e4c2c7a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-create-and-configure-a-destination-party"></a>步驟 3： 建立及設定目的合作對象
在此步驟中，您可以建立並設定建立批次案例的目的合作對象。 您也可以選取訊息的[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]批次和批次排程時，針對該合作對象所定義。 您會排程批次傳送時間為一小時之後將檔案複製到資料夾。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]批次的頻率為一小時之後收到任何訊息。  
  
### <a name="to-create-and-configure-a-destination-party"></a>建立和設定目的地合作對象  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。  
  
2.  在 合作對象屬性 對話方塊中**名稱**方塊中，輸入**Tutorial_BatchDest**，然後按一下 **確定**。  
  
3.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
4.  BTAHL7 組態總管] 中，在上**合作對象**在主控台樹狀目錄索引標籤上，按一下 [ **Tutorial_BatchDest**。  
  
5.  按一下**通知**詳細資料窗格中的索引標籤。 確認**的通知類型**是**無**。  
  
6.  按一下**批次定義** 索引標籤。在**可用訊息**窗格中，選取**BTAHL7Schemas.ADT_A03_231_GLO_DEF**。 按一下 移動 向右箭號 (**>>**) 新增到此結構描述**選取訊息**，然後按一下 **儲存**。  
  
7.  按一下**批次排程** 索引標籤。在**重複批次之後**區段中，確認**小時**已選取，然後輸入**1**中**小時**方塊。 在**第一個批次之前的小時**方塊中，輸入**1**，然後按一下 **啟動排程**。  
  
 若要繼續[步驟 4： 設定建立批次案例的來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md)。