---
title: 步驟 1： 設定批次批次中外的合作對象資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a93d774b-1282-40d9-836f-44abeb65f78e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eafe692cf86ccf3c6fbe0713c1e621a99a601d5d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974919"
---
# <a name="step-1-configure-party-information-for-batch-inbatch-out"></a>步驟 1： 設定合作對象資訊中的批次/批次出
在此步驟中，您關閉批次處理的合作對象，讓批次的片段中 / 批次出案例。 然後重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]以便讓設定變更才會生效。  
  
### <a name="to-turn-off-fragmentation-of-batching-for-the-party"></a>若要關閉批次處理的合作對象的片段  
  
1. 按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下**BTAHL7 設定總管**。  
  
2. BTAHL7 設定總管 中，在**合作對象**索引標籤的左窗格中，按一下**Tutorial_BatchSource**。  
  
3. 按一下 [**批次定義**] 索引標籤。  
  
4. 選取**否**for**片段所需**，然後按一下**儲存**。  
  
5. 請確定在**可復原交換支援所需**下拉式清單中**False**已選取。  
  
   請繼續進行[步驟 2： 修改或建立傳送和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)。