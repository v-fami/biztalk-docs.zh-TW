---
title: 通知錯誤狀況 |Microsoft Docs
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
ms.openlocfilehash: 26bc0524e76521fcb673c6d5d3dc70f43cb12798
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970255"
---
# <a name="acknowledgment-error-conditions"></a>通知錯誤狀況
在下列情況會導致嚴重的錯誤條件時 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會處理通知 (ACK) 訊息：  
  
- MSH9 中缺少必要的欄位  
  
- MSH12 中缺少必要的欄位  
  
  下列情況會產生非嚴重錯誤條件。 在此情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生通知，但也會暫止的通知：  
  
- 遺漏 MSH11 的必要的欄位  
  
- 遺漏 MSH10 值  
  
- 標頭中的選擇性欄位的列舉型別錯誤。  
  
> [!NOTE]
>  MSH 15 設定為 AL 或 ER 時，標頭中找到的列舉型別錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生狀態通知認可**MSA_1 = CR**。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [設定傳送埠來接收 ACK](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)