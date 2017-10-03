---
title: "排程批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, scheduling
- scheduling batching
ms.assetid: 037626f1-1b3b-43e6-80eb-5fb900cdbd46
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08337171897a4a78e605054e9126e8c8238d5fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scheduling-batching"></a>排程批次
您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]Configuration 總管來啟動、 要求或終止輸出批次。 啟用輸出批次包含兩個步驟： 設定以時間為基礎或訊息計數準則，然後啟動輸出批次處理協調流程。  
  
 下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**批次排程** 索引標籤。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchsch.gif "hl7_ops_batchsch")  
  
 使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管和排程批次處理。  
  
### <a name="to-open-btahl7-configuration-explorer"></a>若要開啟 BTAHL7 組態總管  
  
-   按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本 > Accelerator for HL7**，然後按一下  **BTAHL7組態總管**。  
  
### <a name="to-schedule-message-batching"></a>若要排程訊息批次處理  
  
1.  開啟 BTAHL7 組態檔案總管。  
  
2.  BTAHL7 組態總管 中，在中**BTAHL7 Configuration 總管**對話方塊**合作對象**索引標籤上，選取您想要設定的合作對象，然後在**批次排程**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**第一次批次之前的小時**|輸入第一個批次之前啟動的時數。|  
    |**重複之後的批次**|選取下列其中一項：<br /><br /> -   **小時**。 輸入重複執行批次程序的時數。<br />-   **訊息**。 型別要處理下一個批次程序之前的訊息數目開始。|  
    |**批次控制項**|選取下列其中一項：<br /><br /> -   **啟動排程**： 選取批次排程的開始。<br />-   **立即傳送**： 選取来啟動批次立即處理。<br />-   **停止排程**： 選取即可停止目前的批次排程。|  
  
## <a name="see-also"></a>另請參閱  
 [設定批次處理通知](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)