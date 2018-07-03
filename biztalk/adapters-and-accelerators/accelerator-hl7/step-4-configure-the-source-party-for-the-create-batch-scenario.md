---
title: 步驟 4： 設定來源合作對象建立批次案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b06b6545-4c2e-4a56-9feb-bd3f9574d4d1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbb4e172c88c179ea53f1e48d1e08dcb63458607
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999823"
---
# <a name="step-4-configure-the-source-party-for-the-create-batch-scenario"></a>步驟 4： 設定來源合作對象建立批次案例
在此步驟中，您可以設定建立批次案例的來源合作對象。 您也選取通知，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會批次處理，此合作對象定義。 您可以設定通知批次的排程，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]之後的訊息計數達到 2 會建立批次。  
  
> [!NOTE]
>  在此案例中，您會使用相同來源合作對象中建立[步驟 7： 建立和設定來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)的本教學課程 （分散的輸入批次的案例） 的第 1 部分。  
  
### <a name="to-configure-the-source-party-for-the-create-batch-scenario"></a>若要設定的來源合作對象建立批次案例  
  
1. BTAHL7 設定總管 中，在**合作對象**索引標籤上的主控台樹狀目錄中，按一下**Tutorial_BatchSource**。  
  
2. 按一下 **通知**詳細資料窗格中的索引標籤。 確認**的通知類型**是**OriginalMode**。  
  
3. 按一下 [**批次定義**] 索引標籤。底下**可用訊息的 Ack**，按一下**BTAHL7Schemas.ADT_A03_231_GLO_DEF**，按一下 [移動] 向右箭號 (**>>**) 將此結構描述新增至**選取訊息的 Ack**，然後按一下**儲存**。  
  
4. 按一下 [**批次排程**] 索引標籤。在 [**重複批次之後**區段中，選取**訊息**，然後輸入**2**中**訊息**] 方塊中。  
  
5. 按一下 **啟動排程**。  
  
   請繼續進行[步驟 5： 建立訊息批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md)。