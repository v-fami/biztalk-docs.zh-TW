---
title: "步驟 1： 設定批次的批次中超出的合作對象資訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a93d774b-1282-40d9-836f-44abeb65f78e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 982b17fe3826a0e5c5ee2a42030ba020b755ab70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-party-information-for-batch-inbatch-out"></a>步驟 1： 設定批次中的合作對象資訊/出批次
在此步驟中，您關閉片段的合作對象啟用批次的批次中 / 出案例批次。 然後重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]來啟用組態變更才會生效。  
  
### <a name="to-turn-off-fragmentation-of-batching-for-the-party"></a>若要關閉的合作對象的批次片段  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk\<版本 > Accelerator for HL7**，然後按一下  **BTAHL7組態總管**。  
  
2.  BTAHL7 組態總管 中，在上**合作對象**索引標籤的左窗格中，按一下**Tutorial_BatchSource**。  
  
3.  按一下**批次定義** 索引標籤。  
  
4.  選取**否**如**片段所需**，然後按一下 **儲存**。  
  
5.  請確定在**可復原交換支援所需**下拉式清單**False**已選取。  
  
 若要繼續[步驟 2： 修改或建立傳送和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)。