---
title: "步驟 4： 設定建立批次案例的來源合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b06b6545-4c2e-4a56-9feb-bd3f9574d4d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12f7ca9eebb28bb97ae925aec4fc34cefd5a2dcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-the-source-party-for-the-create-batch-scenario"></a>步驟 4： 設定建立批次案例的來源合作對象
在此步驟中，您可以設定建立批次案例的來源合作對象。 您也選取通知，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 將批次，針對此合作對象所定義。 您可以設定通知批次的排程，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會建立批次之後的訊息計數達到 2。  
  
> [!NOTE]
>  在此案例中，您可以使用的相同來源合作對象，您在建立[步驟 7： 建立和設定來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)（分散輸入批次的案例） 本教學課程的第 1 部分。  
  
### <a name="to-configure-the-source-party-for-the-create-batch-scenario"></a>若要設定的來源合作對象建立批次案例  
  
1.  BTAHL7 組態總管] 中，在上**合作對象**在主控台樹狀目錄索引標籤上，按一下 [ **Tutorial_BatchSource**。  
  
2.  按一下**通知**詳細資料窗格中的索引標籤。 確認**的通知類型**是**OriginalMode**。  
  
3.  按一下**批次定義**] 索引標籤。下**可用訊息 Ack**，按一下**BTAHL7Schemas.ADT_A03_231_GLO_DEF**，按一下 [移動] 向右箭號 (**>>**) 將此結構描述新增至**選取訊息 Ack**，然後按一下 [**儲存**。  
  
4.  按一下**批次排程** 索引標籤。在**重複批次之後**區段中，選取**訊息**，然後輸入**2**中**訊息**方塊。  
  
5.  按一下**啟動排程**。  
  
 若要繼續[步驟 5： 建立傳送埠的訊息批次](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md)。