---
title: 通知錯誤情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, errors
- errors, acknowledgements
ms.assetid: 605c7fa0-2365-4cb6-92fb-6df570905ca8
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15b481f4cdb60822841021f7f708a6caea021b8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204582"
---
# <a name="acknowledgment-error-conditions"></a>通知錯誤狀況
在下列情況會導致嚴重的錯誤條件時[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會處理通知 (ACK) 訊息：  
  
-   遺漏 MSH9 中必要的欄位  
  
-   遺漏 MSH12 中必要的欄位  
  
 在下列情況會導致非嚴重錯誤的情況。 在此情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生通知，但也會暫止的通知：  
  
-   遺失必要的欄位中 MSH11  
  
-   遺漏 MSH10 值  
  
-   列舉型別為選擇性欄位標頭中的的錯誤。  
  
> [!NOTE]
>  MSH 15 AL 或增，設定標頭中找到的列舉型別錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生狀態為認可通知**MSA_1 = CR**。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [設定傳送埠來接收通知](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)