---
title: 步驟 7： 建立及設定來源合作對象 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8788a9c-ae6f-461b-82e5-f4276d1d5e0c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba84bd9a0ab8c6f7d5ccd24b27e90ef9c441b93
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960748"
---
# <a name="step-7-create-and-configure-a-source-party"></a>步驟 7： 建立及設定來源合作對象
在此步驟中，您可以建立與設定的來源合作對象，以及指定傳送埠，以啟用外寄訊息的訊息標頭轉換。  
  
### <a name="to-create-and-configure-a-source-party"></a>建立和設定來源合作對象  
  
1.  在 BizTalk 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。  
  
2.  在**合作對象屬性**對話方塊中的，在 [名稱] 欄位中，型別**Tutorial_BatchSource**。  
  
    > [!NOTE]
    >  您在此方塊中輸入的值是從原始的 FHS3.1[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]批次的訊息，FragmentedInboundBatch.txt。  
  
3.  在主控台樹狀目錄中，按一下**傳送埠**。  
  
4.  在 [傳送埠] 窗格的 [名稱] 欄位中，選取**Tutorial_2wayAck**。  
  
5.  按一下 **[確定]**。  
  
6.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
7.  BTAHL7 組態總管] 中，在上**合作對象**索引標籤上，按一下 [ **Tutorial_BatchSource**。  
  
8.  選取**批次定義**BTAHL7 Configuration 總管索引標籤。 選取**是**如**片段所需**，然後按一下 **儲存**。  
  
9. 選取**通知**] 索引標籤。如**的通知類型**，選取**OriginalMode**，然後按一下 [**儲存**。  
  
 若要繼續[步驟 8： 重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md)。